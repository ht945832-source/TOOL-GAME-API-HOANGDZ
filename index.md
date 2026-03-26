
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <title>TOOL TÀI XỈU HOANGDZ</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <script src="https://cdn.jsdelivr.net/npm/particles.js"></script>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      overflow: hidden;
      height: 100%;
      touch-action: manipulation;
      -webkit-tap-highlight-color: transparent;
    }

    #gameSelect {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: url('https://i.postimg.cc/T35VPGmh/2d5ab14f89532f6529fb2cf0f0cf4f3c.jpg') no-repeat center center;
      background-size: cover;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      overflow-y: auto;
      padding: 20px 0;
    }

    #gameSelect::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle at center, rgba(255,182,193,0.2) 0%, rgba(199,21,133,0.4) 100%);
      z-index: -1;
    }

    h2 {
      color: #ffffff;
      margin-bottom: 30px;
      font-size: 28px;
      text-align: center;
      text-shadow: 0 0 15px rgba(255, 182, 193, 0.7);
      position: relative;
      padding-bottom: 15px;
    }

    h2::after {
      content: "";
      display: block;
      width: 150px;
      height: 3px;
      background: linear-gradient(90deg, transparent, #ffffff, transparent);
      margin: 15px auto 0;
      border-radius: 3px;
    }

    .main-categories {
      display: flex;
      flex-direction: column;
      gap: 20px;
      width: 90%;
      max-width: 500px;
    }

    .main-category {
      background: rgba(255, 255, 255, 0.15);
      border-radius: 15px;
      padding: 20px;
      cursor: pointer;
      transition: all 0.3s;
      text-align: center;
      border: 1px solid rgba(255, 255, 255, 0.2);
      box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
      backdrop-filter: blur(10px);
      -webkit-backdrop-filter: blur(10px);
      animation: pulse 2s infinite;
    }

    .main-category:nth-child(2) {
      animation-delay: 0.3s;
    }

    .main-category:nth-child(3) {
      animation-delay: 0.6s;
    }

    @keyframes pulse {
      0% { box-shadow: 0 0 0 0 rgba(255, 182, 193, 0.4); }
      70% { box-shadow: 0 0 0 15px rgba(255, 182, 193, 0); }
      100% { box-shadow: 0 0 0 0 rgba(255, 182, 193, 0); }
    }

    .main-category:hover {
      background: rgba(255, 255, 255, 0.25);
      transform: translateY(-5px) scale(1.02);
      box-shadow: 0 12px 40px rgba(255, 182, 193, 0.3);
    }

    .main-category img {
      width: 80px;
      height: 80px;
      margin-bottom: 15px;
      border-radius: 15px;
      border: 2px solid rgba(255, 255, 255, 0.3);
      box-shadow: 0 0 15px rgba(255, 182, 193, 0.5);
      transition: transform 0.3s;
    }

    .main-category:active img {
      transform: scale(0.95);
    }

    .main-category span {
      font-size: 20px;
      font-weight: 600;
      color: #ffffff;
      text-shadow: 0 0 5px rgba(255, 255, 255, 0.5);
      display: block;
    }

    /* Styles for sub-games (hidden by default) */
    .sub-games {
      display: none;
      width: 90%;
      max-width: 900px;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 15px;
      padding: 20px;
      box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
      border: 1px solid rgba(255, 255, 255, 0.15);
      margin-top: 20px;
      backdrop-filter: blur(15px);
      -webkit-backdrop-filter: blur(15px);
    }

    .sub-games.active {
      display: block;
      animation: fadeIn 0.5s ease-out;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .game-section-title {
      color: #ffffff;
      text-align: center;
      margin-bottom: 15px;
      font-size: 22px;
      text-shadow: 0 0 10px rgba(255, 255, 255, 0.7);
      padding-bottom: 10px;
      border-bottom: 1px solid rgba(255, 255, 255, 0.2);
    }

    .gameOptionsContainer {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 15px;
    }

    .gameOption {
      display: flex;
      align-items: center;
      justify-content: flex-start;
      margin: 0;
      padding: 15px 20px;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 15px;
      cursor: pointer;
      transition: all 0.3s;
      width: 250px;
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
      backdrop-filter: blur(10px);
      -webkit-backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 255, 255, 0.15);
    }

    .gameOption:active {
      transform: scale(0.98);
    }

    .gameOption:hover {
      background: rgba(255, 255, 255, 0.2);
      transform: translateY(-3px);
    }

    .gameOption img {
      width: 40px;
      height: 40px;
      margin-right: 15px;
      border-radius: 10px;
      border: 2px solid rgba(255, 255, 255, 0.3);
      box-shadow: 0 0 10px rgba(255, 182, 193, 0.3);
      transition: transform 0.2s;
    }

    .gameOption:active img {
      transform: scale(0.9);
    }

    .gameOption span {
      font-size: 16px;
      font-weight: 600;
      color: #ffffff;
      text-shadow: 0 0 5px rgba(255, 255, 255, 0.5);
    }

    /* Back button */
    #backButton {
      position: fixed;
      top: 15px;
      left: 15px;
      padding: 12px 20px;
      background: rgba(255, 255, 255, 0.2);
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      z-index: 1001;
      display: none;
      font-weight: bold;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
      transition: all 0.3s;
      font-size: 16px;
      backdrop-filter: blur(10px);
      -webkit-backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 255, 255, 0.2);
      min-width: 100px;
      touch-action: manipulation;
    }

    #backButton:active {
      transform: scale(0.95);
    }

    #backButton:hover {
      background: rgba(255, 255, 255, 0.3);
      transform: translateY(-1px);
    }

    iframe {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      border: none;
      display: none;
      z-index: 1;
    }

    #robotContainer {
      position: fixed;
      top: 50%;
      left: 30px;
      transform: translateY(-50%);
      display: none;
      align-items: center;
      z-index: 9999;
      cursor: move;
      touch-action: none;
    }

    #robotInner {
      transform: rotate(90deg);
      transform-origin: left center;
      display: flex;
      align-items: center;
    }

    #robotIcon {
      width: 120px;
      height: 120px;
      margin-right: 15px;
      pointer-events: none;
      border: none;
      box-shadow: none;
    }

    #robotText {
      background: rgba(147, 39, 143, 0.7);
      color: #ffffff;
      padding: 12px 15px;
      border-radius: 10px;
      font-size: 15px;
      line-height: 1.4;
      box-shadow: 0 3px 10px rgba(199, 21, 133, 0.5);
      white-space: nowrap;
      max-width: 280px;
      position: relative;
      border: 1px solid rgba(255, 182, 193, 0.5);
      backdrop-filter: blur(10px);
      -webkit-backdrop-filter: blur(10px);
    }

    #line1, #line2 {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    strong {
      font-weight: bold;
    }

    #loadingIndicator {
      display: none;
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: rgba(147, 39, 143, 0.9);
      color: #ffb6c1;
      padding: 20px 30px;
      border-radius: 12px;
      z-index: 1002;
      backdrop-filter: blur(10px);
      -webkit-backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 182, 193, 0.5);
      box-shadow: 0 0 30px rgba(255, 105, 180, 0.5);
      font-size: 18px;
      text-align: center;
    }

    .tai {
      color: #98fb98;
      font-weight: bold;
      text-shadow: 0 0 5px rgba(152, 251, 152, 0.7);
    }

    .xiu {
      color: #ff6b6b;
      font-weight: bold;
      text-shadow: 0 0 5px rgba(255, 107, 107, 0.7);
    }

    /* Game Interface Styles */
    #gameInterface {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: url('https://i.postimg.cc/9Fw1y4v3/pink-galaxy.jpg') no-repeat center center;
      background-size: cover;
      z-index: 900;
      overflow: auto;
      touch-action: manipulation;
    }

    #gameInterface::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle at center, rgba(255,105,180,0.3) 0%, rgba(147,39,143,0.7) 100%);
      z-index: -1;
    }

    #particles-js {
      position: fixed;
      width: 100%;
      height: 100%;
      z-index: -1;
    }

    .wrapper {
      max-width: 440px;
      margin: 30px auto;
      background: rgba(147, 39, 143, 0.85);
      padding: 25px;
      border-radius: 20px;
      box-shadow: 0 0 30px rgba(255, 105, 180, 0.5);
      backdrop-filter: blur(10px);
      -webkit-backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 182, 193, 0.5);
      position: relative;
      overflow: hidden;
    }

    .wrapper::before {
      content: "";
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: linear-gradient(
        to bottom right,
        transparent 0%,
        rgba(255, 182, 193, 0.1) 50%,
        transparent 100%
      );
      transform: rotate(30deg);
      animation: shine 6s infinite linear;
    }

    @keyframes shine {
      0% { transform: rotate(30deg) translate(-30%, -30%); }
      100% { transform: rotate(30deg) translate(30%, 30%); }
    }

    .game-title {
      text-align: center;
      color: #ffb6c1;
      text-shadow: 0 0 15px #ffb6c1;
      margin-bottom: 25px;
      font-size: 28px;
      letter-spacing: 1px;
      position: relative;
    }

    .game-title::after {
      content: "";
      display: block;
      width: 150px;
      height: 3px;
      background: linear-gradient(90deg, transparent, #ffb6c1, transparent);
      margin: 15px auto 0;
      border-radius: 3px;
    }

    .circle {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      border: 3px solid #ffb6c1;
      margin: 20px auto;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 26px;
      font-weight: bold;
      background: rgba(119, 0, 119, 0.7);
      box-shadow: 0 0 30px rgba(255, 105, 180, 0.7), inset 0 0 20px rgba(255, 182, 193, 0.3);
      color: white;
      position: relative;
      overflow: hidden;
      transition: all 0.3s;
    }

    .circle::before {
      content: "";
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: radial-gradient(circle, rgba(255, 182, 193, 0.1) 0%, transparent 70%);
      animation: rotate 15s linear infinite;
    }

    @keyframes rotate {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    .status, .time {
      text-align: center;
      margin-top: 8px;
      font-size: 16px;
      color: #ffb6c1;
      text-shadow: 0 0 5px rgba(255, 105, 180, 0.5);
    }

    .stats {
      text-align: center;
      margin: 20px 0;
      font-size: 16px;
      background: rgba(199, 21, 133, 0.3);
      border-radius: 12px;
      padding: 12px;
      color: #ffffff;
      border: 1px solid rgba(255, 182, 193, 0.5);
      box-shadow: 0 0 15px rgba(255, 105, 180, 0.3);
      backdrop-filter: blur(5px);
      -webkit-backdrop-filter: blur(5px);
    }

    .history-table {
      width: 100%;
      margin-top: 15px;
      border-collapse: collapse;
      font-size: 14px;
      background: rgba(119, 0, 119, 0.7);
      border-radius: 12px;
      overflow: hidden;
      box-shadow: 0 0 20px rgba(199, 21, 133, 0.3);
      border: 1px solid rgba(255, 182, 193, 0.5);
    }

    .history-table th, .history-table td {
      padding: 10px;
      border-bottom: 1px solid rgba(199, 21, 133, 0.3);
      text-align: center;
    }

    .history-table th {
      background: rgba(199, 21, 133, 0.7);
      color: #ffb6c1;
      font-weight: 600;
      text-shadow: 0 0 5px rgba(255, 105, 180, 0.5);
    }

    .tai-cell { 
      background: linear-gradient(135deg, #77dd77, #98fb98);
      color: black; 
      padding: 5px 12px; 
      border-radius: 8px; 
      font-weight: bold;
      box-shadow: 0 0 10px rgba(152, 251, 152, 0.7);
      display: inline-block;
      min-width: 50px;
    }

    .xiu-cell { 
      background: linear-gradient(135deg, #ff6b6b, #ff8e8e);
      color: white; 
      padding: 5px 12px; 
      border-radius: 8px; 
      font-weight: bold;
      box-shadow: 0 0 10px rgba(255, 107, 107, 0.7);
      display: inline-block;
      min-width: 50px;
    }

    .win { 
      color: #98fb98; 
      font-weight: bold; 
      text-shadow: 0 0 8px rgba(152, 251, 152, 0.7);
    }

    .lose { 
      color: #ff6b6b; 
      font-weight: bold; 
      text-shadow: 0 0 8px rgba(255, 107, 107, 0.7);
    }

    .pending { 
      color: #e6e6fa; 
      font-style: italic; 
    }

    #phienText {
      font-size: 24px;
      color: #ffffff;
      background: rgba(199, 21, 133, 0.6);
      padding: 8px 16px;
      border-radius: 8px;
      text-shadow: 0 0 15px #ffb6c1;
      font-weight: bold;
      border: 2px solid #ffb6c1;
      box-shadow: 0 0 20px rgba(255, 105, 180, 0.5);
    }

    #prediction {
      font-size: 28px;
      font-weight: bold;
      color: white;
      text-shadow: 0 0 15px currentColor;
    }

    #extraInfo {
      color: #ffb6c1;
      font-size: 16px;
      margin: 15px 0;
      text-shadow: 0 0 5px rgba(255, 105, 180, 0.5);
    }

    #status {
      color: #ffd700;
      font-weight: bold;
      font-size: 16px;
      text-shadow: 0 0 5px rgba(255, 215, 0, 0.5);
    }

    #clock {
      color: #ffffff;
      font-size: 18px;
      margin: 10px 0;
      text-shadow: 0 0 5px rgba(255, 105, 180, 0.5);
    }

    #winStats {
      color: #ffffff;
      font-weight: bold;
      font-size: 16px;
    }

    #historyBody tr:first-child {
      background: rgba(255, 105, 180, 0.15);
    }

    #historyBody tr:hover {
      background: rgba(199, 21, 133, 0.3);
    }

    /* Animation for game title */
    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-8px); }
    }

    .float-1 { animation: float 3s ease-in-out infinite; }
    .float-2 { animation: float 3s ease-in-out infinite 0.3s; }
    .float-3 { animation: float 3s ease-in-out infinite 0.6s; }
    .float-4 { animation: float 3s ease-in-out infinite 0.9s; }

    /* Sicbo selection styles */
    .sicbo-options {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin-top: 20px;
    }

    .sicbo-option {
      padding: 10px 20px;
      background: rgba(199, 21, 133, 0.7);
      border-radius: 10px;
      cursor: pointer;
      transition: all 0.3s;
      border: 1px solid rgba(255, 182, 193, 0.5);
      display: flex;
      align-items: center;
    }

    .sicbo-option:hover {
      background: rgba(219, 21, 153, 0.9);
      transform: translateY(-3px);
    }

    .sicbo-option img {
      width: 30px;
      height: 30px;
      margin-right: 10px;
      border-radius: 8px;
    }

    /* Floating elements */
    .floating-elements {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: -1;
    }

    .floating-circle {
      position: absolute;
      background: radial-gradient(circle, rgba(255,182,193,0.2) 0%, transparent 70%);
      border-radius: 50%;
      animation: float 15s infinite linear;
      opacity: 0.7;
    }

    @keyframes float {
      0% { transform: translateY(0) rotate(0deg); }
      50% { transform: translateY(-50px) rotate(180deg); }
      100% { transform: translateY(0) rotate(360deg); }
    }

    /* Responsive adjustments */
    @media (max-width: 768px) {
      .main-categories {
        width: 95%;
      }
      
      .main-category {
        padding: 15px;
      }
      
      .main-category img {
        width: 60px;
        height: 60px;
      }
      
      .main-category span {
        font-size: 18px;
      }
      
      .gameOption {
        width: 100%;
      }
      
      #robotContainer {
        left: 10px;
      }
      
      #robotText {
        font-size: 13px;
        max-width: 200px;
      }
      
      #robotIcon {
        width: 80px;
        height: 80px;
      }

      .floating-circle {
        display: none;
      }

      .wrapper {
        margin: 15px auto;
        padding: 15px;
        max-width: 90%;
      }

      .circle {
        width: 100px;
        height: 100px;
        font-size: 22px;
      }

      .history-table {
        font-size: 12px;
      }

      .history-table th, .history-table td {
        padding: 8px 5px;
      }
    }

    /* Scrollbar styles */
    ::-webkit-scrollbar {
      width: 8px;
    }

    ::-webkit-scrollbar-track {
      background: rgba(147, 39, 143, 0.5);
    }

    ::-webkit-scrollbar-thumb {
      background: rgba(255, 105, 180, 0.5);
      border-radius: 4px;
    }

    ::-webkit-scrollbar-thumb:hover {
      background: rgba(255, 105, 180, 0.7);
    }

    /* Tap highlight for mobile */
    .main-category, .gameOption, #backButton {
      -webkit-tap-highlight-color: transparent;
    }
  </style>
