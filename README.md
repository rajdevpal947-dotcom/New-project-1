<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>A Special Message for My Love</title>
  <style>
    body {
        background-color: #222;
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        margin: 0;
        font-family: sans-serif;
        overflow: hidden;
    }
    #card-container {
        width: 375px;
        height: 800px;
        background-color: white;
        box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
        border-radius: 30px;
        overflow: hidden;
        position: relative;
        z-index: 1;
    }
    .page {
        width: 100%;
        height: 100%;
        position: absolute;
        top: 0;
        left: 0;
        opacity: 0;
        pointer-events: none;
        padding: 20px;
        box-sizing: border-box;
        text-align: center;
        transition: opacity 0.7s ease-in-out;
    }
    .page.active {
        opacity: 1;
        pointer-events: auto;
    }
    .content-box { padding: 20px; }
    h1 { color: #f47b9e; font-size: 2.2em; margin-top: 50px; }
    h2 { color: #8e44ad; font-size: 1.8em; }
    h3 { color: #e74c3c; font-size: 1.5em; }
    h4 { color: #9b59b6; font-size: 1em; font-weight: normal; }
    .main-image {
        max-width: 90%;
        max-height: 250px;
        border-radius: 10px;
        margin-bottom: 20px;
        transition: transform 0.5s ease;
    }
    .main-image:hover { transform: scale(1.05); }
    .letter-body { text-align: left; padding: 10px; font-size: 1.1em; font-family: cursive; line-height: 1.6; }
    .playlist { list-style: none; padding: 0; text-align: left; }
    .playlist a {
        color: #3498db;
        text-decoration: none;
        font-weight: bold;
        display: block;
        padding: 5px 0;
        transition: color 0.3s;
    }
    .playlist a:hover { color: #8e44ad; }
    button {
        background-color: #f47b9e;
        color: white;
        border: none;
        padding: 10px 20px;
        border-radius: 25px;
        cursor: pointer;
        font-size: 1.1em;
        margin-top: 30px;
        box-shadow: 0 4px #c25d7e;
        transition: background-color 0.2s, transform 0.2s;
    }
    button:hover { background-color: #c25d7e; transform: scale(1.05); }
    .caption { font-weight: bold; color: #e74c3c; margin-top: 10px; }

    /* Hearts Animation */
    .heart {
        position: absolute;
        width: 20px;
        height: 20px;
        background-color: #e74c3c;
        transform: rotate(45deg);
        animation: float 6s linear infinite;
        z-index: 0;
    }
    .heart::before,
    .heart::after {
        content: "";
        position: absolute;
        width: 20px;
        height: 20px;
        background-color: #e74c3c;
        border-radius: 50%;
    }
    .heart::before { top: -10px; left: 0; }
    .heart::after { left: 10px; top: 0; }

    @keyframes float {
        0% { transform: translateY(0) rotate(45deg); opacity: 0; }
        10% { opacity: 1; }
        100% { transform: translateY(-900px) rotate(45deg); opacity: 0; }
    }
  </style>
</head>
<body>

  <div id="card-container">
    <div class="page active" id="page-1">
      <div class="content-box">
        <img src="hello_kitty_intro.png" alt="Hello Kitty" class="main-image">
        <h1>Something Special Is Coming...</h1>
        <p>A special message is coming your way 💌</p>
        <button onclick="nextPage()">Open Letter</button>
      </div>
    </div>

    <div class="page" id="page-2">
      <div class="content-box">
        <h2>Dear Babe Girl</h2>
        <div class="letter-body">
          <p>I want to offer my sincerest apologies for the ways I have let you down. Please forgive me for my mistakes.</p>
          <p>With all my love,</p>
          <p>Yours sincerely,</p>
          <p>Rajdev Xd</p>
        </div>
        <button onclick="nextPage()">View Playlist</button>
      </div>
    </div>

    <div class="page" id="page-3">
      <div class="content-box">
        <h2>Songs Dedicated To You</h2>
        <p>Songs that remind me of you:</p>
        <ul class="playlist">
          <li><a href="#" target="_blank">O Tum Mere Ho</a></li>
          <li><a href="#" target="_blank">Meri Banaogi Kya</a></li>
          <li><a href="#" target="_blank">Maan Mera</a></li>
        </ul>
        <button onclick="nextPage()">Read Promise</button>
      </div>
    </div>

    <div class="page" id="page-4">
      <div class="content-box">
        <img src="funny_cat_meme.jpg" alt="Funny Cat" class="main-image">
        <h3>Last warning ok</h3>
        <p>I'm truly sorry and promise to do better. ❤️</p>
        <button onclick="nextPage()">Final Message</button>
      </div>
    </div>

    <div class="page" id="page-5">
      <div class="content-box">
        <h4>Please forgive my errors and help me find a brighter day.</h4>
        <img src="us_picture.jpg" alt="Us Together" class="main-image">
        <p class="caption">❤️ This is us btw ❤️</p>
        <h2>Don't be angryyyyyyy.</h2>
      </div>
    </div>
  </div>

  <script>
    let currentPage = 1;
    function nextPage() {
      const current = document.getElementById(`page-${currentPage}`);
      current.classList.remove("active");
      currentPage++;
      const next = document.getElementById(`page-${currentPage}`);
      if(next) {
        next.classList.add("active");
      }
    }

    // Add floating hearts dynamically
    const colors = ['#e74c3c', '#f47b9e', '#ff6b81'];
    for(let i=0; i<20; i++){
      const heart = document.createElement('div');
      heart.classList.add('heart');
      heart.style.left = Math.random() * window.innerWidth + 'px';
      heart.style.animationDuration = (4 + Math.random() * 4) + 's';
      heart.style.backgroundColor = colors[Math.floor(Math.random()*colors.length)];
      document.body.appendChild(heart);
    }
  </script>

</body>
</html>
