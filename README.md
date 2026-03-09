<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <title>Home</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', system-ui, sans-serif;
      color: #e0f0e0;
      min-height: 100vh;
      background: #060b06;
      overflow-x: hidden;
    }

    /* --- ФОН: чисто CSS, без внешних картинок --- */
    .bg {
      position: fixed;
      inset: 0;
      z-index: -1;
      background:
              radial-gradient(ellipse 120% 80% at 20% 50%, rgba(20,60,20,0.5) 0%, transparent 60%),
              radial-gradient(ellipse 100% 90% at 80% 30%, rgba(10,50,25,0.4) 0%, transparent 55%),
              radial-gradient(ellipse 80% 60% at 50% 100%, rgba(5,35,15,0.6) 0%, transparent 50%),
              linear-gradient(170deg, #080e08 0%, #0a1a0d 30%, #0d1f0d 50%, #081008 100%);
    }

    /* Зелёные "частицы" на фоне */
    .bg::before {
      content: '';
      position: absolute;
      inset: 0;
      background:
              radial-gradient(2px 2px at 10% 20%, rgba(76,175,80,0.3), transparent),
              radial-gradient(2px 2px at 30% 70%, rgba(76,175,80,0.2), transparent),
              radial-gradient(3px 3px at 60% 15%, rgba(76,175,80,0.25), transparent),
              radial-gradient(2px 2px at 80% 60%, rgba(76,175,80,0.2), transparent),
              radial-gradient(2px 2px at 50% 90%, rgba(76,175,80,0.15), transparent),
              radial-gradient(3px 3px at 90% 40%, rgba(76,175,80,0.2), transparent);
    }

    /* --- LAYOUT --- */
    .container {
      max-width: 1100px;
      margin: 0 auto;
      padding: 40px 24px 60px;
    }

    /* --- ВЕРХНЯЯ ЧАСТЬ --- */
    .top-section {
      text-align: center;
      margin-bottom: 28px;
    }

    .clock {
      font-size: 5.5rem;
      font-weight: 200;
      letter-spacing: -2px;
      line-height: 1;
      text-shadow: 0 4px 30px rgba(0,0,0,0.5);
    }

    .date {
      font-size: 1rem;
      opacity: 0.6;
      margin-top: 6px;
      font-weight: 400;
    }

    .greeting {
      font-size: 1.8rem;
      font-weight: 300;
      margin-top: 18px;
      text-shadow: 0 2px 16px rgba(0,0,0,0.4);
    }

    .weather {
      margin-top: 10px;
      font-size: 0.95rem;
      opacity: 0.7;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
    }

    /* --- ПОИСК --- */
    .search-wrap {
      max-width: 560px;
      margin: 24px auto;
      position: relative;
    }

    .search-wrap input {
      width: 100%;
      padding: 14px 20px 14px 48px;
      border-radius: 14px;
      border: 1px solid rgba(76,175,80,0.25);
      background: rgba(10,18,10,0.6);
      color: #e0f0e0;
      font-size: 1rem;
      font-family: inherit;
      outline: none;
      transition: border-color 0.3s, box-shadow 0.3s;
    }

    .search-wrap input::placeholder { color: rgba(200,230,201,0.35); }

    .search-wrap input:focus {
      border-color: rgba(76,175,80,0.6);
      box-shadow: 0 0 20px rgba(76,175,80,0.15);
    }

    .search-icon {
      position: absolute;
      left: 16px;
      top: 50%;
      transform: translateY(-50%);
      opacity: 0.35;
      font-size: 1.1rem;
    }

    /* --- POMODORO --- */
    .pomodoro {
      text-align: center;
      margin: 24px auto;
      max-width: 420px;
    }

    .pomo-tabs {
      display: flex;
      justify-content: center;
      background: rgba(10,18,10,0.5);
      border-radius: 12px;
      border: 1px solid rgba(76,175,80,0.15);
      overflow: hidden;
      margin-bottom: 14px;
    }

    .pomo-tab {
      padding: 10px 22px;
      cursor: pointer;
      font-size: 0.85rem;
      font-weight: 500;
      color: rgba(200,230,201,0.5);
      transition: all 0.25s;
      border: none;
      background: transparent;
      font-family: inherit;
    }

    .pomo-tab.active {
      background: rgba(76,175,80,0.2);
      color: #4caf50;
    }

    .pomo-tab:hover:not(.active) {
      color: #c8e6c9;
      background: rgba(76,175,80,0.08);
    }

    .pomo-time {
      font-size: 3.5rem;
      font-weight: 200;
      letter-spacing: 2px;
    }

    .pomo-controls {
      margin-top: 10px;
      display: flex;
      justify-content: center;
      gap: 14px;
    }

    .pomo-btn {
      width: 44px;
      height: 44px;
      border-radius: 50%;
      border: 1px solid rgba(76,175,80,0.3);
      background: rgba(10,18,10,0.5);
      color: #c8e6c9;
      font-size: 1.2rem;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.25s;
    }

    .pomo-btn:hover {
      border-color: #4caf50;
      color: #4caf50;
      box-shadow: 0 0 12px rgba(76,175,80,0.2);
    }

    /* --- ССЫЛКИ --- */
    .links-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(170px, 1fr));
      gap: 16px;
      margin: 32px 0;
    }

    .link-card {
      background: rgba(10, 18, 10, 0.55);
      border: 1px solid rgba(76, 175, 80, 0.18);
      border-radius: 16px;
      padding: 20px 16px;
      text-align: center;
      transition: all 0.3s ease;
    }

    .link-card:hover {
      border-color: rgba(76, 175, 80, 0.45);
      box-shadow: 0 0 20px rgba(76, 175, 80, 0.12);
      transform: translateY(-2px);
    }

    .link-card-icon {
      font-size: 2rem;
      margin-bottom: 10px;
      display: block;
    }

    .link-card-title {
      font-size: 0.75rem;
      font-weight: 700;
      color: #4caf50;
      text-transform: uppercase;
      letter-spacing: 1.5px;
      margin-bottom: 10px;
    }

    .link-card a {
      display: block;
      color: rgba(200, 230, 201, 0.7);
      text-decoration: none;
      font-size: 0.88rem;
      padding: 4px 0;
      transition: color 0.2s;
    }

    .link-card a:hover { color: #4caf50; }

    /* --- ЗАМЕТКИ --- */
    .notes-section {
      max-width: 560px;
      margin: 32px auto;
    }

    .notes-title {
      font-size: 0.75rem;
      font-weight: 700;
      color: #4caf50;
      text-transform: uppercase;
      letter-spacing: 1.5px;
      margin-bottom: 8px;
    }

    .notes-area {
      width: 100%;
      min-height: 110px;
      padding: 14px;
      border-radius: 14px;
      border: 1px solid rgba(76,175,80,0.18);
      background: rgba(10,18,10,0.55);
      color: #e0f0e0;
      font-family: inherit;
      font-size: 0.9rem;
      resize: vertical;
      outline: none;
      transition: border-color 0.3s;
    }

    .notes-area:focus { border-color: rgba(76,175,80,0.5); }

    /* --- Анимации --- */
    .fade-in { animation: fadeUp 0.5s ease both; }

    @keyframes fadeUp {
      0% { opacity: 0; transform: translateY(12px); }
      100% { opacity: 1; transform: translateY(0); }
    }

    .d1 { animation-delay: 0.05s; }
    .d2 { animation-delay: 0.1s; }
    .d3 { animation-delay: 0.15s; }
    .d4 { animation-delay: 0.2s; }
    .d5 { animation-delay: 0.25s; }
    .d6 { animation-delay: 0.3s; }
    .d7 { animation-delay: 0.35s; }
  </style>
</head>
<body>

<div class="bg"></div>

<div class="container">

  <div class="top-section fade-in d1">
    <div class="clock" id="clock">00:00:00</div>
    <div class="date" id="date"></div>
    <div class="greeting" id="greeting"></div>
  </div>

  <div class="search-wrap fade-in d2">
    <span class="search-icon">🔍</span>
    <input type="text" id="search" placeholder="Искать в Google..." autocomplete="off">
  </div>

  <div class="pomodoro fade-in d3">
    <div class="pomo-tabs">
      <button class="pomo-tab active" data-time="25">Pomodoro</button>
      <button class="pomo-tab" data-time="5">Перерыв</button>
      <button class="pomo-tab" data-time="15">Длинный перерыв</button>
    </div>
    <div class="pomo-time" id="pomo-time">25:00</div>
    <div class="pomo-controls">
      <button class="pomo-btn" id="pomo-play" title="Старт/Пауза">▶</button>
      <button class="pomo-btn" id="pomo-reset" title="Сброс">↻</button>
    </div>
  </div>

  <div class="links-grid">
    <div class="link-card fade-in d3">
      <span class="link-card-icon">💻</span>
      <div class="link-card-title">Dev</div>
      <a href="https://github.com">GitHub</a>
      <a href="https://stackoverflow.com">StackOverflow</a>
      <a href="https://leetcode.com">LeetCode</a>
      <a href="https://codeforces.com">CodeForces</a>
    </div>
    <div class="link-card fade-in d4">
      <span class="link-card-icon">🎓</span>
      <div class="link-card-title">Education</div>
      <a href="https://www.asu.ru">AGU</a>
      <a href="https://doka.guide">Doka</a>
      <a href="https://2gis.ru">2GIS</a>
      <a href="https://coursera.org">Coursera</a>
    </div>
    <div class="link-card fade-in d5">
      <span class="link-card-icon">🎬</span>
      <div class="link-card-title">Media</div>
      <a href="https://youtube.com">YouTube</a>
      <a href="https://open.spotify.com">Spotify</a>
      <a href="https://vk.com">VK</a>
      <a href="https://reddit.com">Reddit</a>
    </div>
    <div class="link-card fade-in d6">
      <span class="link-card-icon">💬</span>
      <div class="link-card-title">Chats</div>
      <a href="https://discord.com/app">Discord</a>
      <a href="https://web.telegram.org">Telegram</a>
      <a href="https://mail.google.com">Gmail</a>
      <a href="https://drive.google.com">Google Cloud</a>
    </div>
    <div class="link-card fade-in d7">
      <span class="link-card-icon">🤖</span>
      <div class="link-card-title">AI</div>
      <a href="https://gemini.google.com">Gemini</a>
      <a href="https://chat.openai.com">ChatGPT</a>
      <a href="https://github.com/copilot">Copilot</a>
      <a href="https://deepseek.com">DeepSeek</a>
    </div>
  </div>
</div>

<script>
  // === ЧАСЫ ===
  function updateClock() {
    var now = new Date();
    var h = String(now.getHours()).padStart(2, '0');
    var m = String(now.getMinutes()).padStart(2, '0');
    var s = String(now.getSeconds()).padStart(2, '0');
    document.getElementById('clock').textContent = h + ':' + m + ':' + s;

    var days = ['воскресенье','понедельник','вторник','среда','четверг','пятница','суббота'];
    var months = ['января','февраля','марта','апреля','мая','июня','июля','августа','сентября','октября','ноября','декабря'];
    document.getElementById('date').textContent = days[now.getDay()] + ', ' + now.getDate() + ' ' + months[now.getMonth()];

    var hour = now.getHours();
    var greet = 'Доброй ночи';
    if (hour >= 5 && hour < 12) greet = 'Доброе утро';
    else if (hour >= 12 && hour < 18) greet = 'Добрый день';
    else if (hour >= 18 && hour < 23) greet = 'Добрый вечер';
    document.getElementById('greeting').textContent = greet + ', qwizzit';
  }
  updateClock();
  setInterval(updateClock, 1000);

  // === ПОИСК ===
  document.getElementById('search').addEventListener('keydown', function(e) {
    if (e.key === 'Enter' && e.target.value.trim()) {
      window.location.href = 'https://www.google.com/search?q=' + encodeURIComponent(e.target.value.trim());
    }
  });

  // === POMODORO ===
  var pomoTime = 25 * 60;
  var pomoInterval = null;
  var pomoRunning = false;

  function updatePomoDisplay() {
    var m = String(Math.floor(pomoTime / 60)).padStart(2, '0');
    var s = String(pomoTime % 60).padStart(2, '0');
    document.getElementById('pomo-time').textContent = m + ':' + s;
  }

  var tabs = document.querySelectorAll('.pomo-tab');
  for (var i = 0; i < tabs.length; i++) {
    tabs[i].addEventListener('click', function() {
      for (var j = 0; j < tabs.length; j++) tabs[j].classList.remove('active');
      this.classList.add('active');
      clearInterval(pomoInterval);
      pomoRunning = false;
      document.getElementById('pomo-play').textContent = '▶';
      pomoTime = parseInt(this.getAttribute('data-time')) * 60;
      updatePomoDisplay();
    });
  }

  document.getElementById('pomo-play').addEventListener('click', function() {
    if (pomoRunning) {
      clearInterval(pomoInterval);
      pomoRunning = false;
      this.textContent = '▶';
    } else {
      pomoRunning = true;
      this.textContent = '⏸';
      pomoInterval = setInterval(function() {
        if (pomoTime <= 0) {
          clearInterval(pomoInterval);
          pomoRunning = false;
          document.getElementById('pomo-play').textContent = '▶';
          try { new Audio('data:audio/wav;base64,UklGRl9vT19teleXQBAABAAQAIABAAAAA').play(); } catch(e) {}
          return;
        }
        pomoTime--;
        updatePomoDisplay();
      }, 1000);
    }
  });

  document.getElementById('pomo-reset').addEventListener('click', function() {
    clearInterval(pomoInterval);
    pomoRunning = false;
    document.getElementById('pomo-play').textContent = '▶';
    var active = document.querySelector('.pomo-tab.active');
    pomoTime = parseInt(active.getAttribute('data-time')) * 60;
    updatePomoDisplay();
  });
</script>

</body>
</html>

