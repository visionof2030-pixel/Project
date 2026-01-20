<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Batching Quiz Generator</title>

<style>
body {
    background:#0f3c4c;
    font-family:Tahoma;
    color:#fff;
    margin:0;
    padding:20px;
}
.container {
    max-width:900px;
    margin:auto;
    background:#164b5f;
    padding:20px;
    border-radius:12px;
}
h1 {
    text-align:center;
    margin-bottom:20px;
}
input, select, button {
    width:100%;
    padding:12px;
    margin:8px 0;
    border-radius:6px;
    border:none;
    font-size:16px;
}
button {
    background:#3fa34d;
    color:#fff;
    font-weight:bold;
    cursor:pointer;
}
button:disabled {
    background:#777;
}
.question {
    background:#1d6079;
    padding:15px;
    border-radius:8px;
    margin-top:15px;
}
.option {
    background:#124050;
    padding:10px;
    margin:6px 0;
    border-radius:6px;
    cursor:pointer;
}
.option:hover {background:#1b6b86}
.correct {background:#2e8b57 !important}
.wrong {background:#8b2e2e !important}
.feedback {
    background:#0c2f3b;
    padding:12px;
    margin-top:10px;
    border-radius:6px;
}
.hidden {display:none}
.loader {
    margin-top:15px;
    text-align:center;
}
</style>
</head>

<body>
<div class="container">
<h1>🚀 Batching Quiz Generator</h1>

<input id="topic" placeholder="اكتب موضوع الاختبار هنا">

<select id="language">
    <option value="ar">عربي</option>
    <option value="en">English</option>
</select>

<select id="count">
    <option>5</option>
    <option selected>10</option>
    <option>20</option>
    <option>30</option>
    <option>40</option>
    <option>60</option>
</select>

<button id="btn" onclick="generate()">توليد الاختبار</button>

<div id="loader" class="loader hidden">⏳ جاري التوليد...</div>
<div id="output"></div>
</div>

<script>
const BACKEND = "https://batching-project.onrender.com";

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
        const res = await fetch(`${BACKEND}/generate`,{
            method:"POST",
            headers:{
                "Content-Type":"application/json"
            },
            body:JSON.stringify({
                topic: topic,
                language: document.getElementById("language").value,
                total_questions: Number(document.getElementById("count").value)
            })
        });

        if(!res.ok){
            throw new Error("HTTP " + res.status);
        }

        const data = await res.json();
        renderQuiz(data.questions);

    }catch(e){
        alert("حدث خطأ أثناء التوليد");
        console.error(e);
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
            ${q.options.map((o,idx)=>`
                <div class="option"
                     onclick="choose(this,${idx},${q.answer},${JSON.stringify(q.explanations)})">
                     ${o}
                </div>
            `).join("")}
            <div class="feedback hidden"></div>
        </div>`;
    });
    document.getElementById("output").innerHTML = html;
}

function choose(el,idx,answer,exps){
    const box = el.parentElement;
    const fb = box.querySelector(".feedback");
    fb.classList.remove("hidden");

    let html = "<b>التغذية الراجعة:</b><br>";
    exps.forEach((e,i)=>{
        if(i === answer){
            html += `<div style="color:#9fffbc;margin-top:6px"><b>✔ الصحيح:</b> ${e}</div>`;
        }else{
            html += `<div style="color:#ffd2d2;margin-top:6px"><b>✖ خطأ:</b> ${e}</div>`;
        }
    });
    fb.innerHTML = html;

    [...box.querySelectorAll(".option")].forEach((o,i)=>{
        o.onclick = null;
        if(i === answer) o.classList.add("correct");
        else if(i === idx) o.classList.add("wrong");
    });
}
</script>
</body>
</html>
