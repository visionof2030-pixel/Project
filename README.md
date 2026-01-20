<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Batching Quiz Generator</title>

<style>
body{
    margin:0;
    font-family:Tahoma;
    background:#0f3c4c;
    color:#fff;
    padding:20px;
}
.container{
    max-width:900px;
    margin:auto;
    background:#164b5f;
    padding:20px;
    border-radius:14px;
}
h1{
    text-align:center;
    margin-bottom:20px;
}
input,select,button{
    width:100%;
    padding:12px;
    margin:8px 0;
    border-radius:8px;
    border:none;
    font-size:16px;
}
button{
    background:#3fa34d;
    color:#fff;
    font-weight:bold;
    cursor:pointer;
}
button:disabled{
    background:#777;
}
.question{
    background:#1d6079;
    margin-top:15px;
    padding:15px;
    border-radius:10px;
}
.option{
    background:#124050;
    margin:6px 0;
    padding:10px;
    border-radius:6px;
    cursor:pointer;
}
.option:hover{
    background:#1b6b86;
}
.option.correct{
    background:#2e8b57;
}
.option.wrong{
    background:#8b2e2e;
}
.feedback{
    background:#0c2f3b;
    padding:10px;
    margin-top:10px;
    border-radius:6px;
}
.hidden{
    display:none;
}
.loader{
    text-align:center;
    margin-top:15px;
}
</style>
</head>

<body>
<div class="container">
<h1>🚀 Batching Quiz Generator</h1>

<input id="topic" placeholder="اكتب موضوع الاختبار">
<select id="language">
    <option value="ar">عربي</option>
    <option value="en">English</option>
</select>

<select id="count">
    <option value="5">5</option>
    <option value="10" selected>10</option>
    <option value="20">20</option>
    <option value="40">40</option>
    <option value="60">60</option>
    <option value="100">100</option>
    <option value="200">200</option>
</select>

<button id="btn" onclick="generate()">توليد الاختبار</button>
<div id="loader" class="loader hidden">⏳ جاري التوليد...</div>
<div id="output"></div>
</div>

<script>
const API = "https://batching-project.onrender.com/generate";

async function generate(){
    const topic = document.getElementById("topic").value.trim();
    if(!topic){
        alert("اكتب موضوع الاختبار");
        return;
    }

    document.getElementById("btn").disabled = true;
    document.getElementById("loader").classList.remove("hidden");
    document.getElementById("output").innerHTML = "";

    try{
        const res = await fetch(API,{
            method:"POST",
            headers:{
                "Content-Type":"application/json"
            },
            body:JSON.stringify({
                topic: topic,
                language: document.getElementById("language").value,
                total_questions: parseInt(document.getElementById("count").value)
            })
        });

        if(!res.ok){
            throw new Error("Load failed");
        }

        const data = await res.json();
        renderQuiz(data.questions);
    }catch(e){
        alert("حدث خطأ أثناء التوليد");
    }

    document.getElementById("btn").disabled = false;
    document.getElementById("loader").classList.add("hidden");
}

function renderQuiz(questions){
    let html = "";
    questions.forEach((q,i)=>{
        html += `
        <div class="question">
            <b>${i+1}. ${q.q}</b>
            ${q.options.map((op,idx)=>`
                <div class="option" onclick="choose(this,${idx},${q.answer},${encodeURIComponent(JSON.stringify(q.explanations))})">
                    ${op}
                </div>
            `).join("")}
            <div class="feedback hidden"></div>
        </div>
        `;
    });
    document.getElementById("output").innerHTML = html;
}

function choose(el,idx,answer,expsEncoded){
    const box = el.parentElement;
    const fb = box.querySelector(".feedback");
    const explanations = JSON.parse(decodeURIComponent(expsEncoded));

    box.querySelectorAll(".option").forEach((o,i)=>{
        o.onclick = null;
        if(i === answer) o.classList.add("correct");
        else if(i === idx) o.classList.add("wrong");
    });

    let html = "<b>التغذية الراجعة:</b><br>";
    explanations.forEach((e,i)=>{
        if(i === answer){
            html += `<div style="color:#9fffbc;margin-top:6px"><b>✔ الإجابة الصحيحة:</b> ${e}</div>`;
        }else{
            html += `<div style="color:#ffd2d2;margin-top:6px"><b>✖ خيار خاطئ:</b> ${e}</div>`;
        }
    });

    fb.innerHTML = html;
    fb.classList.remove("hidden");
}
</script>
</body>
</html>