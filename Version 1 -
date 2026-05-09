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

    /* bouton connexion */
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

  <script>
    const form = document.getElementById('searchForm');

    form.addEventListener('submit', function(e) {
      e.preventDefault();
      const query = document.getElementById('searchInput').value;

      if(query.trim() !== '') {
        // redirection simple vers Google (temporaire)
        window.location.href = 'https://www.google.com/search?q=' + encodeURIComponent(query);
      }
    });
  </script>

</body>
</html>
