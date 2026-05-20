<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>세모를 찾아요</title>
  <style>
    * {
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
      user-select: none;
    }

    body {
      margin: 0;
      font-family: "Pretendard", "Noto Sans KR", Arial, sans-serif;
      background: linear-gradient(180deg, #fff7dd 0%, #f0f8ff 100%);
      color: #222;
      min-height: 100vh;
    }

    .app {
      width: 100%;
      min-height: 100vh;
      padding: 24px;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    header {
      width: 100%;
      max-width: 1100px;
      text-align: center;
      margin-bottom: 18px;
    }

    h1 {
      font-size: clamp(36px, 5vw, 64px);
      margin: 16px 0 8px;
      color: #263238;
      letter-spacing: -1px;
    }

    .subtitle {
      font-size: clamp(20px, 2.4vw, 30px);
      margin: 0;
      color: #4b5563;
      font-weight: 700;
    }

    .screen {
      display: none;
      width: 100%;
      max-width: 1100px;
      animation: pop 0.18s ease-out;
    }

    .screen.active {
      display: block;
    }

    @keyframes pop {
      from { transform: scale(0.98); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }

    .menu-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 24px;
      margin-top: 36px;
    }

    .big-btn {
      min-height: 190px;
      border: 0;
      border-radius: 28px;
      font-size: clamp(28px, 3vw, 42px);
      font-weight: 900;
      cursor: pointer;
      box-shadow: 0 10px 0 rgba(0,0,0,0.16);
      transition: transform 0.08s, box-shadow 0.08s;
      color: #1f2937;
    }

    .big-btn:active, .item-card:active, .control-btn:active {
      transform: translateY(5px);
      box-shadow: 0 5px 0 rgba(0,0,0,0.16);
    }

    .yellow { background: #ffe082; }
    .pink { background: #ffcdd2; }
    .green { background: #c8e6c9; }
    .blue { background: #bbdefb; }
    .purple { background: #d1c4e9; }
    .orange { background: #ffcc80; }

    .top-controls {
      display: flex;
      justify-content: center;
      gap: 12px;
      margin: 12px 0 22px;
      flex-wrap: wrap;
    }

    .control-btn {
      border: 0;
      border-radius: 999px;
      padding: 14px 24px;
      font-size: 22px;
      font-weight: 800;
      background: #eceff1;
      cursor: pointer;
      box-shadow: 0 5px 0 rgba(0,0,0,0.14);
    }

    .question-box {
      background: white;
      border-radius: 28px;
      padding: 24px;
      text-align: center;
      box-shadow: 0 8px 24px rgba(0,0,0,0.12);
      margin-bottom: 22px;
    }

    .question-box h2 {
      margin: 0;
      font-size: clamp(32px, 4vw, 54px);
      color: #111827;
    }

    .items-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 18px;
    }

    .item-card {
      min-height: 210px;
      border: 6px solid transparent;
      border-radius: 28px;
      background: #fff;
      cursor: pointer;
      box-shadow: 0 8px 0 rgba(0,0,0,0.13);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 12px;
      font-size: 28px;
      font-weight: 900;
    }

    .emoji {
      font-size: clamp(58px, 8vw, 96px);
      line-height: 1;
    }

    .feedback {
      margin-top: 24px;
      min-height: 72px;
      border-radius: 24px;
      background: rgba(255,255,255,0.9);
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      font-size: clamp(28px, 3vw, 44px);
      font-weight: 900;
      color: #1f2937;
      box-shadow: 0 6px 16px rgba(0,0,0,0.1);
      padding: 10px 20px;
    }

    .correct {
      border-color: #22c55e !important;
      background: #ecfdf5 !important;
    }

    .wrong {
      border-color: #ef4444 !important;
      background: #fff1f2 !important;
    }

    .draw-tabs {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
      justify-content: center;
      margin-bottom: 16px;
    }

    .draw-tab {
      border: 0;
      border-radius: 18px;
      padding: 14px 18px;
      font-size: 22px;
      font-weight: 900;
      background: #e0e7ff;
      cursor: pointer;
    }

    .draw-tab.active-tab {
      background: #818cf8;
      color: white;
    }

    .canvas-wrap {
      width: 100%;
      background: white;
      border-radius: 28px;
      padding: 16px;
      box-shadow: 0 8px 24px rgba(0,0,0,0.14);
    }

    canvas {
      width: 100%;
      height: 520px;
      display: block;
      border-radius: 22px;
      background: #fffdf7;
      border: 4px dashed #cbd5e1;
      touch-action: none;
    }

    .draw-help {
      text-align: center;
      font-size: clamp(24px, 2.6vw, 36px);
      font-weight: 900;
      margin: 14px 0;
      color: #374151;
    }

    .draw-controls {
      display: flex;
      justify-content: center;
      gap: 12px;
      flex-wrap: wrap;
      margin-top: 16px;
    }

    .primary {
      background: #86efac;
    }

    @media (max-width: 850px) {
      .menu-grid, .items-grid {
        grid-template-columns: 1fr;
      }

      .big-btn {
        min-height: 130px;
      }

      .item-card {
        min-height: 160px;
      }

      canvas {
        height: 430px;
      }
    }
  </style>
</head>
<body>
  <div class="app">
    <header>
      <h1>세모를 찾아요</h1>
      <p class="subtitle">모양을 보고, 찾고, 그려요</p>
    </header>

    <main id="home" class="screen active">
      <div class="menu-grid">
        <button class="big-btn yellow" onclick="startQuiz('triangle')">▲<br>세모 물건 찾기</button>
        <button class="big-btn pink" onclick="startQuiz('square')">■<br>네모 물건 찾기</button>
        <button class="big-btn green" onclick="showScreen('draw'); initDraw('free')">✏️<br>세모 그리기</button>
      </div>
    </main>

    <section id="quiz" class="screen">
      <div class="top-controls">
        <button class="control-btn" onclick="showScreen('home')">처음으로</button>
        <button class="control-btn" onclick="restartQuiz()">다시 하기</button>
      </div>

      <div class="question-box">
        <h2 id="quizQuestion">세모 모양 물건을 찾아요</h2>
      </div>

      <div id="itemsGrid" class="items-grid"></div>
      <div id="feedback" class="feedback">알맞은 물건을 눌러 보세요.</div>
    </section>

    <section id="draw" class="screen">
      <div class="top-controls">
        <button class="control-btn" onclick="showScreen('home')">처음으로</button>
        <button class="control-btn" onclick="clearCanvas()">지우기</button>
      </div>

      <div class="draw-tabs">
        <button id="freeTab" class="draw-tab" onclick="initDraw('free')">자유롭게 세모 그리기</button>
        <button id="dotTab" class="draw-tab" onclick="initDraw('dot')">점 3개 찍기</button>
        <button id="connectTab" class="draw-tab" onclick="initDraw('connect')">점을 이어 세모 만들기</button>
      </div>

      <p id="drawHelp" class="draw-help">손가락이나 펜으로 세모를 그려 보세요.</p>

      <div class="canvas-wrap">
        <canvas id="drawCanvas"></canvas>
      </div>

      <div class="draw-controls">
        <button class="control-btn primary" onclick="makeTriangle()">세모 만들기</button>
        <button class="control-btn" onclick="clearCanvas()">다시 그리기</button>
      </div>
    </section>
  </div>

  <script>
    const screens = document.querySelectorAll('.screen');
    const itemsGrid = document.getElementById('itemsGrid');
    const feedback = document.getElementById('feedback');
    const quizQuestion = document.getElementById('quizQuestion');

    let currentQuiz = 'triangle';

    const triangleItems = [
      { name: '삼각김밥', emoji: '🍙', shape: 'triangle' },
      { name: '피자 조각', emoji: '🍕', shape: 'triangle' },
      { name: '세모 표지판', emoji: '⚠️', shape: 'triangle' },
      { name: '공', emoji: '⚽', shape: 'circle' },
      { name: '시계', emoji: '🕘', shape: 'circle' },
      { name: '접시', emoji: '🍽️', shape: 'circle' }
    ];

    const squareItems = [
      { name: '책', emoji: '📕', shape: 'square' },
      { name: '창문', emoji: '🪟', shape: 'square' },
      { name: '선물상자', emoji: '🎁', shape: 'square' },
      { name: '공', emoji: '⚽', shape: 'circle' },
      { name: '피자 조각', emoji: '🍕', shape: 'triangle' },
      { name: '삼각김밥', emoji: '🍙', shape: 'triangle' }
    ];

    function showScreen(id) {
      screens.forEach(screen => screen.classList.remove('active'));
      document.getElementById(id).classList.add('active');
      if (id === 'draw') resizeCanvas();
    }

    function shuffle(array) {
      return [...array].sort(() => Math.random() - 0.5);
    }

    function startQuiz(type) {
      currentQuiz = type;
      showScreen('quiz');
      renderQuiz();
    }

    function restartQuiz() {
      renderQuiz();
    }

    function renderQuiz() {
      feedback.textContent = '알맞은 물건을 눌러 보세요.';
      feedback.style.color = '#1f2937';
      itemsGrid.innerHTML = '';

      const target = currentQuiz === 'triangle' ? 'triangle' : 'square';
      const questionText = currentQuiz === 'triangle'
        ? '세모 모양 물건을 찾아요'
        : '네모 모양 물건을 찾아요';

      quizQuestion.textContent = questionText;

      const items = currentQuiz === 'triangle' ? triangleItems : squareItems;
      shuffle(items).forEach(item => {
        const card = document.createElement('button');
        card.className = 'item-card';
        card.innerHTML = `<div class="emoji">${item.emoji}</div><div>${item.name}</div>`;
        card.onclick = () => checkAnswer(card, item.shape === target, target);
        itemsGrid.appendChild(card);
      });
    }

    function checkAnswer(card, isCorrect, target) {
      document.querySelectorAll('.item-card').forEach(c => c.classList.remove('correct', 'wrong'));

      if (isCorrect) {
        card.classList.add('correct');
        feedback.textContent = target === 'triangle' ? '맞아요! 세모 모양이에요.' : '맞아요! 네모 모양이에요.';
        feedback.style.color = '#15803d';
      } else {
        card.classList.add('wrong');
        feedback.textContent = target === 'triangle' ? '다시 찾아볼까요? 세모 모양을 찾아요.' : '다시 찾아볼까요? 네모 모양을 찾아요.';
        feedback.style.color = '#b91c1c';
      }
    }

    const canvas = document.getElementById('drawCanvas');
    const ctx = canvas.getContext('2d');
    const drawHelp = document.getElementById('drawHelp');
    let drawMode = 'free';
    let drawing = false;
    let dots = [];
    let connectIndex = 0;

    function resizeCanvas() {
      const rect = canvas.getBoundingClientRect();
      const oldWidth = canvas.width;
      const oldHeight = canvas.height;

      if (oldWidth === Math.floor(rect.width) && oldHeight === Math.floor(rect.height)) return;

      canvas.width = Math.floor(rect.width);
      canvas.height = Math.floor(rect.height);
      setupLineStyle();
      if (drawMode === 'connect') drawPresetDots();
    }

    window.addEventListener('resize', resizeCanvas);

    function setupLineStyle() {
      ctx.lineWidth = 14;
      ctx.lineCap = 'round';
      ctx.lineJoin = 'round';
      ctx.strokeStyle = '#111827';
      ctx.fillStyle = '#ef4444';
    }

    function initDraw(mode) {
      drawMode = mode;
      dots = [];
      connectIndex = 0;
      document.querySelectorAll('.draw-tab').forEach(tab => tab.classList.remove('active-tab'));

      if (mode === 'free') {
        document.getElementById('freeTab').classList.add('active-tab');
        drawHelp.textContent = '손가락이나 펜으로 세모를 그려 보세요.';
      }

      if (mode === 'dot') {
        document.getElementById('dotTab').classList.add('active-tab');
        drawHelp.textContent = '빈 곳에 점을 3개 찍어 보세요.';
      }

      if (mode === 'connect') {
        document.getElementById('connectTab').classList.add('active-tab');
        drawHelp.textContent = '빨간 점을 이어 세모를 만들어 보세요.';
      }

      resizeCanvas();
      clearCanvas();
      if (mode === 'connect') drawPresetDots();
    }

    function getPos(event) {
      const rect = canvas.getBoundingClientRect();
      const clientX = event.touches ? event.touches[0].clientX : event.clientX;
      const clientY = event.touches ? event.touches[0].clientY : event.clientY;
      return {
        x: clientX - rect.left,
        y: clientY - rect.top
      };
    }

    function startDraw(event) {
      event.preventDefault();
      resizeCanvas();
      const pos = getPos(event);

      if (drawMode === 'dot') {
        if (dots.length < 3) {
          dots.push(pos);
          drawDot(pos.x, pos.y, dots.length);
          if (dots.length === 3) {
            drawHelp.textContent = '점 3개를 찍었어요. 세모 만들기 버튼을 눌러 보세요.';
          }
        }
        return;
      }

      drawing = true;
      ctx.beginPath();
      ctx.moveTo(pos.x, pos.y);
    }

    function moveDraw(event) {
      if (!drawing) return;
      event.preventDefault();
      const pos = getPos(event);
      ctx.lineTo(pos.x, pos.y);
      ctx.stroke();
    }

    function endDraw(event) {
      if (!drawing) return;
      event.preventDefault();
      drawing = false;
      ctx.closePath();
    }

    function drawDot(x, y, number = '') {
      ctx.beginPath();
      ctx.fillStyle = '#ef4444';
      ctx.arc(x, y, 18, 0, Math.PI * 2);
      ctx.fill();
      ctx.fillStyle = '#ffffff';
      ctx.font = 'bold 22px Arial';
      ctx.textAlign = 'center';
      ctx.textBaseline = 'middle';
      ctx.fillText(number, x, y + 1);
      setupLineStyle();
    }

    function drawPresetDots() {
      dots = [
        { x: canvas.width / 2, y: canvas.height * 0.18 },
        { x: canvas.width * 0.23, y: canvas.height * 0.78 },
        { x: canvas.width * 0.77, y: canvas.height * 0.78 }
      ];
      dots.forEach((dot, index) => drawDot(dot.x, dot.y, index + 1));
    }

    function makeTriangle() {
      if (drawMode === 'free') return;

      if (dots.length < 3) {
        drawHelp.textContent = '점 3개가 필요해요.';
        return;
      }

      setupLineStyle();
      ctx.beginPath();
      ctx.moveTo(dots[0].x, dots[0].y);
      ctx.lineTo(dots[1].x, dots[1].y);
      ctx.lineTo(dots[2].x, dots[2].y);
      ctx.closePath();
      ctx.stroke();
      dots.forEach((dot, index) => drawDot(dot.x, dot.y, index + 1));
      drawHelp.textContent = '세모가 완성되었어요!';
    }

    function clearCanvas() {
      resizeCanvas();
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      setupLineStyle();

      if (drawMode === 'dot') {
        dots = [];
        drawHelp.textContent = '빈 곳에 점을 3개 찍어 보세요.';
      }

      if (drawMode === 'connect') {
        drawHelp.textContent = '빨간 점을 이어 세모를 만들어 보세요.';
        drawPresetDots();
      }

      if (drawMode === 'free') {
        drawHelp.textContent = '손가락이나 펜으로 세모를 그려 보세요.';
      }
    }

    canvas.addEventListener('mousedown', startDraw);
    canvas.addEventListener('mousemove', moveDraw);
    canvas.addEventListener('mouseup', endDraw);
    canvas.addEventListener('mouseleave', endDraw);

    canvas.addEventListener('touchstart', startDraw, { passive: false });
    canvas.addEventListener('touchmove', moveDraw, { passive: false });
    canvas.addEventListener('touchend', endDraw, { passive: false });

    setTimeout(() => {
      resizeCanvas();
      setupLineStyle();
    }, 100);
  </script>
</body>
</html>
