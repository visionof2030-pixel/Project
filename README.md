<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>SmartTest – اختبار ذكي مدفوع</title>

<style>
*{box-sizing:border-box}
body{
    margin:0;
    padding:12px;
    font-family:Tahoma,Arial,sans-serif;
    background:#0f3c4c;
    color:#fff;
}
.container{
    width:100%;
    background:#164b5f;
    padding:14px;
    border-radius:12px;
}
h1{
    text-align:center;
    margin:8px 0 12px;
    font-size:20px;
}
input,select,button{
    width:100%;
    padding:14px;
    margin:6px 0;
    border:none;
    border-radius:10px;
    font-size:16px;
}
input,select{
    background:#fff;
    color:#000;
}
button{
    background:#3fa34d;
    color:#fff;
    font-weight:bold;
}
button:disabled{background:#777}
.status{
    margin-top:10px;
    padding:10px;
    border-radius:8px;
    font-size:15px;
}
.status.error{background:#8b2e2e}
.status.loading{background:#444}
.status.success{background:#2e8b57}
.question{
    background:#1d6079;
    padding:14px;
    border-radius:10px;
    margin-top:12px;
}
.option{
    background:#124050;
    padding:12px;
    margin:6px 0;
    border-radius:8px;
}
.option.correct{background:#2e8b57}
.option.wrong{background:#8b2e2e}
.feedback{
    background:#0c2f3b;
    padding:10px;
    margin-top:8px;
    border-radius:8px;
}
</style>
</head>

<body>
<div class="container">
<h1>🧠 SmartTest – اختبار ذكي</h1>

<input id="licenseInput" placeholder="🔑 أدخل مفتاح التفعيل">
<button id="activateBtn">تفعيل المفتاح</button>

<input id="topic" placeholder="📘 موضوع الاختبار" disabled>

<select id="language" disabled>
    <option value="ar">عربي</option>
    <option value="en">English</option>
</select>

<select id="count" disabled>
    <option value="5">5 أسئلة</option>
    <option value="10">10 أسئلة</option>
    <option value="20">20 سؤال</option>
</select>

<button id="generateBtn" disabled>🚀 توليد الاختبار</button>

<div id="status"></div>
<div id="output"></div>
</div>

<script>
const API_URL = "https://batching-project.onrender.com/generate/batch";
let ACTIVE_LICENSE = null;

/* ===== device-id ثابت للجهاز ===== */
let DEVICE_ID = localStorage.getItem("device_id");
if(!DEVICE_ID){
    DEVICE_ID = "dev-" + crypto.randomUUID();
    localStorage.setItem("device_id", DEVICE_ID);
}

const statusBox = document.getElementById("status");
const outputBox = document.getElementById("output");

function setStatus(msg,type="loading"){
    statusBox.className="status "+type;
    statusBox.innerText=msg;
}

/* ===== تفعيل المفتاح ===== */
document.getElementById("activateBtn").onclick = async ()=>{
    const key = licenseInput.value.trim();
    if(!key){
        setStatus("❌ أدخل مفتاح التفعيل","error");
        return;
    }

    setStatus("⏳ جارٍ التحقق من المفتاح…","loading");

    try{
        const res = await fetch(API_URL,{
            method:"POST",
            headers:{
                "Content-Type":"application/json",
                "license-key": key,
                "device-id": DEVICE_ID
            },
            body:JSON.stringify({
                topic:"test",
                language:"ar",
                total_questions:1
            })
        });

        const data = await res.json();
        if(!res.ok) throw new Error(data.detail || "فشل التفعيل");

        ACTIVE_LICENSE = key;
        topic.disabled = language.disabled = count.disabled = generateBtn.disabled = false;
        setStatus("✅ تم تفعيل المفتاح بنجاح","success");
    }catch(e){
        setStatus("❌ "+e.message,"error");
    }
};

/* ===== توليد الاختبار ===== */
document.getElementById("generateBtn").onclick = async ()=>{
    outputBox.innerHTML="";
    if(!ACTIVE_LICENSE){
        setStatus("❌ فعل المفتاح أولاً","error");
        return;
    }

    setStatus("⏳ جارٍ التوليد…","loading");

    try{
        const res = await fetch(API_URL,{
            method:"POST",
            headers:{
                "Content-Type":"application/json",
                "license-key": ACTIVE_LICENSE,
                "device-id": DEVICE_ID
            },
            body:JSON.stringify({
                topic: topic.value,
                language: language.value,
                total_questions: Number(count.value)
            })
        });

        const data = await res.json();
        if(!res.ok) throw new Error(data.detail || "فشل التوليد");

        render(data.questions);
        setStatus("✅ تم التوليد بنجاح","success");
    }catch(e){
        setStatus("❌ "+e.message,"error");
    }
};

function render(qs){
    outputBox.innerHTML="";
    qs.forEach((q,i)=>{
        const d=document.createElement("div");
        d.className="question";
        d.innerHTML=`<b>${i+1}. ${q.q}</b>`;
        q.options.forEach((o,j)=>{
            const op=document.createElement("div");
            op.className="option";
            op.innerText=o;
            op.onclick=()=>{
                d.querySelectorAll(".option").forEach((x,k)=>{
                    if(k===q.answer) x.classList.add("correct");
                    else if(k===j) x.classList.add("wrong");
                });
                const fb=document.createElement("div");
                fb.className="feedback";
                fb.innerHTML=q.explanations.join("<br>");
                d.appendChild(fb);
            };
            d.appendChild(op);
        });
        outputBox.appendChild(d);
    });
}
</script>
</body>
</html>