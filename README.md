<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Franc</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #ffffff;
      height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }

    .top-bar {
      position: absolute;
      top: 20px;
      right: 20px;
    }

    .login-btn {
      padding: 8px 14px;
      border: 1px solid #ccc;
      border-radius: 20px;
      background: white;
      cursor: pointer;
      font-size: 14px;
    }

    .login-btn:hover {
      background: #f2f2f2;
    }

    .title {
      font-size: 80px;
      font-weight: bold;
      margin-bottom: 40px;
    }

    form {
      width: 100%;
      max-width: 600px;
      display: flex;
      border: 1px solid #ccc;
      border-radius: 30px;
      padding: 10px 20px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }

    input {
      flex: 1;
      border: none;
      outline: none;
      font-size: 18px;
    }

    .info-bar {
      margin-top: 20px;
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      justify-content: center;
    }

    .info-box {
      padding: 10px 14px;
      border: 1px solid #ddd;
      border-radius: 12px;
      background: #fafafa;
      font-size: 14px;
      min-width: 160px;
      text-align: center;
    }

    /* BOUTON IA */
    .ai-button {
      position: fixed;
      bottom: 20px;
      right: 20px;
      width: 55px;
      height: 55px;
      border-radius: 50%;
      background: #111;
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 22px;
      cursor: pointer;
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
    }

    /* PANEL IA */
    .ai-panel {
      position: fixed;
      bottom: 90px;
      right: 20px;
      width: 320px;
      height: 400px;
      background: white;
      border: 1px solid #ddd;
      border-radius: 15px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.2);
      display: none;
      flex-direction: column;
      overflow: hidden;
    }

    .ai-header {
      padding: 10px;
      background: #111;
      color: white;
      font-size: 14px;
    }

    .ai-messages {
      flex: 1;
      padding: 10px;
      overflow-y: auto;
      font-size: 14px;
    }

    .ai-input {
      display: flex;
      border-top: 1px solid #ddd;
    }

    .ai-input input {
      flex: 1;
      border: none;
      padding: 10px;
      outline: none;
    }

    .ai-input button {
      border: none;
      background: #111;
      color: white;
      padding: 10px;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <div class="top-bar">
    <button class="login-btn">Se connecter</button>
  </div>

  <div class="title">Franc</div>

  <form id="searchForm">
    <input type="text" id="searchInput" placeholder="Rechercher sur Franc...">
  </form>

  <div class="info-bar">
    <div class="info-box" id="timeBox"></div>
    <div class="info-box" id="dayBox"></div>
    <div class="info-box" id="saintBox"></div>
  </div>

  <!-- IA BUTTON -->
  <div class="ai-button" id="aiButton">✦✦</div>

  <!-- IA PANEL -->
  <div class="ai-panel" id="aiPanel">
    <div class="ai-header">IA Franc (API externe à connecter)</div>
    <div class="ai-messages" id="aiMessages"></div>
    <div class="ai-input">
      <input type="text" id="aiInput" placeholder="Demander quelque chose...">
      <button onclick="sendAI()">→</button>
    </div>
  </div>

  <script>
    const form = document.getElementById('searchForm');

    form.addEventListener('submit', function(e) {
      e.preventDefault();
      const query = document.getElementById('searchInput').value;

      if(query.trim() !== '') {
        window.location.href = 'https://www.google.com/search?q=' + encodeURIComponent(query);
      }
    });

    function updateTime() {
      const now = new Date();

      const time = now.toLocaleTimeString('fr-FR', {
        hour: '2-digit',
        minute: '2-digit'
      });

      const day = now.toLocaleDateString('fr-FR', {
        weekday: 'long',
        year: 'numeric',
        month: 'long',
        day: 'numeric'
      });

      const saints = {
        "1-1": "Sainte Marie",
        "25-12": "Noël (Jésus)",
        "11-11": "Saint Martin"
      };

      const key = (now.getDate()) + '-' + (now.getMonth() + 1);
      const saint = saints[key] || "Sainte du jour non définie";

      document.getElementById('timeBox').innerText = time;
      document.getElementById('dayBox').innerText = day;
      document.getElementById('saintBox').innerText = saint;
    }

    setInterval(updateTime, 60000);
    updateTime();

    // IA PANEL TOGGLE
    const aiButton = document.getElementById('aiButton');
    const aiPanel = document.getElementById('aiPanel');

    aiButton.addEventListener('click', () => {
      aiPanel.style.display = aiPanel.style.display === 'flex' ? 'none' : 'flex';
    });

    // IA FAKE RESPONSE (à connecter API plus tard)
    function sendAI() {
      const input = document.getElementById('aiInput');
      const messages = document.getElementById('aiMessages');

      if(input.value.trim() === '') return;

      const userMsg = document.createElement('div');
      userMsg.innerText = "Toi : " + input.value;
      messages.appendChild(userMsg);

      const botMsg = document.createElement('div');
      botMsg.innerText = "IA : (réponse simulée) Je dois être connectée à une API pour répondre intelligemment.";
      messages.appendChild(botMsg);

      input.value = '';
      messages.scrollTop = messages.scrollHeight;
    }
  </script>

</body>
</html>
