# Wob-u
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Love Forever</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    body {
      background: #000;
      height: 100vh;
      margin: 0;
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: system-ui, -apple-system, "Segoe UI", Roboto, Arial, sans-serif;
    }
    canvas { display: none; }
    #ui {
      position: relative;
      width: 450px;
      height: 450px;
    }
    .love {
      position: absolute;
      top: 50%;
      left: 50%;
      margin-top: -225px;
      margin-left: -225px;
    }
    .love_word {
      color: #ea80b0;
      font-size: 1.4rem;
      transform: translateY(-100%) rotateZ(-30deg);
      text-shadow: 0 0 10px #fff;
      letter-spacing: 2px;
      white-space: nowrap;
      display: inline-block;
      min-width: 8ch;
      max-width: 12ch;
      overflow: hidden;
      text-overflow: clip;
      text-align: center;
    }
    .love_horizontal {
      animation: horizontal 10000ms infinite alternate ease-in-out;
      animation-delay: var(--d);
    }
    .love_vertical {
      animation: vertical 20000ms infinite linear;
      animation-delay: var(--d);
    }
    @keyframes horizontal {
      from { transform: translateX(0px); }
      to   { transform: translateX(450px); }
    }
    @keyframes vertical {
      0%    { transform: translateY(180px); }
      10%   { transform: translateY(45px); }
      15%   { transform: translateY(4.5px); }
      18%   { transform: translateY(0px); }
      20%   { transform: translateY(4.5px); }
      22%   { transform: translateY(34.6px); }
      24%   { transform: translateY(64.3px); }
      25%   { transform: translateY(112.5px); }
      26%   { transform: translateY(64.3px); }
      28%   { transform: translateY(34.6px); }
      30%   { transform: translateY(4.5px); }
      32%   { transform: translateY(0px); }
      35%   { transform: translateY(4.5px); }
      40%   { transform: translateY(45px); }
      50%   { transform: translateY(180px); }
      71%   { transform: translateY(428.6px); }
      72.5% { transform: translateY(441.2px); }
      75%   { transform: translateY(450px); }
      77.5% { transform: translateY(441.2px); }
      79%   { transform: translateY(428.6px); }
      100%  { transform: translateY(180px); }
    }
  </style>
</head>
<body>
  <div id="ui"></div>
  <script>
    const phrases = [
      "I love you", "Te amo", "Je t'aime", "Ti amo",
      "Eu te amo", "사랑해요", "愛してる", "我爱你",
      "Σ'αγαπώ", "Mahal kita", "أحبك", "Volim te",
      "Kocham cię", "Miluji tě", "Szeretlek", "Te iubesc",
      "Seni seviyorum".substring(0,11), "Ik hou van je".substring(0,11),
      "Nakupenda", "Я кохаю", "Обичам те",
      "გიყვარხარ", "Ndikukunda", "Ke a go rata".substring(0,11),
      "Aroha nui", "Mo nifẹ rẹ", "Ina sonki",
      "Ngiyakuthanda".substring(0,11), "T'estimo", "Mən sevir.",
      "Tôi yêu em", "Rwy'n caru", "Is breá liom",
      "Ngo oi nei", "Aloha au", "我愛你",
      "Ljubim te", "Miluju tě", "Rakastan", "Jag älskar",
      "Jeg elsker", "Saranghae", "Aishiteru", "Dost daram",
      "Bahibak", "Habibti", "Habibi", "사랑해",
      "Amor meu", "Kärlek", "ฉันรักคุณ", "Я люблю",
      "Ek is lief", "Lubim ťa", "Мен сүйем",
      "Es mīlu", "Aš myliu", "Ma armast.", "Ndinokuda",
      "Ndagukunda", "Ich liebe", "Prema", "Cinta",
    ];

// Trim all phrases to roughly similar display length
const trimmed = phrases.map(p => p.length > 13 ? p.substring(0, 11) + '…' : p);

const N = 120;
const ui = document.getElementById('ui');
for (let i = 0; i < N; i++) {
  const love = document.createElement('div');
  love.className = 'love';
  const delay = (i * -300) + 'ms';
  love.style.setProperty('--d', delay);

  const h = document.createElement('div');
  h.className = 'love_horizontal';
  h.style.setProperty('--d', delay);

  const v = document.createElement('div');
  v.className = 'love_vertical';
  v.style.setProperty('--d', delay);

  const word = document.createElement('div');
  word.className = 'love_word';
  word.textContent = trimmed[i % trimmed.length];

  v.appendChild(word);
  h.appendChild(v);
  love.appendChild(h);
  ui.appendChild(love);
}


</script>
</body>
</html>