<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SmartTest – Batching Quiz</title>

<style>
body{
    margin:0;
    padding:20px;
    font-family:Tahoma,Arial,sans-serif;
    background:#0f3c4c;
    color:#fff;
}
.container{
    max-width:900px;
    margin:auto;
    background:#164b5f;
    padding:20px;
    border-radius:12px;
}
h1{text-align:center}
input,select,button{
    width:100%;
    padding:12px;
    margin:10px 0;
    border:none;
    border-radius:8px;
    font-size:16px;
}
button{
    background:#3fa34d;
    color:#fff;
    font-weight:bold;
    cursor:pointer;
}
button:disabled{background:#777}
.status{
    margin-top:10px;
    padding:10px;
    border-radius:8px;
}
.status.error{background:#8b2e2e}
.status.loading{background:#444}
.question{
    background:#1d6079;
    padding:15px;
    border-radius:8px;
    margin-top:15px;
}
.option{
    background:#124050;
    padding:10px;
    margin:6px 0;
    border-radius:6px;
    cursor:pointer;
}
.option:hover{background:#1b6b86}
.option.correct{background:#2e8b57}
.option.wrong{background:#8b2e2e}
.feedback{
    background:#0c2f3b;
    padding:10px;
    margin-top:10px;
    border-radius:6px;
}
</style>
</head>

<body>
<div class="container">
<h1>🚀 SmartTest – اختبار ذكي</h1>

<input id="topic" placeholder="اكتب موضوع الاختبار (مثال: قواعد النحو)">
<select id="language">
    <option value="ar">عربي</option>
    <option value="en">English</option>
</select>
<select id="count">
    <option value="10">10</option>
    <option value="20">20</option>
    <option value="60">60</option>
    <option value="100">100</option>
    <option value="200">200</option>
</select>

<button id="generateBtn">توليد الاختبار</button>

<div id="status"></div>
<div id="output"></div>
</div>

<script>
/* 🔴 endpoint الصحيح بعد التحديث */
const API_URL = "https://batching-project.onrender.com/generate/batch";

const topicInput   = document.getElementById("topic");
const languageSel  = document.getElementById("language");
const countSel     = document.getElementById("count");
const btn          = document.getElementById("generateBtn");
const statusBox    = document.getElementById("status");
const outputBox    = document.getElementById("output");

btn.addEventListener("click", generate);

function setStatus(text,type="loading"){
    statusBox.className="status "+type;
    statusBox.innerText=text;
}

async function generate(){
    outputBox.innerHTML="";
    const topic = topicInput.value.trim();
    if(!topic){
        setStatus("❌ أدخل موضوع الاختبار","error");
        return;
    }

    btn.disabled=true;
    setStatus("⏳ جارٍ توليد الأسئلة باستخدام batching…");

    try{
        const res = await fetch(API_URL,{
            method:"POST",
            headers:{ "Content-Type":"application/json" },
            body:JSON.stringify({
                topic: topic,
                language: languageSel.value,
                total_questions: Number(countSel.value)
            })
        });

        if(!res.ok){
            const t = await res.text();
            throw new Error(t);
        }

        const data = await res.json();

        if(!data.questions || !Array.isArray(data.questions)){
            throw new Error("لم يتم استلام أسئلة صالحة من الخادم");
        }

        renderQuestions(data.questions);
        setStatus(`✅ تم توليد ${data.questions.length} سؤال بنجاح`);
    }catch(err){
        setStatus("❌ فشل في التوليد: "+err.message,"error");
    }finally{
        btn.disabled=false;
    }
}

function renderQuestions(questions){
    outputBox.innerHTML="";
    questions.forEach((q,i)=>{
        const qBox=document.createElement("div");
        qBox.className="question";
        qBox.innerHTML=`<b>${i+1}. ${q.q}</b>`;

        q.options.forEach((opt,idx)=>{
            const o=document.createElement("div");
            o.className="option";
            o.textContent=opt;
            o.onclick=()=>choose(o,idx,q.answer,q.explanations,qBox);
            qBox.appendChild(o);
        });

        const fb=document.createElement("div");
        fb.className="feedback";
        fb.style.display="none";
        qBox.appendChild(fb);

        outputBox.appendChild(qBox);
    });
}

function choose(el,idx,answer,exps,box){
    const fb=box.querySelector(".feedback");
    fb.style.display="block";

    let html="<b>التغذية الراجعة:</b><br>";
    exps.forEach((e,i)=>{
        if(i===answer){
            html+=`<div style="color:#9fffbc"><b>✔ الإجابة الصحيحة:</b> ${e}</div>`;
        }else{
            html+=`<div style="color:#ffd2d2"><b>✖ خيار خاطئ:</b> ${e}</div>`;
        }
    });
    fb.innerHTML=html;

    box.querySelectorAll(".option").forEach((o,i)=>{
        o.onclick=null;
        if(i===answer) o.classList.add("correct");
        else if(i===idx) o.classList.add("wrong");
    });
}
</script>
</body>
</html>