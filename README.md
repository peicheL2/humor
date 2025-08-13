## Hi there 👋

<!--
**peicheL2/peicheL2** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<title>幽默風格簡易測驗</title>
<style>
 body { font-family: Arial, sans-serif; margin: 20px; line-height: 1.6; }
 .question { margin-bottom: 15px; }
 .btn { padding: 10px 15px; background-color: #4CAF50; color: white; border: none; cursor: pointer; }
 .btn:hover { background-color: #45a049; }
 .result { margin-top: 20px; font-weight: bold; }
</style>
</head>
<body>
<h2>幽默風格簡易測驗（8 題版）</h2>
<p>請依照 1（非常不同意）到 5（非常同意）進行評分。</p>
<div id="quiz"></div>
<button class="btn" onclick="calculateScore()">提交並查看結果</button>
<div class="result" id="result"></div>
<script>
const questions = [
 "我常用幽默讓氣氛更輕鬆。",
 "即使情況不順，我也能找到讓自己笑的方法。",
 "我喜歡用玩笑來揶揄或取笑別人。",
 "我常自嘲讓別人笑，即使對我形象不好。",
 "我喜歡用笑話來打開話題，讓人更容易親近。",
 "當我情緒低落時，幽默能幫我恢復心情。",
 "我有時會用諷刺來指出別人的缺點。",
 "我會用取笑自己的方式讓人覺得我好相處。"
];
const quizDiv = document.getElementById('quiz');
questions.forEach((q, i) => {
 let html = `<div class='question'>${i+1}. ${q}<br>`;
 for (let score = 1; score <= 5; score++) {
   html += `<label><input type='radio' name='q${i}' value='${score}'>${score}</label> `;
 }
 html += '</div>';
 quizDiv.innerHTML += html;
});
function calculateScore() {
 let scores = { affiliative: 0, selfEnhancing: 0, aggressive: 0, selfDefeating: 0 };
 let mapping = {
   0: 'affiliative',
   1: 'selfEnhancing',
   2: 'aggressive',
   3: 'selfDefeating',
   4: 'affiliative',
   5: 'selfEnhancing',
   6: 'aggressive',
   7: 'selfDefeating'
 };
 for (let i = 0; i < 8; i++) {
   let val = document.querySelector(`input[name='q${i}']:checked`);
   if (!val) {
     alert('請完成所有題目！');
     return;
   }
   scores[mapping[i]] += parseInt(val.value);
 }
 let resultText = `親和型: ${scores.affiliative}\n自我提升型: ${scores.selfEnhancing}\n攻擊型: ${scores.aggressive}\n自我貶抑型: ${scores.selfDefeating}`;
 document.getElementById('result').innerText = resultText;
}
</script>
</body>
</html>
