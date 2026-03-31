<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>بوت الزخرفة</title>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700;900&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #080810;
    --surface: #10101e;
    --card: #14142a;
    --border: #1e1e3a;
    --orange: #ff5c00;
    --orange2: #ff8c42;
    --text: #f0f0ff;
    --muted: #6666aa;
    --bot-bubble: #14142a;
    --user-bubble: linear-gradient(135deg, #ff5c00, #ff8c42);
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Cairo', sans-serif;
    font-weight: 700;
    background: var(--bg);
    color: var(--text);
    height: 100vh;
    display: flex;
    flex-direction: column;
    overflow: hidden;
  }

  body::before {
    content: "";
    position: fixed;
    inset: 0;
    background:
      radial-gradient(ellipse 60% 40% at 20% 10%, rgba(255,92,0,.1) 0%, transparent 70%),
      radial-gradient(ellipse 50% 50% at 80% 90%, rgba(255,140,66,.07) 0%, transparent 60%);
    pointer-events: none;
    z-index: 0;
  }

  /* ── Header ── */
  .header {
    position: relative;
    z-index: 1;
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 16px 20px;
    background: var(--surface);
    border-bottom: 1px solid var(--border);
  }

  .avatar {
    width: 44px;
    height: 44px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--orange), var(--orange2));
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.3rem;
    flex-shrink: 0;
  }

  .header-info .name {
    font-size: 1rem;
    font-weight: 900;
    color: var(--text);
  }

  .header-info .status {
    font-size: .75rem;
    font-weight: 400;
    color: #22c55e;
  }

  /* ── Chat ── */
  .chat {
    position: relative;
    z-index: 1;
    flex: 1;
    overflow-y: auto;
    padding: 20px 16px;
    display: flex;
    flex-direction: column;
    gap: 14px;
    scroll-behavior: smooth;
  }

  .chat::-webkit-scrollbar { width: 4px; }
  .chat::-webkit-scrollbar-track { background: transparent; }
  .chat::-webkit-scrollbar-thumb { background: var(--border); border-radius: 4px; }

  /* ── Bubbles ── */
  .row {
    display: flex;
    align-items: flex-end;
    gap: 8px;
    animation: popIn .25s ease both;
  }

  @keyframes popIn {
    from { opacity: 0; transform: translateY(10px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .row.bot  { flex-direction: row; }
  .row.user { flex-direction: row-reverse; }

  .bubble-avatar {
    width: 32px;
    height: 32px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--orange), var(--orange2));
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: .85rem;
    flex-shrink: 0;
  }

  .bubble {
    max-width: 75%;
    padding: 12px 16px;
    border-radius: 18px;
    font-size: .95rem;
    font-weight: 400;
    line-height: 1.6;
  }

  .row.bot .bubble {
    background: var(--bot-bubble);
    border: 1px solid var(--border);
    border-bottom-right-radius: 4px;
  }

  .row.user .bubble {
    background: var(--user-bubble);
    color: #fff;
    font-weight: 700;
    border-bottom-left-radius: 4px;
  }

  /* styles grid inside bubble */
  .styles-grid {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-top: 10px;
  }

  .style-row {
    background: #0f0f1e;
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 10px 14px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 10px;
  }

  .style-info { flex: 1; }

  .style-label {
    font-size: .65rem;
    font-weight: 900;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--orange);
    margin-bottom: 4px;
  }

  .style-name {
    font-size: 1.1rem;
    color: #fff;
    word-break: break-all;
  }

  .cp {
    padding: 5px 12px;
    border-radius: 7px;
    border: 1.5px solid var(--border);
    background: transparent;
    color: var(--muted);
    font-family: 'Cairo', sans-serif;
    font-weight: 700;
    font-size: .75rem;
    cursor: pointer;
    white-space: nowrap;
    transition: all .2s;
    flex-shrink: 0;
  }

  .cp:hover { border-color: var(--orange); color: var(--orange); }
  .cp.done  { border-color: #22c55e; color: #22c55e; }

  /* ── Input area ── */
  .input-area {
    position: relative;
    z-index: 1;
    display: flex;
    gap: 10px;
    padding: 14px 16px;
    background: var(--surface);
    border-top: 1px solid var(--border);
  }

  input {
    flex: 1;
    background: var(--card);
    border: 2px solid var(--border);
    border-radius: 12px;
    padding: 12px 16px;
    color: var(--text);
    font-family: 'Cairo', sans-serif;
    font-weight: 700;
    font-size: .95rem;
    outline: none;
    transition: border-color .2s;
  }

  input::placeholder { color: var(--muted); font-weight: 400; }
  input:focus { border-color: var(--orange); }

  .send-btn {
    width: 46px;
    height: 46px;
    border-radius: 12px;
    border: none;
    background: linear-gradient(135deg, var(--orange), var(--orange2));
    color: #fff;
    font-size: 1.2rem;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: transform .15s, box-shadow .15s;
    box-shadow: 0 4px 16px rgba(255,92,0,.3);
    flex-shrink: 0;
  }

  .send-btn:hover { transform: scale(1.07); }
  .send-btn:active { transform: scale(.97); }

  /* typing indicator */
  .typing {
    display: flex;
    align-items: center;
    gap: 5px;
    padding: 12px 16px;
  }

  .dot {
    width: 7px; height: 7px;
    border-radius: 50%;
    background: var(--muted);
    animation: bounce .9s infinite;
  }

  .dot:nth-child(2) { animation-delay: .15s; }
  .dot:nth-child(3) { animation-delay: .3s; }

  @keyframes bounce {
    0%, 60%, 100% { transform: translateY(0); }
    30% { transform: translateY(-6px); }
  }
</style>
</head>
<body>

<div class="header">
  <div class="avatar">🤖</div>
  <div class="header-info">
    <div class="name">بوت الزخرفة</div>
    <div class="status">متصل الآن</div>
  </div>
</div>

<div class="chat" id="chat"></div>

<div class="input-area">
  <input id="inp" type="text" placeholder="اكتب هنا..." maxlength="30">
  <button class="send-btn" onclick="send()">&#10148;</button>
</div>

<script>
const STYLES = [
  { label: "Bold",         map: "𝗔𝗕𝗖𝗗𝗘𝗙𝗚𝗛𝗜𝗝𝗞𝗟𝗠𝗡𝗢𝗣𝗤𝗥𝗦𝗧𝗨𝗩𝗪𝗫𝗬𝗭𝗮𝗯𝗰𝗱𝗲𝗳𝗴𝗵𝗶𝗷𝗸𝗹𝗺𝗻𝗼𝗽𝗾𝗿𝘀𝘁𝘂𝘃𝘄𝘅𝘆𝘇" },
  { label: "Italic",       map: "𝘈𝘉𝘊𝘋𝘌𝘍𝘎𝘏𝘐𝘑𝘒𝘓𝘔𝘕𝘖𝘗𝘘𝘙𝘚𝘛𝘜𝘝𝘞𝘟𝘠𝘡𝘢𝘣𝘤𝘥𝘦𝘧𝘨𝘩𝘪𝘫𝘬𝘭𝘮𝘯𝘰𝘱𝘲𝘳𝘴𝘵𝘶𝘷𝘸𝘹𝘺𝘻" },
  { label: "Bold Italic",  map: "𝑨𝑩𝑪𝑫𝑬𝑭𝑮𝑯𝑰𝑱𝑲𝑳𝑴𝑵𝑶𝑷𝑸𝑹𝑺𝑻𝑼𝑽𝑾𝑿𝒀𝒁𝒂𝒃𝒄𝒅𝒆𝒇𝒈𝒉𝒊𝒋𝒌𝒍𝒎𝒏𝒐𝒑𝒒𝒓𝒔𝒕𝒖𝒗𝒘𝒙𝒚𝒛" },
  { label: "Script",       map: "𝒜ℬ𝒞𝒟ℰℱ𝒢ℋℐ𝒥𝒦ℒℳ𝒩𝒪𝒫𝒬ℛ𝒮𝒯𝒰𝒱𝒲𝒳𝒴𝒵𝒶𝒷𝒸𝒹𝑒𝒻𝑔𝒽𝒾𝒿𝓀𝓁𝓂𝓃𝑜𝓅𝓆𝓇𝓈𝓉𝓊𝓋𝓌𝓍𝓎𝓏" },
  { label: "Bold Script",  map: "𝓐𝓑𝓒𝓓𝓔𝓕𝓖𝓗𝓘𝓙𝓚𝓛𝓜𝓝𝓞𝓟𝓠𝓡𝓢𝓣𝓤𝓥𝓦𝓧𝓨𝓩𝓪𝓫𝓬𝓭𝓮𝓯𝓰𝓱𝓲𝓳𝓴𝓵𝓶𝓷𝓸𝓹𝓺𝓻𝓼𝓽𝓾𝓿𝔀𝔁𝔂𝔃" },
  { label: "Fraktur",      map: "𝔄𝔅ℭ𝔇𝔈𝔉𝔊ℌℑ𝔍𝔎𝔏𝔐𝔑𝔒𝔓𝔔ℜ𝔖𝔗𝔘𝔙𝔚𝔛𝔜ℨ𝔞𝔟𝔠𝔡𝔢𝔣𝔤𝔥𝔦𝔧𝔨𝔩𝔪𝔫𝔬𝔭𝔮𝔯𝔰𝔱𝔲𝔳𝔴𝔵𝔶𝔷" },
  { label: "Double Struck",map: "𝔸𝔹ℂ𝔻𝔼𝔽𝔾ℍ𝕀𝕁𝕂𝕃𝕄ℕ𝕆ℙℚℝ𝕊𝕋𝕌𝕍𝕎𝕏𝕐ℤ𝕒𝕓𝕔𝕕𝕖𝕗𝕘𝕙𝕚𝕛𝕜𝕝𝕞𝕟𝕠𝕡𝕢𝕣𝕤𝕥𝕦𝕧𝕨𝕩𝕪𝕫" },
  { label: "Circled",      map: "ⒶⒷⒸⒹⒺⒻⒼⒽⒾⒿⓀⓁⓂⓃⓄⓅⓆⓇⓈⓉⓊⓋⓌⓍⓎⓏⓐⓑⓒⓓⓔⓕⓖⓗⓘⓙⓚⓛⓜⓝⓞⓟⓠⓡⓢⓣⓤⓥⓦⓧⓨⓩ" },
  { label: "Wide",         map: "ＡＢＣＤＥＦＧＨＩＪＫＬＭＮＯＰＱＲＳＴＵＶＷＸＹＺａｂｃｄｅｆｇｈｉｊｋｌｍｎｏｐｑｒｓｔｕｖｗｘｙｚ" },
  { label: "Bold Fraktur", map: "𝕬𝕭𝕮𝕯𝕰𝕱𝕲𝕳𝕴𝕵𝕶𝕷𝕸𝕹𝕺𝕻𝕼𝕽𝕾𝕿𝖀𝖁𝖂𝖃𝖄𝖅𝖆𝖇𝖈𝖉𝖊𝖋𝖌𝖍𝖎𝖏𝖐𝖑𝖒𝖓𝖔𝖕𝖖𝖗𝖘𝖙𝖚𝖛𝖜𝖝𝖞𝖟" },
];

const U = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
const L = "abcdefghijklmnopqrstuvwxyz";

function convert(text, map) {
  const chars = [...map];
  const up = chars.slice(0,26), lo = chars.slice(26,52);
  return [...text].map(c => {
    const ui = U.indexOf(c), li = L.indexOf(c);
    if (ui !== -1) return up[ui] || c;
    if (li !== -1) return lo[li] || c;
    return c;
  }).join("");
}

const chat = document.getElementById("chat");
let waitingForName = false;
let msgCount = 0;

function addBubble(type, html) {
  const row = document.createElement("div");
  row.className = "row " + type;
  const av = type === "bot" ? `<div class="bubble-avatar">🤖</div>` : "";
  row.innerHTML = `${av}<div class="bubble">${html}</div>`;
  chat.appendChild(row);
  chat.scrollTop = chat.scrollHeight;
}

function showTyping() {
  const row = document.createElement("div");
  row.className = "row bot";
  row.id = "typing";
  row.innerHTML = `<div class="bubble-avatar">🤖</div>
    <div class="bubble"><div class="typing"><div class="dot"></div><div class="dot"></div><div class="dot"></div></div></div>`;
  chat.appendChild(row);
  chat.scrollTop = chat.scrollHeight;
}

function removeTyping() {
  const t = document.getElementById("typing");
  if (t) t.remove();
}

function botReply(html, delay = 900) {
  showTyping();
  setTimeout(() => {
    removeTyping();
    addBubble("bot", html);
  }, delay);
}

function styleResults(name) {
  const rows = STYLES.map((s, i) => {
    const styled = convert(name, s.map);
    return `<div class="style-row">
      <div class="style-info">
        <div class="style-label">${s.label}</div>
        <div class="style-name" id="sn${msgCount}_${i}">${styled}</div>
      </div>
      <button class="cp" onclick="cp('sn${msgCount}_${i}', this)">نسخ</button>
    </div>`;
  }).join("");
  msgCount++;
  return `<div>هذه أنماط اسم <b>${name}</b>:</div><div class="styles-grid">${rows}</div>`;
}

function cp(id, btn) {
  const el = document.getElementById(id);
  if (!el) return;
  navigator.clipboard.writeText(el.innerText).then(() => {
    btn.textContent = "تم";
    btn.classList.add("done");
    setTimeout(() => { btn.textContent = "نسخ"; btn.classList.remove("done"); }, 2000);
  });
}

function send() {
  const inp = document.getElementById("inp");
  const text = inp.value.trim();
  if (!text) return;
  inp.value = "";

  addBubble("user", text);

  const lower = text.toLowerCase();

  if (!waitingForName) {
    if (lower.includes("اسم") || lower.includes("زخرف") || lower.includes("name") || lower.includes("نعم") || lower.includes("اوكي") || lower.includes("okay") || lower.includes("ok") || lower.includes("يلا") || lower.includes("ابدا")) {
      waitingForName = true;
      botReply("تمام! أرسل لي الاسم الذي تريد تحويله.");
    } else {
      botReply("مرحباً! أنا هنا لمساعدتك في تحويل الأسماء. هل تريد أن أحول لك اسماً؟");
    }
  } else {
    waitingForName = false;
    const result = styleResults(text);
    botReply(result, 1100);
    setTimeout(() => {
      botReply("هل تريد تحويل اسم آخر؟", 2200);
      waitingForName = false;
    }, 2200);
  }
}

document.getElementById("inp").addEventListener("keydown", e => {
  if (e.key === "Enter") send();
});

// Initial bot message
setTimeout(() => {
  botReply("مرحباً! أنا بوت تحويل الأسماء 🤖<br>هل تريد أن أحول لك اسماً؟", 600);
  waitingForName = false;
}, 400);
</script>
</body>
</html>
