<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>SmartTest – اختبار ذكي مدفوع</title>

<style>
body{
    margin:0;
    padding:16px;
    font-family:Tahoma,Arial,sans-serif;
    background:#0f3c4c;
    color:#fff;
}
.container{
    max-width:900px;
    margin:auto;
    background:#164b5f;
    padding:16px;
    border-radius:12px;
}
h1{text-align:center;margin-bottom:10px}
input,select,button{
    width:100%;
    padding:14px;
    margin:8px 0;
    border:none;
    border-radius:10px;
    font-size:16px;
}
button{
    background:#3fa34d;
    color:#fff;
    font-weight:bold;
}
button:disabled{
    background:#777;
}
.status{
    margin-top:10px;
    padding:10px;
    border-radius:8px;
    font-size:15px;
}
.status.error{background:#8b2e2e}
.status.loading{background:#444}
.status.success{background:#2e8b57}

.section{
    margin-top:15px;
}

.question{
    background:#1d6079;
    padding:14px;
    border-radius:10px;
    margin-top:12px;
}
.option{
    background:#124050;
    padding:10px;
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

<!-- ====== تفعيل المفتاح ====== -->
<div class="section">
<input id="licenseInput" placeholder="🔑 أدخل مفتاح التفعيل">
<button id="activateBtn">تفعيل المفتاح</button>
</div>

<!-- ====== إعدادات الاختبار ====== -->
<div class="section">
<input id="topic" placeholder="📘 موضوع الاختبار" disabled>

<select id="language" disabled>
    <option value="ar">عربي</option>
    <option value="en">English</option>
</select>

<select id="count" disabled>
    <option value="5">5 أسئلة</option>
    <option value="10">10 أسئلة</option>
    <option value="20">20 سؤال</option>
    <option value="60">60 سؤال</option>
    <option value="100">100 سؤال</option>
    <option value="200">200 سؤال</option>
</select>

<button id="generateBtn" disabled>🚀 توليد الاختبار</button>
</div>

<div id="status"></div>
<div id="output"></div>
</div>

<script>
const API_URL = "https://batching-project.onrender.com/generate/batch";

let ACTIVE_LICENSE = null;

const licenseInput = document.getElementById("licenseInput");
const activateBtn  = document.getElementById("activateBtn");

const topicInput  = document.getElementById("topic");
const languageSel = document.getElementById("language");
const countSel    = document.getElementById("count");
const generateBtn = document.getElementById("generateBtn");

const statusBox = document.getElementById("status");
const outputBox = document.getElementById("output");

function setStatus(text,type="loading"){
    statusBox.className="status "+type;
    statusBox.innerText=text;
}

/* ====== تفعيل المفتاح ====== */
activateBtn.onclick = async ()=>{
    const key = licenseInput.value.trim();
    if(!key){
        setStatus("❌ أدخل مفتاح التفعيل","error");
        return;
    }

    activateBtn.disabled = true;
    setStatus("⏳ جارٍ التحقق من المفتاح…","loading");

    try{
        const res = await fetch(API_URL,{
            method:"POST",
            headers:{
                "Content-Type":"application/json",
                "license-key": key
            },
            body:JSON.stringify({
                topic:"اختبار",
                language:"ar",
                total_questions:1
            })
        });

        if(!res.ok){
            const err = await res.json();
            throw new Error(err.detail || "مفتاح غير صالح");
        }

        ACTIVE_LICENSE = key;

        topicInput.disabled = false;
        languageSel.disabled = false;
        countSel.disabled = false;
        generateBtn.disabled = false;

        setStatus("✅ تم تفعيل المفتاح بنجاح","success");
    }catch(e){
        setStatus("❌ فشل التفعيل: "+e.message,"error");
        activateBtn.disabled = false;
    }
};

/* ====== توليد الاختبار ====== */
generateBtn.onclick = async ()=>{
    outputBox.innerHTML="";

    if(!ACTIVE_LICENSE){
        setStatus("❌ يجب تفعيل المفتاح أولاً","error");
        return;
    }

    const topic = topicInput.value.trim();
    if(!topic){
        setStatus("❌ أدخل موضوع الاختبار","error");
        return;
    }

    generateBtn.disabled = true;
    setStatus("⏳ جارٍ توليد الأسئلة…","loading");

    try{
        const res = await fetch(API_URL,{
            method:"POST",
            headers:{
                "Content-Type":"application/json",
                "license-key": ACTIVE_LICENSE
            },
            body:JSON.stringify({
                topic: topic,
                language: languageSel.value,
                total_questions: Number(countSel.value)
            })
        });

        if(!res.ok){
            const err = await res.json();
            throw new Error(err.detail || "فشل التوليد");
        }

        const data = await res.json();
        renderQuestions(data.questions);

        setStatus(`✅ تم توليد ${data.questions.length} سؤال`,"success");
    }catch(e){
        setStatus("❌ "+e.message,"error");
    }finally{
        generateBtn.disabled = false;
    }
};

function renderQuestions(questions){
    outputBox.innerHTML="";
    questions.forEach((q,i)=>{
        const box=document.createElement("div");
        box.className="question";
        box.innerHTML=`<b>${i+1}. ${q.q}</b>`;

        q.options.forEach((opt,idx)=>{
            const o=document.createElement("div");
            o.className="option";
            o.innerText=opt;
            o.onclick=()=>{
                box.querySelectorAll(".option").forEach((el,j)=>{
                    el.onclick=null;
                    if(j===q.answer) el.classList.add("correct");
                    else if(j===idx) el.classList.add("wrong");
                });

                const fb=document.createElement("div");
                fb.className="feedback";
                fb.innerHTML=q.explanations.join("<br>");
                box.appendChild(fb);
            };
            box.appendChild(o);
        });

        outputBox.appendChild(box);
    });
}
</script>
</body>
</html>