</head>
<body>
  <!-- Màn hình chọn game -->
  <div id="gameSelect">
    <h2>🎮 CHỌN LOẠI GAME</h2>
    
    <!-- Floating decorative elements -->
    <div class="floating-elements">
      <div class="floating-circle" style="top:20%; left:10%; width:100px; height:100px; animation-delay:0s;"></div>
      <div class="floating-circle" style="top:70%; left:80%; width:150px; height:150px; animation-delay:1s;"></div>
      <div class="floating-circle" style="top:40%; left:85%; width:80px; height:80px; animation-delay:2s;"></div>
    </div>
    
    <!-- 3 lựa chọn chính -->
    <div class="main-categories">
      <div class="main-category" id="regularCategory">
        <img src="https://i.postimg.cc/Jn4jGkLJ/images-1.jpg" alt="Tài Xỉu Thường">
        <span>TÀI XỈU THƯỜNG</span>
      </div>
      
      <div class="main-category" id="md5Category">
        <img src="https://i.postimg.cc/4NrvBy6k/images-2.jpg" alt="Tài Xỉu MD5">
        <span>TÀI XỈU MD5</span>
      </div>
      
      <div class="main-category" id="sicboCategory">
        <img src="https://i.postimg.cc/c1fJJKnC/images.jpg" alt="Sicbo">
        <span>SICBO</span>
      </div>
    </div>
    
    <!-- Sub-games (hidden by default) -->
    <div class="sub-games" id="regular-games">
      <div class="game-section-title">
        <img src="https://i.postimg.cc/Jn4jGkLJ/images-1.jpg" alt="Tài Xỉu Thường" style="width: 30px; height: 30px; vertical-align: middle; margin-right: 10px;">
        TÀI XỈU THƯỜNG
      </div>
      <div class="gameOptionsContainer">
        <div class="gameOption" id="sunOption">
          <img src="https://i.postimg.cc/y6wrZ8xx/IMG-7874.jpg" alt="SunWin">
          <span>SunWin</span>
        </div>
        <div class="gameOption" id="game789Option">
          <img src="https://raw.githubusercontent.com/csgopravo/csgopravo.github.io/main/789-logo.png" alt="789">
          <span>789 Club</span>
        </div>
      </div>
    </div>

    <div class="sub-games" id="md5-games">
      <div class="game-section-title">
        <img src="https://i.postimg.cc/4NrvBy6k/images-2.jpg" alt="Tài Xỉu MD5" style="width: 30px; height: 30px; vertical-align: middle; margin-right: 10px;">
        TÀI XỈU MD5
      </div>
      <div class="gameOptionsContainer">
        <div class="gameOption" id="hitclubOption">
          <img src="https://i.postimg.cc/L6LQBFgT/IMG-7875.jpg" alt="HitClub">
          <span>HitClub</span>
        </div>
        <div class="gameOption" id="b52Option">
          <img src="https://i.postimg.cc/ZKdxtPTK/IMG-7873.jpg" alt="B52">
          <span>B52</span>
        </div>
        <div class="gameOption" id="luckywinOption">
          <img src="https://i.postimg.cc/3xHPtTTR/t-i-xu-ng.jpg" alt="LuckyWin">
          <span>LuckyWin</span>
        </div>
        <div class="gameOption" id="sumclubOption">
          <img src="https://i.postimg.cc/HxLz6Snj/logosumclub2.webp" alt="Sumclub">
          <span>Sumclub</span>
        </div>
        <div class="gameOption" id="xd88Option">
          <img src="https://i.postimg.cc/wMCkTgVs/xocdia88.png" alt="XD88">
          <span>XD88</span>
        </div>
      </div>
    </div>

    <div class="sub-games" id="sicbo-games">
      <div class="game-section-title">
        <img src="https://i.postimg.cc/c1fJJKnC/images.jpg" alt="Sicbo" style="width: 30px; height: 30px; vertical-align: middle; margin-right: 10px;">
        GAME SICBO
      </div>
      <div class="gameOptionsContainer">
        <div class="gameOption" id="sicboSunOption">
          <img src="https://i.postimg.cc/y6wrZ8xx/IMG-7874.jpg" alt="Sun Sicbo">
          <span>Sun Sicbo</span>
        </div>
        <div class="gameOption" id="sicbo789Option">
          <img src="https://raw.githubusercontent.com/csgopravo/csgopravo.github.io/main/789-logo.png" alt="789 Sicbo">
          <span>789 Sicbo</span>
        </div>
      </div>
    </div>
  </div>

  <!-- Các iframe game -->
  <iframe id="sunFrame" src="https://web.sunwin.ag/?affId=Sunwin"></iframe>
  <iframe id="game789Frame" src="https://play.789.club"></iframe>
  <iframe id="sumclubFrame" src="https://play.sum34.club/?domain=sum34.club&packname=home"></iframe>
  <iframe id="xd88Frame" src="https://play.xocdia88.ai.in/"></iframe>
  <iframe id="luckywinFrame" src="https://fhe75d54.md5edu1.com/mobile/#/"></iframe>

  <!-- Nút quay lại -->
  <button id="backButton">← QUAY LẠI</button>

  <!-- Robot dự đoán -->
  <div id="robotContainer">
    <div id="robotInner">
      <img id="robotIcon" src="https://i.postimg.cc/rwkZQhxp/Robot.gif" alt="Robot Icon" />
      <div id="robotText">
        <div id="line1"><strong>Chờ phiên mới</strong></div>
        <div id="line2"></div>
      </div>
    </div>
  </div>

  <!-- Loading indicator -->
  <div id="loadingIndicator">Đang kết nối...</div>

  <!-- Game Interface (for HitClub and B52) -->
  <div id="gameInterface">
    <div id="particles-js"></div>
    <div class="wrapper">
      <h2 class="game-title">
        <span class="float-1">DỰ</span>
        <span class="float-2">ĐOÁN</span>
        <span class="float-3">TÀI</span>
        <span class="float-4">XỈU</span>
      </h2>
      <div class="status" id="phienText">#------</div>
      <div class="circle" id="prediction">--</div>
      <div class="status" id="extraInfo">--</div>
      <div class="status" id="status">ĐANG KẾT NỐI...</div>
      <div class="time" id="clock">--:--:--</div>
      <div class="stats" id="winStats">✔ Thắng: 0 | ✘ Thua: 0</div>

      <table class="history-table">
        <thead>
          <tr>
            <th>Phiên</th>
            <th>Dự đoán</th>
            <th>Kết quả</th>
            <th>Đánh giá</th>
            <th>Thời gian</th>
          </tr>
        </thead>
        <tbody id="historyBody">
        </tbody>
      </table>
    </div>
  </div>

  <audio id="soundWin" src="https://freesound.org/data/previews/341/341695_5260877-lq.mp3"></audio>
  <audio id="soundLose" src="https://freesound.org/data/previews/109/109662_945474-lq.mp3"></audio>

  <script>
    // DOM Elements
    const gameSelect = document.getElementById("gameSelect");
    const regularCategory = document.getElementById("regularCategory");
    const md5Category = document.getElementById("md5Category");
    const sicboCategory = document.getElementById("sicboCategory");
    const regularGames = document.getElementById("regular-games");
    const md5Games = document.getElementById("md5-games");
    const sicboGames = document.getElementById("sicbo-games");
    
    const sunOption = document.getElementById("sunOption");
    const hitclubOption = document.getElementById("hitclubOption");
    const b52Option = document.getElementById("b52Option");
    const game789Option = document.getElementById("game789Option");
    const sumclubOption = document.getElementById("sumclubOption");
    const xd88Option = document.getElementById("xd88Option");
    const luckywinOption = document.getElementById("luckywinOption");
    const sicboSunOption = document.getElementById("sicboSunOption");
    const sicbo789Option = document.getElementById("sicbo789Option");
    
    const sunFrame = document.getElementById("sunFrame");
    const game789Frame = document.getElementById("game789Frame");
    const sumclubFrame = document.getElementById("sumclubFrame");
    const xd88Frame = document.getElementById("xd88Frame");
    const luckywinFrame = document.getElementById("luckywinFrame");
    
    const backButton = document.getElementById("backButton");
    const robot = document.getElementById("robotContainer");
    const line1 = document.getElementById("line1");
    const line2 = document.getElementById("line2");
    const loadingIndicator = document.getElementById("loadingIndicator");
    const gameInterface = document.getElementById("gameInterface");
    const phienText = document.getElementById("phienText");
    const predictionCircle = document.getElementById("prediction");
    const extraInfo = document.getElementById("extraInfo");
    const statusText = document.getElementById("status");
    const clockText = document.getElementById("clock");
    const winStats = document.getElementById("winStats");
    const historyBody = document.getElementById("historyBody");
    const soundWin = document.getElementById("soundWin");
    const soundLose = document.getElementById("soundLose");

    let currentGame = null;
    let currentCategory = null;
    let fetchInterval = null;
    let isFetching = false;
    let currentProxyIndex = 0;
    let retryCount = 0;
    let winCount = 0;
    let loseCount = 0;
    let historyData = [];
    let lastProcessedSession = null;
    let lastResultData = null;
    let currentSessionData = null;
    let isAnalyzing = false;
    let analysisTimeout = null;
    let pendingResults = {};

    // API endpoints
    const SUNWIN_API = "https://apisunhpt.onrender.com/sunlon";
    const HITCLUB_API = "https://binhtool-hitpredict.onrender.com/api/taixiu";
    const B52_API = "https://binhtool90-b52.onrender.com/api/taixiu";
    const GAME789_API = "https://binhtool-789predict.onrender.com/taixiu";
    const SUMCLUB_API = "https://binhtool90-sumclub.onrender.com/api/taixiu/lucky";
    const XD88_API = "https://xd88-1233.onrender.com/api/taixiu";
    const LUCKYWIN_API = "https://binhtool-luckpredict.onrender.com/api/taixiu/lottery";
    const SICBO_SUN_API = "https://binhtool-sicsunpredict.onrender.com/predict";
    const SICBO_789_API = "https://binhtool-sic789prrdict.onrender.com/predict";

    // Xử lý sự kiện cho các category chính
    regularCategory.addEventListener("click", () => showSubGames("regular"));
    md5Category.addEventListener("click", () => showSubGames("md5"));
    sicboCategory.addEventListener("click", () => showSubGames("sicbo"));

    // Thêm sự kiện cảm ứng
    regularCategory.addEventListener("touchstart", (e) => {
      e.preventDefault();
      showSubGames("regular");
    }, { passive: false });
    
    md5Category.addEventListener("touchstart", (e) => {
      e.preventDefault();
      showSubGames("md5");
    }, { passive: false });
    
    sicboCategory.addEventListener("touchstart", (e) => {
      e.preventDefault();
      showSubGames("sicbo");
    }, { passive: false });

    // Xử lý sự kiện cho các game option
    sunOption.addEventListener("click", () => selectGame("sun"));
    hitclubOption.addEventListener("click", () => selectGame("hitclub"));
    b52Option.addEventListener("click", () => selectGame("b52"));
    game789Option.addEventListener("click", () => selectGame("game789"));
    sumclubOption.addEventListener("click", () => selectGame("sumclub"));
    xd88Option.addEventListener("click", () => selectGame("xd88"));
    luckywinOption.addEventListener("click", () => selectGame("luckywin"));
    sicboSunOption.addEventListener("click", () => selectGame("sicbo_sun"));
    sicbo789Option.addEventListener("click", () => selectGame("sicbo_789"));
    
    // Thêm sự kiện cảm ứng cho các game option
    sunOption.addEventListener("touchstart", (e) => {
      e.preventDefault();
      selectGame("sun");
    }, { passive: false });
    
    hitclubOption.addEventListener("touchstart", (e) => {
      e.preventDefault();
      selectGame("hitclub");
    }, { passive: false });
    
    b52Option.addEventListener("touchstart", (e) => {
      e.preventDefault();
      selectGame("b52");
    }, { passive: false });
    
    game789Option.addEventListener("touchstart", (e) => {
      e.preventDefault();
      selectGame("game789");
    }, { passive: false });
    
    sumclubOption.addEventListener("touchstart", (e) => {
      e.preventDefault();
      selectGame("sumclub");
    }, { passive: false });
    
    xd88Option.addEventListener("touchstart", (e) => {
      e.preventDefault();
      selectGame("xd88");
    }, { passive: false });
    
    luckywinOption.addEventListener("touchstart", (e) => {
      e.preventDefault();
      selectGame("luckywin");
    }, { passive: false });
    
    sicboSunOption.addEventListener("touchstart", (e) => {
      e.preventDefault();
      selectGame("sicbo_sun");
    }, { passive: false });
    
    sicbo789Option.addEventListener("touchstart", (e) => {
      e.preventDefault();
      selectGame("sicbo_789");
    }, { passive: false });
    
    backButton.addEventListener("click", deselectGame);
    backButton.addEventListener("touchstart", (e) => {
      e.preventDefault();
      deselectGame();
    }, { passive: false });

    function showSubGames(category) {
      // Ẩn tất cả sub-games
      regularGames.classList.remove("active");
      md5Games.classList.remove("active");
      sicboGames.classList.remove("active");
      
      // Hiển thị sub-game tương ứng
      if (category === "regular") {
        regularGames.classList.add("active");
        currentCategory = "regular";
      } else if (category === "md5") {
        md5Games.classList.add("active");
        currentCategory = "md5";
      } else if (category === "sicbo") {
        sicboGames.classList.add("active");
        currentCategory = "sicbo";
      }
      
      // Hiển thị nút back
      backButton.style.display = "block";
      backButton.textContent = "← QUAY LẠI DANH MỤC";
      
      // Cuộn xuống phần sub-games
      document.querySelector(".sub-games.active").scrollIntoView({ behavior: "smooth" });
    }

    function selectGame(game) {
      currentGame = game;
      gameSelect.style.display = "none";
      backButton.style.display = "block";
      backButton.textContent = "← QUAY LẠI";
      
      // Ẩn tất cả các giao diện game trước khi hiển thị cái mới
      sunFrame.style.display = "none";
      game789Frame.style.display = "none";
      sumclubFrame.style.display = "none";
      xd88Frame.style.display = "none";
      luckywinFrame.style.display = "none";
      gameInterface.style.display = "none";
      robot.style.display = "none";
      
      // Hiển thị loading
      loadingIndicator.style.display = "block";
      loadingIndicator.innerHTML = `
        <div style="display:flex; flex-direction:column; align-items:center;">
          <div style="width:50px; height:50px; border:3px solid rgba(255,255,255,0.3); border-radius:50%; border-top-color:#fff; animation:spin 1s linear infinite; margin-bottom:15px;"></div>
          <span style="font-size:18px;">Đang tải ${game.toUpperCase()}...</span>
        </div>
      `;
      
      // Reset stats
      winCount = 0;
      loseCount = 0;
      historyData = [];
      lastProcessedSession = null;
      lastResultData = null;
      pendingResults = {};
      updateStats();
      historyBody.innerHTML = "";

      // Ẩn loading sau 1.5s và hiển thị game
      setTimeout(() => {
        loadingIndicator.style.display = "none";
        
        if (game === "sun") {
          sunFrame.style.display = "block";
          robot.style.display = "flex";
          startFetching(SUNWIN_API, processSunData);
        } else if (game === "game789") {
          game789Frame.style.display = "block";
          robot.style.display = "flex";
          startFetching(GAME789_API, process789Data);
        } else if (game === "sumclub") {
          sumclubFrame.style.display = "block";
          robot.style.display = "flex";
          startFetching(SUMCLUB_API, processSumclubData);
        } else if (game === "xd88") {
          xd88Frame.style.display = "block";
          robot.style.display = "flex";
          startFetching(XD88_API, processXd88Data);
        } else if (game === "luckywin") {
          luckywinFrame.style.display = "block";
          robot.style.display = "flex";
          startFetching(LUCKYWIN_API, processLuckywinData);
        } else if (game === "sicbo_sun") {
          sunFrame.style.display = "block";
          robot.style.display = "flex";
          startFetching(SICBO_SUN_API, processSicboData);
        } else if (game === "sicbo_789") {
          game789Frame.style.display = "block";
          robot.style.display = "flex";
          startFetching(SICBO_789_API, processSicboData);
        } else if (game === "hitclub" || game === "b52") {
          gameInterface.style.display = "block";
          const gameTitle = document.querySelector(".game-title");
          if (gameTitle) {
            gameTitle.innerHTML = game === "hitclub" ? 
              '<span class="float-1">DỰ</span> <span class="float-2">ĐOÁN</span> <span class="float-3">HITCLUB</span>' :
              '<span class="float-1">DỰ</span> <span class="float-2">ĐOÁN</span> <span class="float-3">B52</span>';
          }
          
          // Initialize particles
          particlesJS("particles-js", {
            particles: {
              number: { 
                value: 120,
                density: {
                  enable: true,
                  value_area: 800
                }
              },
              color: { 
                value: ["#ffb6c1", "#ff69b4", "#db7093", "#ffffff"] 
              },
              shape: { 
                type: "circle",
                stroke: {
                  width: 0,
                  color: "#000000"
                }
              },
              opacity: {
                value: 0.7,
                random: true,
                anim: {
                  enable: true,
                  speed: 1,
                  opacity_min: 0.1,
                  sync: false
                }
              },
              size: {
                value: 3,
                random: true,
                anim: {
                  enable: true,
                  speed: 2,
                  size_min: 0.1,
                  sync: false
                }
              },
              line_linked: {
                enable: true,
                distance: 150,
                color: "#ff69b4",
                opacity: 0.3,
                width: 1
              },
              move: {
                enable: true,
                speed: 1,
                direction: "none",
                random: true,
                straight: false,
                out_mode: "out",
                bounce: false,
                attract: {
                  enable: true,
                  rotateX: 600,
                  rotateY: 1200
                }
              }
            },
            interactivity: {
              detect_on: "canvas",
              events: {
                onhover: {
                  enable: true,
                  mode: "bubble"
                },
                onclick: {
                  enable: true,
                  mode: "push"
                },
                resize: true
              },
              modes: {
                bubble: {
                  distance: 200,
                  size: 6,
                  duration: 2,
                  opacity: 0.8,
                  speed: 3
                },
                push: {
                  particles_nb: 4
                }
              }
            },
            retina_detect: true
          });
          
          // Start fetching data
          const apiUrl = game === "hitclub" ? HITCLUB_API : B52_API;
          startFetching(apiUrl, game === "hitclub" ? processHitClubData : processB52Data);
        }
      }, 1500);
    }

    function deselectGame() {
      if (currentGame) {
        // Nếu đang ở màn hình game, quay lại danh sách game
        currentGame = null;
        
        // Ẩn tất cả iframe và giao diện game
        sunFrame.style.display = "none";
        game789Frame.style.display = "none";
        sumclubFrame.style.display = "none";
        xd88Frame.style.display = "none";
        luckywinFrame.style.display = "none";
        gameInterface.style.display = "none";
        robot.style.display = "none";
        
        // Hiển thị lại màn hình chọn game
        gameSelect.style.display = "flex";
        backButton.textContent = "← QUAY LẠI DANH MỤC";
        
        // Dừng các interval
        if (fetchInterval) {
          clearInterval(fetchInterval);
          fetchInterval = null;
        }
        
        // Dừng âm thanh
        soundWin.pause();
        soundWin.currentTime = 0;
        soundLose.pause();
        soundLose.currentTime = 0;

        // Dừng âm thanh từ iframe
        [sunFrame, game789Frame, sumclubFrame, xd88Frame, luckywinFrame].forEach(frame => {
          if (frame.contentWindow) {
            try {
              frame.contentWindow.postMessage({type: 'pause-audio'}, '*');
            } catch (e) {
              console.log("Cannot control iframe audio");
            }
          }
        });

        // Reload iframe để dừng hoàn toàn âm thanh
        [sunFrame, game789Frame, sumclubFrame, xd88Frame, luckywinFrame].forEach(frame => {
          if (frame.src) {
            const currentSrc = frame.src;
            frame.src = 'about:blank';
            setTimeout(() => {
              frame.src = currentSrc;
            }, 100);
          }
        });

        // Clear analysis timeout
        if (analysisTimeout) {
          clearTimeout(analysisTimeout);
          analysisTimeout = null;
        }

        // Reset tất cả trạng thái
        retryCount = 0;
        currentSessionData = null;
        isAnalyzing = false;
        lastProcessedSession = null;
        lastResultData = null;
        pendingResults = {};

        resetDisplay();
      } else if (currentCategory) {
        // Nếu đang ở danh sách game con, quay lại danh mục chính
        currentCategory = null;
        regularGames.classList.remove("active");
        md5Games.classList.remove("active");
        sicboGames.classList.remove("active");
        backButton.style.display = "none";
      }
    }

    function resetDisplay() {
      line1.innerHTML = "<strong>Chờ phiên mới</strong>";
      line2.textContent = "";

      // Reset game interface
      phienText.textContent = "#------";
      predictionCircle.textContent = "--";
      extraInfo.textContent = "--";
      statusText.textContent = "⏳ Sẵn sàng...";
      clockText.textContent = "--:--:--";
      historyBody.innerHTML = "";

      // Reset error states
      retryCount = 0;
    }

    // Helper functions for game interface
    function playSound(win) {
      const audio = win ? soundWin : soundLose;
      audio.currentTime = 0;
      audio.play().catch(e => console.log("Audio play failed:", e));
    }

    function updateStats() {
      winStats.textContent = `✔ Thắng: ${winCount} | ✘ Thua: ${loseCount}`;
    }

    function formatTime() {
      const now = new Date();
      return now.toLocaleTimeString("vi-VN", {
        hour: '2-digit',
        minute: '2-digit',
        second: '2-digit'
      });
    }

    function addHistoryRow(phien, prediction, result, time, isNewResult = false) {
      // Check if this row already exists
      const existingRow = Array.from(historyBody.rows).find(row => 
        row.cells[0].textContent === phien.toString()
      );
      
      const row = document.createElement("tr");
      let evaluation = "<span class='pending'>Chờ kết quả</span>";
      
      const predHTML = prediction === "Tài" 
        ? `<span class="tai-cell">${prediction}</span>` 
        : `<span class="xiu-cell">${prediction}</span>`;
      
      let resultHTML = "<span class='pending'>Chưa có</span>";
      
      if (result && result !== "Chưa có" && (result.includes("=") || result.includes("Tài") || result.includes("Xỉu"))) {
        resultHTML = result.includes("Tài") 
          ? `<span class="tai-cell">${result}</span>` 
          : `<span class="xiu-cell">${result}</span>`;
        
        const win = (prediction === "Tài" && result.includes("Tài")) || 
                   (prediction === "Xỉu" && result.includes("Xỉu"));
        
        evaluation = win ? "<span class='win'>✔ Thắng</span>" : "<span class='lose'>✘ Thua</span>";
        
        if (isNewResult) {
          win ? winCount++ : loseCount++;
          updateStats();
          playSound(win);
        }
      }
      
      row.innerHTML = `
        <td>${phien}</td>
        <td>${predHTML}</td>
        <td>${resultHTML}</td>
        <td>${evaluation}</td>
        <td>${time}</td>
      `;
      
      if (existingRow) {
        historyBody.replaceChild(row, existingRow);
      } else {
        historyBody.insertBefore(row, historyBody.firstChild);
        if (historyBody.rows.length > 10) historyBody.removeChild(historyBody.lastChild);
      }
    }

    // Data processing functions
    function processSumclubData(data) {
      try {
        if (!data || !data.Phien) {
          console.log("Invalid Sumclub data structure:", data);
          return;
        }

        const currentSession = data.Phien;
        const prediction = data.Du_doan;
        const lastResult = data.Ket_qua || null;
        const time = formatTime();

        console.log("Sumclub data:", { currentSession, prediction, lastResult });

        // Kiểm tra và xử lý kết quả phiên trước
        if (lastResult && (lastResult.includes("Tài") || lastResult.includes("Xỉu"))) {
          const prevSession = data.Phien - 1;
          
          if (pendingResults[prevSession]) {
            const prevPrediction = pendingResults[prevSession];
            updateHistoryWithResult(prevSession, prevPrediction, lastResult, time);
            delete pendingResults[prevSession];
          }
        }

        // Chỉ cập nhật nếu là phiên mới và không đang phân tích
        if (currentSession !== lastProcessedSession && !isAnalyzing) {
          lastProcessedSession = currentSession;
          currentSessionData = {
            session: currentSession,
            prediction: prediction
          };
          
          pendingResults[currentSession] = prediction;
          
          // Update robot interface
          line1.innerHTML = `<strong>Phiên: #${currentSession}</strong>`;
          line2.innerHTML = `Dự đoán: <span class="${prediction === 'Tài' ? 'tai' : 'xiu'}">${prediction}</span>`;
        }

      } catch (e) {
        console.error("Sumclub data error:", e);
      }
    }

    function processXd88Data(data) {
      try {
        if (!data || !data.Phien) {
          console.log("Invalid XD88 data structure:", data);
          return;
        }

        const currentSession = data.Phien;
        const prediction = data.Du_doan;
        const lastResult = data.Ket_qua || null;
        const time = formatTime();

        console.log("XD88 data:", { currentSession, prediction, lastResult });

        // Kiểm tra và xử lý kết quả phiên trước
        if (lastResult && (lastResult.includes("Tài") || lastResult.includes("Xỉu"))) {
          const prevSession = data.Phien - 1;
          
          if (pendingResults[prevSession]) {
            const prevPrediction = pendingResults[prevSession];
            updateHistoryWithResult(prevSession, prevPrediction, lastResult, time);
            delete pendingResults[prevSession];
          }
        }

        // Chỉ cập nhật nếu là phiên mới và không đang phân tích
        if (currentSession !== lastProcessedSession && !isAnalyzing) {
          lastProcessedSession = currentSession;
          currentSessionData = {
            session: currentSession,
            prediction: prediction
          };
          
          pendingResults[currentSession] = prediction;
          
          // Update robot interface
          line1.innerHTML = `<strong>Phiên: #${currentSession}</strong>`;
          line2.innerHTML = `Dự đoán: <span class="${prediction === 'Tài' ? 'tai' : 'xiu'}">${prediction}</span>`;
        }

      } catch (e) {
        console.error("XD88 data error:", e);
      }
    }

    function processLuckywinData(data) {
      try {
        if (!data || !data.Phien) {
          console.log("Invalid LuckyWin data structure:", data);
          return;
        }

        const currentSession = data.Phien;
        const prediction = data.Du_doan;
        const lastResult = data.Ket_qua || null;
        const time = formatTime();

        console.log("LuckyWin data:", { currentSession, prediction, lastResult });

        // Kiểm tra và xử lý kết quả phiên trước
        if (lastResult && (lastResult.includes("Tài") || lastResult.includes("Xỉu"))) {
          const prevSession = data.Phien - 1;
          
          if (pendingResults[prevSession]) {
            const prevPrediction = pendingResults[prevSession];
            updateHistoryWithResult(prevSession, prevPrediction, lastResult, time);
            delete pendingResults[prevSession];
          }
        }

        // Chỉ cập nhật nếu là phiên mới và không đang phân tích
        if (currentSession !== lastProcessedSession && !isAnalyzing) {
          lastProcessedSession = currentSession;
          currentSessionData = {
            session: currentSession,
            prediction: prediction
          };
          
          pendingResults[currentSession] = prediction;
          
          // Update robot interface
          line1.innerHTML = `<strong>Phiên: #${currentSession}</strong>`;
          line2.innerHTML = `Dự đoán: <span class="${prediction === 'Tài' ? 'tai' : 'xiu'}">${prediction}</span>`;
        }

      } catch (e) {
        console.error("LuckyWin data error:", e);
      }
    }

    function processSicboData(data) {
      try {
        if (!data || !data.Phien) {
          console.log("Invalid Sicbo data structure:", data);
          return;
        }

        const currentSession = data.Phien;
        const prediction = data.Du_doan;
        const lastResult = data.Ket_qua || null;
        const time = formatTime();
        const dicePositions = data.doan_vi ? data.doan_vi.join(", ") : "Không có";

        console.log("Sicbo data:", { currentSession, prediction, lastResult, dicePositions });

        // Kiểm tra và xử lý kết quả phiên trước
        if (lastResult && (lastResult.includes("Tài") || lastResult.includes("Xỉu"))) {
          const prevSession = data.Phien - 1;
          
          if (pendingResults[prevSession]) {
            const prevPrediction = pendingResults[prevSession];
            updateHistoryWithResult(prevSession, prevPrediction, lastResult, time);
            delete pendingResults[prevSession];
          }
        }

        // Chỉ cập nhật nếu là phiên mới và không đang phân tích
        if (currentSession !== lastProcessedSession && !isAnalyzing) {
          lastProcessedSession = currentSession;
          currentSessionData = {
            session: currentSession,
            prediction: prediction
          };
          
          pendingResults[currentSession] = prediction;
          
          // Update robot interface with Sicbo info
          line1.innerHTML = `<strong>Phiên Sicbo: #${currentSession}</strong>`;
          line2.innerHTML = `Dự đoán: <span class="${prediction === 'Tài' ? 'tai' : 'xiu'}">${prediction}</span><br>
                            Đoán vị: ${dicePositions}`;
        }

      } catch (e) {
        console.error("Sicbo data error:", e);
      }
    }

    function processSunData(data) {
      try {
        const session = data.phien || "N/A";
        const prediction = data.du_doan || "Chưa có";
        const result = data.ket_qua || null;
        
        if (result && currentSessionData && currentSessionData.session < session) {
          showResult(currentSessionData.prediction, result);
          return;
        }
        
        if (!currentSessionData || currentSessionData.session !== session) {
          if (isAnalyzing) return;
          
          currentSessionData = {
            session: session,
            prediction: prediction
          };
          
          const predictionClass = prediction === 'Tài' ? 'tai' : 'xiu';
          line1.innerHTML = `<strong>Phiên: #${session + 1}</strong>`;
          line2.innerHTML = `Dự đoán: <span class="${predictionClass}">${prediction}</span>`;
        }
      } catch (e) {
        console.error("SunWin data error:", e);
        showApiError("Lỗi dữ liệu SunWin");
      }
    }

    function process789Data(data) {
      try {
        if (!data || !data.Phien) {
          console.log("Invalid 789 data structure:", data);
          return;
        }

        const currentSession = data.Phien;
        const prediction = data.Du_doan;
        const lastResult = data.Ket_qua || null;
        const time = formatTime();

        console.log("789 data:", { currentSession, prediction, lastResult });

        if (lastResult && (lastResult.includes("Tài") || lastResult.includes("Xỉu"))) {
          const prevSession = data.Phien - 1;
          
          if (pendingResults[prevSession]) {
            const prevPrediction = pendingResults[prevSession];
            updateHistoryWithResult(prevSession, prevPrediction, lastResult, time);
            delete pendingResults[prevSession];
          }
        }

        if (currentSession !== lastProcessedSession && !isAnalyzing) {
          lastProcessedSession = currentSession;
          currentSessionData = {
            session: currentSession,
            prediction: prediction
          };
          
          pendingResults[currentSession] = prediction;
          
          line1.innerHTML = `<strong>Phiên: #${currentSession}</strong>`;
          line2.innerHTML = `Dự đoán: <span class="${prediction === 'Tài' ? 'tai' : 'xiu'}">${prediction}</span>`;
        }

      } catch (e) {
        console.error("789 data error:", e);
      }
    }

    function processHitClubData(data) {
      try {
        if (!data || !data.Phien) {
          console.log("Invalid HitClub data structure:", data);
          return;
        }

        const currentSession = data.Phien;
        const prediction = data.Du_doan;
        const lastResult = data.Ket_qua || null;
        const time = formatTime();

        console.log("HitClub data:", { currentSession, prediction, lastResult });

        if (lastResult && (lastResult.includes("Tài") || lastResult.includes("Xỉu"))) {
          const prevSession = data.Phien - 1;
          
          if (pendingResults[prevSession]) {
            const prevPrediction = pendingResults[prevSession];
            updateHistoryWithResult(prevSession, prevPrediction, lastResult, time);
            delete pendingResults[prevSession];
          }
        }

        if (currentSession !== lastProcessedSession && !isAnalyzing) {
          lastProcessedSession = currentSession;
          currentSessionData = {
            session: currentSession,
            prediction: prediction
          };
          
          pendingResults[currentSession] = prediction;
          
          if (phienText) phienText.textContent = `#${currentSession}`;
          if (predictionCircle) {
            predictionCircle.innerHTML = prediction === "Tài" 
              ? `<span style="color:#98fb98; text-shadow: 0 0 15px #98fb98;">TÀI</span>` 
              : `<span style="color:#ff6b6b; text-shadow: 0 0 15px #ff6b6b;">XỈU</span>`;
          }
          if (extraInfo) {
            extraInfo.innerHTML = `📈 Thời gian: <strong>${time || 'N/A'}</strong>`;
          }
          if (statusText) {
            statusText.innerHTML = '<span style="color:#98fb98">●</span> HITCLUB ĐÃ KẾT NỐI';
          }
          if (clockText) clockText.textContent = time;

          addHistoryRow(currentSession, prediction, "Chưa có", time);
        }

      } catch (e) {
        console.error("HitClub data error:", e);
      }
    }

    function processB52Data(data) {
      try {
        if (!data || !data.Phien) {
          console.log("Invalid B52 data structure:", data);
          return;
        }

        const currentSession = data.Phien + 1; // Next session
        const prediction = data.Du_doan;
        const lastResult = data.Ket_qua || null;
        const time = formatTime();

        console.log("B52 data:", { currentSession, prediction, lastResult });

        if (lastResult && (lastResult.includes("Tài") || lastResult.includes("Xỉu"))) {
          const currentSessionWithResult = data.Phien;
          
          if (pendingResults[currentSessionWithResult]) {
            const prevPrediction = pendingResults[currentSessionWithResult];
            updateHistoryWithResult(currentSessionWithResult, prevPrediction, lastResult, time);
            delete pendingResults[currentSessionWithResult];
          }
        }

        if (currentSession !== lastProcessedSession && !isAnalyzing) {
          lastProcessedSession = currentSession;
          currentSessionData = {
            session: currentSession,
            prediction: prediction
          };
          
          pendingResults[currentSession] = prediction;
          
          if (phienText) phienText.textContent = `#${currentSession}`;
          if (predictionCircle) {
            predictionCircle.innerHTML = prediction === "Tài" 
              ? `<span style="color:#98fb98; text-shadow: 0 0 15px #98fb98;">TÀI</span>` 
              : `<span style="color:#ff6b6b; text-shadow: 0 0 15px #ff6b6b;">XỈU</span>`;
          }
          if (extraInfo) {
            extraInfo.innerHTML = `📊 Phiên Trước: <strong>#${data.Phien}</strong>`;
          }
          if (statusText) {
            statusText.innerHTML = '<span style="color:#98fb98">●</span> B52 ĐÃ KẾT NỐI';
          }
          if (clockText) clockText.textContent = time;

          addHistoryRow(currentSession, prediction, "Chưa có", time);
        }

      } catch (e) {
        console.error("B52 data error:", e);
      }
    }

    function updateHistoryWithResult(session, prediction, result, time) {
      const existingRow = Array.from(historyBody.rows).find(row => 
        row.cells[0].textContent === session.toString()
      );
      
      if (existingRow) {
        const win = (prediction === "Tài" && result.includes("Tài")) || 
                   (prediction === "Xỉu" && result.includes("Xỉu"));
        
        const resultHTML = result.includes("Tài") 
          ? `<span class="tai-cell">${result}</span>` 
          : `<span class="xiu-cell">${result}</span>`;
        
        const evaluation = win ? "<span class='win'>✔ Thắng</span>" : "<span class='lose'>✘ Thua</span>";
        
        existingRow.cells[2].innerHTML = resultHTML;
        existingRow.cells[3].innerHTML = evaluation;
        
        win ? winCount++ : loseCount++;
        updateStats();
        playSound(win);
      }
    }

    function showResult(prediction, actualResult) {
      if (isAnalyzing) return;
      
      const isWin = (prediction === "Tài" && actualResult.includes("Tài")) || 
                   (prediction === "Xỉu" && actualResult.includes("Xỉu"));
      
      if (currentGame === "sun" || currentGame === "game789" || 
          currentGame === "sumclub" || currentGame === "xd88" || 
          currentGame === "luckywin" || currentGame.includes("sicbo")) {
        line1.innerHTML = `<strong>Kết quả: ${actualResult}</strong>`;
        line2.innerHTML = isWin ? 
          `<span style="color: #98fb98; font-weight: bold;">🎉 CHIẾN THẮNG!</span>` :
          `<span style="color: #ff6b6b; font-weight: bold;">🙁 THUA CUỘC!</span>`;
      } else {
        predictionCircle.innerHTML = isWin ? 
          `<span style="color:#98fb98; text-shadow: 0 0 15px #98fb98;">THẮNG</span>` :
          `<span style="color:#ff6b6b; text-shadow: 0 0 15px #ff6b6b;">THUA</span>`;
        statusText.innerHTML = `<span style="color:${isWin ? '#98fb98' : '#ff6b6b'}">● ${isWin ? 'CHIẾN THẮNG' : 'THUA CUỘC'}</span>`;
      }
      
      playSound(isWin);
      
      setTimeout(() => {
        showAnalyzing();
      }, 5000);
    }
    
    function showAnalyzing() {
      isAnalyzing = true;
      
      if (currentGame === "sun" || currentGame === "game789" || 
          currentGame === "sumclub" || currentGame === "xd88" || 
          currentGame === "luckywin" || currentGame.includes("sicbo")) {
        line1.innerHTML = `<strong>🔍 Đang phân tích...</strong>`;
        line2.innerHTML = `<span style="color: #ffd700;">Vui lòng chờ dự đoán mới</span>`;
      } else {
        predictionCircle.innerHTML = `<span style="color:#ffd700; text-shadow: 0 0 15px #ffd700;">...</span>`;
        statusText.innerHTML = `<span style="color:#ffd700">🔍 ĐANG PHÂN TÍCH</span>`;
      }
      
      analysisTimeout = setTimeout(() => {
        isAnalyzing = false;
        currentSessionData = null;
      }, 5000);
    }

    function showApiError(message = "Lỗi kết nối API") {
      console.log("API connection issue:", message);
    }

    // Enhanced connection with multiple fallback APIs and immediate retry
    const B52_BACKUP_APIS = [
      "https://binhtool90-b52.onrender.com/api/taixiu",
      "https://api.codetabs.com/v1/proxy/?quest=https://binhtool90-b52.onrender.com/api/taixiu",
      "https://cors-anywhere.herokuapp.com/https://binhtool90-b52.onrender.com/api/taixiu"
    ];

    const GAME789_BACKUP_APIS = [
      "https://binhtool-789.onrender.com/taixiu",
      "https://api.codetabs.com/v1/proxy/?quest=https://binhtool-789.onrender.com/taixiu",
      "https://cors-anywhere.herokuapp.com/https://binhtool-789.onrender.com/taixiu"
    ];

    let currentB52ApiIndex = 0;
    let current789ApiIndex = 0;
    let fetchAttempts = 0;
    let connectionPrimary = null;
    let connectionBackup = null;

    // Primary proxy for all requests
    const PRIMARY_PROXY = "https://api.codetabs.com/v1/proxy/?quest=";

    // Enhanced fetch with multiple strategies  
    async function fetchDataEnhanced(url, processor, isBackup = false) {
      // Strategy 1: Try CORS proxy first (most reliable)
      const success = await fetchWithProxy(url, processor, isBackup);
      if (success) return true;

      // Strategy 2: Try direct fetch if proxy fails
      return await fetchDirect(url, processor, isBackup);
    }

    // Direct fetch attempt
    async function fetchDirect(url, processor, isBackup = false) {
      const controller = new AbortController();
      const timeoutId = setTimeout(() => controller.abort(), 5000);
      
      try {
        const response = await fetch(url, {
          method: 'GET',
          headers: {
            'Accept': 'application/json',
            'Cache-Control': 'no-cache',
            'Origin': window.location.origin
          },
          signal: controller.signal,
          mode: 'cors'
        });

        clearTimeout(timeoutId);

        if (!response.ok) throw new Error(`HTTP ${response.status}`);

        const data = await response.json();
        processor(data);
        retryCount = 0;
        fetchAttempts = 0;
        return true;

      } catch (error) {
        clearTimeout(timeoutId);
        console.log(`Direct fetch failed: ${error.message}`);
        return false;
      }
    }

    // Simplified proxy fetch
    async function fetchWithProxy(originalUrl, processor, isBackup = false) {
      const proxyUrl = PRIMARY_PROXY + encodeURIComponent(originalUrl);
      
      try {
        console.log(`Fetching ${originalUrl} via proxy...`);
        
        const response = await fetch(proxyUrl, {
          method: 'GET',
          headers: {
            'Accept': 'application/json'
          }
        });

        if (!response.ok) {
          throw new Error(`Proxy error: ${response.status}`);
        }

        const data = await response.json();
        console.log(`✓ Data received successfully:`, data);
        
        processor(data);
        retryCount = 0;
        fetchAttempts = 0;
        return true;

      } catch (error) {
        console.error(`✗ Proxy failed:`, error.message);
        return false;
      }
    }

    // Main connection function with proper error handling
    async function fetchWithParallelConnections(processor) {
      if (isFetching) return;
      isFetching = true;

      try {
        let primaryUrl;
        let backupApis;
        
        if (currentGame === 'b52') {
          primaryUrl = B52_API;
          backupApis = B52_BACKUP_APIS;
        } else if (currentGame === 'game789') {
          primaryUrl = GAME789_API;
          backupApis = GAME789_BACKUP_APIS;
        } else if (currentGame === 'hitclub') {
          primaryUrl = HITCLUB_API;
        } else if (currentGame === 'sumclub') {
          primaryUrl = SUMCLUB_API;
        } else if (currentGame === 'xd88') {
          primaryUrl = XD88_API;
        } else if (currentGame === 'luckywin') {
          primaryUrl = LUCKYWIN_API;
        } else if (currentGame === 'sicbo_sun') {
          primaryUrl = SICBO_SUN_API;
        } else if (currentGame === 'sicbo_789') {
          primaryUrl = SICBO_789_API;
        } else {
          primaryUrl = SUNWIN_API;
        }
        
        console.log(`=== Connecting to ${currentGame.toUpperCase()} ===`);
        
        const success = await fetchDataEnhanced(primaryUrl, processor, false);
        
        if (success) {
          console.log(`✓ ${currentGame.toUpperCase()} connected successfully`);
          if (statusText && !['sun', 'game789', 'sumclub', 'xd88', 'luckywin', 'sicbo_sun', 'sicbo_789'].includes(currentGame)) {
            statusText.innerHTML = '<span style="color:#98fb98">●</span> KẾT NỐI THÀNH CÔNG';
          }
        } else {
          console.log(`✗ ${currentGame.toUpperCase()} connection failed`);
          
          // Try backup APIs if available
          if (backupApis && backupApis.length > 0) {
            let backupSuccess = false;
            for (let i = 0; i < backupApis.length; i++) {
              backupSuccess = await fetchDataEnhanced(backupApis[i], processor, true);
              if (backupSuccess) break;
            }
            
            if (!backupSuccess) {
              console.log(`All backup APIs failed for ${currentGame}`);
              if (statusText && !['sun', 'game789', 'sumclub', 'xd88', 'luckywin', 'sicbo_sun', 'sicbo_789'].includes(currentGame)) {
                statusText.innerHTML = '<span style="color:#ff6b6b">●</span> KẾT NỐI THẤT BẠI - THỬ LẠI...';
              }
            }
          }
        }

      } catch (error) {
        console.error("Connection error:", error.message);
        if (statusText && !['sun', 'game789', 'sumclub', 'xd88', 'luckywin', 'sicbo_sun', 'sicbo_789'].includes(currentGame)) {
          statusText.innerHTML = '<span style="color:#ff6b6b">●</span> LỖI KẾT NỐI';
        }
      } finally {
        isFetching = false;
      }
    }

    function startFetching(url, processor) {
      console.log(`Starting fetching for ${currentGame}`);
      
      // Clear any existing intervals
      if (fetchInterval) clearInterval(fetchInterval);
      if (connectionBackup) clearInterval(connectionBackup);
      
      // Initial immediate fetch
      fetchWithParallelConnections(processor).catch(error => {
        console.error("Initial fetch error:", error);
      });
      
      // Set up regular interval
      const interval = currentGame === 'b52' ? 3000 : 5000; // 3s for B52, 5s for others
      
      fetchInterval = setInterval(() => {
        fetchWithParallelConnections(processor).catch(error => {
          console.error("Interval fetch error:", error);
        });
      }, interval);
    }

    // Connection maintenance - simplified
    function maintainConnection() {
      if (currentGame && !isFetching) {
        console.log(`Maintaining connection for ${currentGame}`);
      }
    }

    // Start connection maintenance
    setInterval(maintainConnection, 10000);

    // Update clock every second
    setInterval(() => {
      if (gameInterface.style.display === "block") {
        clockText.textContent = formatTime();
      }
    }, 1000);

    // Drag and drop for robot
    let isDragging = false;
    let offsetX = 0;
    let offsetY = 0;

    robot.addEventListener("mousedown", (e) => {
      isDragging = true;
      offsetX = e.clientX - robot.offsetLeft;
      offsetY = e.clientY - robot.offsetTop;
    });

    document.addEventListener("mousemove", (e) => {
      if (isDragging) {
        robot.style.left = e.clientX - offsetX + "px";
        robot.style.top = e.clientY - offsetY + "px";
      }
    });

    document.addEventListener("mouseup", () => {
      isDragging = false;
    });

    // Thêm xử lý cảm ứng
    robot.addEventListener("touchstart", (e) => {
      isDragging = true;
      const touch = e.touches[0];
      offsetX = touch.clientX - robot.offsetLeft;
      offsetY = touch.clientY - robot.offsetTop;
      e.preventDefault();
    }, { passive: false });

    document.addEventListener("touchmove", (e) => {
      if (isDragging) {
        const touch = e.touches[0];
        robot.style.left = touch.clientX - offsetX + "px";
        robot.style.top = touch.clientY - offsetY + "px";
        e.preventDefault();
      }
    }, { passive: false });

    document.addEventListener("touchend", () => {
      isDragging = false;
    });

    // Auto-hide back button
    let hideTimeout;
    document.addEventListener("mousemove", () => {
      backButton.style.opacity = "1";
      clearTimeout(hideTimeout);
      hideTimeout = setTimeout(() => {
        backButton.style.opacity = "0.7";
      }, 2000);
    });

    // Thêm xử lý cho cảm ứng
    document.addEventListener("touchstart", () => {
      backButton.style.opacity = "1";
      clearTimeout(hideTimeout);
      hideTimeout = setTimeout(() => {
        backButton.style.opacity = "0.7";
      }, 2000);
    });

    // Prevent zoom on double-tap
    document.addEventListener('dblclick', function(e) {
      e.preventDefault();
    }, { passive: false });

    document.addEventListener('touchstart', function(e) {
      if (e.touches.length > 1) {
        e.preventDefault();
      }
    }, { passive: false });

    // Prevent pull-to-refresh on mobile
    document.addEventListener('touchmove', function(e) {
      if (e.touches.length > 1 || e.scale && e.scale !== 1) {
        e.preventDefault();
      }
    }, { passive: false });

    // Disable context menu on long press
    document.addEventListener('contextmenu', function(e) {
      e.preventDefault();
    }, false);
  </script>
</body>
</html>
