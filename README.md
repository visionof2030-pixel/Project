<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<title>Batching Quiz Generator</title>
<style>
body{font-family:Tahom a;background:#0f3c4c;color:#fff;padding:20px}
.container{max-width:800px;margin:auto}
input,select,button{width:100%;padding:10px;margin:6px 0;border-radius:6px}
button{background:#3fa34d;color:#fff;font-weight:bold}
.question{background:#1d6079;padding:15px;margin-top:15px;border-radius:8px}
.option{background:#124050;padding:10px;margin:5px 0;border-radius:6px;cursor:pointer}
.correct{background:#2e8b57}
.wrong{background:#8b2e2e}
.progress{margin-top:10px}
</style>
</head>

<body>
<div class="container">
<h2>🚀 Batching Quiz Generator</h2>

<input id="topic" placeholder="اكتب الموضوع">
<select id="language">
  <option value="ar">عربي</option>
  <option value="en">English</option>
</select>
<select id="count">
  <option>10</option>
  <option>20</option>
  <option>60</option>
  <option>100</option>
  <option>200</option>
</select>

<button onclick="start()">توليد الاختبار</button>
<div class="progress" id="progress"></div>
<div id="output"></div>
</div>

<script>
const API = "https://batching-project.onrender.com/generate/batch";
let allQuestions = [];

async function start(){
  allQuestions = [];
  output.innerHTML="";
  progress.innerHTML="بدأ التوليد...";
  await generateLoop(0);
}

async function generateLoop(offset){
  const total = parseInt(count.value);

  const res = await fetch(API,{
    method:"POST",
    headers:{"Content-Type":"application/json"},
    body:JSON.stringify({
      topic:topic.value,
      language:language.value,
      total_questions: total,
      offset: offset
    })
  });

  const data = await res.json();
  if(!data.questions){
    progress.innerHTML="❌ فشل في التوليد";
    return;
  }

  allQuestions.push(...data.questions);
  progress.innerHTML = `تم توليد ${allQuestions.length} / ${total}`;

  if(!data.done){
    await generateLoop(data.offset);
  } else {
    progress.innerHTML="✅ اكتمل التوليد";
    render(allQuestions);
  }
}

function render(qs){
  let html="";
  qs.forEach((q,i)=>{
    html+=`
    <div class="question">
      <b>${i+1}. ${q.q}</b>
      ${q.options.map((o,idx)=>`
        <div class="option" onclick="choose(this,${idx},${q.answer},${JSON.stringify(q.explanations)})">${o}</div>
      `).join("")}
      <div></div>
    </div>`;
  });
  output.innerHTML=html;
}

function choose(el,idx,answer,exps){
  const box = el.parentElement;
  [...box.querySelectorAll(".option")].forEach((o,i)=>{
    o.onclick=null;
    if(i===answer) o.classList.add("correct");
    else if(i===idx) o.classList.add("wrong");
  });

  let fb = "<hr>";
  exps.forEach((e,i)=>{
    fb += i===answer
      ? `<div style="color:#9fffbc">✔ ${e}</div>`
      : `<div style="color:#ffd2d2">✖ ${e}</div>`;
  });
  box.innerHTML += fb;
}
</script>
</body>
</html>