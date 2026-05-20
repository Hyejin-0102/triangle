<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>○ △ □ 찾아요</title>
  <style>
    * {
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
      user-select: none;
    }

    body {
      margin: 0;
      font-family: "Pretendard", "Noto Sans KR", Arial, sans-serif;
      background: linear-gradient(180deg, #fff7dd 0%, #eaf7ff 100%);
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
      overflow: hidden;
    }

    header {
      width: 100%;
      max-width: 1180px;
      text-align: center;
      margin-bottom: 18px;
    }

    h1 {
      font-size: clamp(42px, 6vw, 84px);
      margin: 12px 0 8px;
      color: #263238;
      letter-spacing: -1px;
    }

    .subtitle {
      font-size: clamp(22px, 2.8vw, 36px);
      margin: 0;
      color: #4b5563;
      font-weight: 800;
    }

    .screen {
      display: none;
      width: 100%;
      max-width: 1180px;
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
      margin-top: 34px;
    }

    .big-btn {
      min-height: 210px;
      border: 0;
      border-radius: 30px;
      font-size: clamp(28px, 3vw, 42px);
      font-weight: 950;
      cursor: pointer;
      box-shadow: 0 10px 0 rgba(0,0,0,0.16);
      transition: transform 0.08s, box-shadow 0.08s;
      color: #1f2937;
      line-height: 1.35;
      padding: 20px;
    }

    .big-btn:active, .item-card:active, .control-btn:active, .shape-btn:active, .draw-tab:active {
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

    .control-btn, .shape-btn, .draw-tab {
      border: 0;
      border-radius: 999px;
      padding: 14px 24px;
      font-size: 22px;
      font-weight: 900;
      background: #eceff1;
      cursor: pointer;
      box-shadow: 0 5px 0 rgba(0,0,0,0.14);
    }

    .shape-btn.active-shape, .draw-tab.active-tab {
      background: #4f46e5;
      color: white;
    }

    .title-box, .question-box {
      background: white;
      border-radius: 28px;
      padding: 22px;
      text-align: center;
      box-shadow: 0 8px 24px rgba(0,0,0,0.12);
      margin-bottom: 22px;
    }

    .title-box h2, .question-box h2 {
      margin: 0;
      font-size: clamp(32px, 4vw, 54px);
      color: #111827;
    }

    .feature-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 20px;
    }

    .feature-card {
      background: white;
      border-radius: 32px;
      padding: 24px;
      text-align: center;
      box-shadow: 0 8px 24px rgba(0,0,0,0.12);
      min-height: 360px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      gap: 18px;
    }

    .shape-mark {
      font-size: clamp(88px, 10vw, 150px);
      line-height: 1;
      font-weight: 900;
    }

    .feature-card ul {
      list-style: none;
      padding: 0;
      margin: 0;
      display: flex;
      flex-direction: column;
      gap: 14px;
    }

    .feature-card li {
      background: #f8fafc;
      border-radius: 18px;
      padding: 14px;
      font-size: clamp(24px, 2.6vw, 34px);
      font-weight: 900;
    }

    .shape-select {
      display: flex;
      justify-content: center;
      gap: 12px;
      flex-wrap: wrap;
      margin-bottom: 18px;
    }

    .items-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 18px;
    }

    .item-card {
      min-height: 190px;
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
      font-size: 26px;
      font-weight: 950;
      padding: 12px;
    }

    .emoji {
      font-size: clamp(54px, 7vw, 88px);
      line-height: 1;
    }

    .feedback {
      margin-top: 24px;
      min-height: 74px;
      border-radius: 24px;
      background: rgba(255,255,255,0.92);
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      font-size: clamp(28px, 3vw, 44px);
      font-weight: 950;
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

    .found {
      opacity: 0.65;
      border-color: #22c55e !important;
      background: #ecfdf5 !important;
    }

    .draw-tabs {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
      justify-content: center;
      margin-bottom: 16px;
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
      height: 500px;
      display: block;
      border-radius: 22px;
      background: #fffdf7;
      border: 4px dashed #cbd5e1;
      touch-action: none;
    }

    .draw-help {
      text-align: center;
      font-size: clamp(24px, 2.6vw, 36px);
      font-weight: 950;
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

    .celebration {
      position: fixed;
      inset: 0;
      pointer-events: none;
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 100;
      background: rgba(255,255,255,0.3);
    }

    .celebration.show {
      display: flex;
      animation: fadeOut 1.5s ease-in forwards;
    }

    .celebration-text {
      font-size: clamp(48px, 8vw, 100px);
      font-weight: 950;
      background: white;
      border-radius: 36px;
      padding: 30px 50px;
      box-shadow: 0 12px 40px rgba(0,0,0,0.22);
      animation: bounce 0.7s ease-in-out infinite alternate;
    }

    @keyframes bounce {
      from { transform: scale(1) rotate(-2deg); }
      to { transform: scale(1.08) rotate(2deg); }
    }

    @keyframes fadeOut {
      0%, 70% { opacity: 1; }
      100% { opacity: 0; }
    }

    .confetti {
      position: fixed;
      top: -20px;
      width: 14px;
      height: 24px;
      border-radius: 4px;
      pointer-events: none;
      animation: fall 1.4s linear forwards;
      z-index: 110;
    }

    @keyframes fall {
      to {
        transform: translateY(110vh) rotate(720deg);
        opacity: 0;
      }
    }

    @media (max-width: 950px) {
      .menu-grid, .feature-grid, .items-grid {
        grid-template-columns: 1fr;
      }

      .big-btn {
        min-height: 130px;
      }

      .item-card {
        min-height: 150px;
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
      <h1>○ △ □ 찾아요</h1>
      <p class="subtitle">모양을 보고, 찾고, 그려요</p>
    </header>

    <main id="home" class="screen active">
      <div class="menu-grid">
        <button class="big-btn yellow" onclick="showScreen('features')">○ △ □<br>모양의 특징</button>
        <button class="big-btn pink" onclick="showScreen('quiz'); startQuiz('circle')">○ △ □<br>모양 물건 찾기</button>
        <button class="big-btn green" onclick="showScreen('draw'); initDraw('free')">○ △ □<br>모양 그리기</button>
      </div>
    </main>

    <section id="features" class="screen">
      <div class="top-controls">
        <button class="control-btn" onclick="showScreen('home')">처음으로</button>
        <button class="control-btn" onclick="restartFeatureQuiz()">다시 하기</button>
      </div>

      <div class="title-box">
        <h2>모양의 특징을 찾아요</h2>
      </div>

      <div class="question-box">
        <h2 id="featureQuestion">동그라미의 특징은 무엇일까요?</h2>
      </div>

      <div id="featureOptions" class="items-grid"></div>
      <div id="featureFeedback" class="feedback">알맞은 특징을 눌러 보세요.</div>
    </section>

    <section id="quiz" class="screen">
      <div class="top-controls">
        <button class="control-btn" onclick="showScreen('home')">처음으로</button>
        <button class="control-btn" onclick="restartQuiz()">다시 하기</button>
      </div>

      <div class="shape-select">
        <button id="circleQuizBtn" class="shape-btn" onclick="startQuiz('circle')">○ 동그라미</button>
        <button id="triangleQuizBtn" class="shape-btn" onclick="startQuiz('triangle')">△ 세모</button>
        <button id="squareQuizBtn" class="shape-btn" onclick="startQuiz('square')">□ 네모</button>
      </div>

      <div class="question-box">
        <h2 id="quizQuestion">동그라미 모양 물건을 찾아요</h2>
      </div>

      <div id="itemsGrid" class="items-grid"></div>
      <div id="feedback" class="feedback">알맞은 물건을 눌러 보세요.</div>
    </section>

    <section id="draw" class="screen">
      <div class="top-controls">
        <button class="control-btn" onclick="showScreen('home')">처음으로</button>
        <button class="control-btn" onclick="clearCanvas()">지우기</button>
      </div>

      <div class="shape-select">
        <button id="circleDrawBtn" class="shape-btn" onclick="setDrawShape('circle')">○ 동그라미</button>
        <button id="triangleDrawBtn" class="shape-btn" onclick="setDrawShape('triangle')">△ 세모</button>
        <button id="squareDrawBtn" class="shape-btn" onclick="setDrawShape('square')">□ 네모</button>
      </div>

      <div class="draw-tabs">
        <button id="freeTab" class="draw-tab" onclick="initDraw('free')">자유롭게 그리기</button>
        <button id="connectTab" class="draw-tab" onclick="initDraw('connect')">점 잇기</button>
        <button id="dotTab" class="draw-tab" onclick="initDraw('dot')">점 찍고 완성하기</button>
      </div>

      <p id="drawHelp" class="draw-help">손가락이나 펜으로 모양을 그려 보세요.</p>

      <div class="canvas-wrap">
        <canvas id="drawCanvas"></canvas>
      </div>

      <div class="draw-controls">
        <button class="control-btn primary" onclick="checkDrawing()">확인하기</button>
        <button id="makeShapeBtn" class="control-btn primary" onclick="makeShape()">모양 완성</button>
        <button class="control-btn" onclick="clearCanvas()">다시 그리기</button>
      </div>
    </section>
  </div>

  <div id="celebration" class="celebration">
    <div class="celebration-text">참 잘했어요!</div>
  </div>

  <script>
    const screens = document.querySelectorAll('.screen');
    const itemsGrid = document.getElementById('itemsGrid');
    const feedback = document.getElementById('feedback');
    const quizQuestion = document.getElementById('quizQuestion');
    const celebration = document.getElementById('celebration');

    let currentQuiz = 'circle';
    let currentFeatureQuiz = 0;
    let foundCount = 0;
    let audioContext;

    const shapeLabels = {
      circle: '동그라미',
      triangle: '세모',
      square: '네모'
    };

    const shapeSymbols = {
      circle: '○',
      triangle: '△',
      square: '□'
    };

    const quizItems = [
      { name: '자동차 바퀴', emoji: '🛞', shape: 'circle' },
      { name: '쿠키', emoji: '🍪', shape: 'circle' },
      { name: '시계', emoji: '🕘', shape: 'circle' },
      { name: '사탕', emoji: '🍬', shape: 'circle' },
      { name: '삼각김밥', emoji: '🍙', shape: 'triangle' },
      { name: '삼각자', emoji: '📐', shape: 'triangle' },
      { name: '조각피자', emoji: '🍕', shape: 'triangle' },
      { name: '세모 표지판', emoji: '⚠️', shape: 'triangle' },
      { name: '책', emoji: '📕', shape: 'square' },
      { name: '책상', emoji: '🟫', shape: 'square' },
      { name: '텔레비전', emoji: '📺', shape: 'square' },
      { name: '스마트폰', emoji: '📱', shape: 'square' }
    ];

    const featureQuestions = [
      {
        shape: '○',
        question: '동그라미의 특징은 무엇일까요?',
        answer: '둥글다 / 모서리가 없다',
        options: ['둥글다 / 모서리가 없다', '반듯한 선이 3개 있다', '반듯한 선이 4개 있다']
      },
      {
        shape: '△',
        question: '세모의 특징은 무엇일까요?',
        answer: '반듯한 선이 3개 / 뾰족한 부분이 3개 있다',
        options: ['모서리가 없다', '반듯한 선이 3개 / 뾰족한 부분이 3개 있다', '반듯한 선이 4개 / 뾰족한 부분이 4개 있다']
      },
      {
        shape: '□',
        question: '네모의 특징은 무엇일까요?',
        answer: '반듯한 선이 4개 / 뾰족한 부분이 4개 있다',
        options: ['둥글다', '반듯한 선이 3개 / 뾰족한 부분이 3개 있다', '반듯한 선이 4개 / 뾰족한 부분이 4개 있다']
      }
    ];

    function showScreen(id) {
      screens.forEach(screen => screen.classList.remove('active'));
      document.getElementById(id).classList.add('active');
      if (id === 'features') renderFeatureQuiz();
      if (id === 'draw') resizeCanvas();
    }

    function shuffle(array) {
      return [...array].sort(() => Math.random() - 0.5);
    }

    function restartFeatureQuiz() {
      currentFeatureQuiz = 0;
      renderFeatureQuiz();
    }

    function renderFeatureQuiz() {
      const questionData = featureQuestions[currentFeatureQuiz];
      const featureQuestion = document.getElementById('featureQuestion');
      const featureOptions = document.getElementById('featureOptions');
      const featureFeedback = document.getElementById('featureFeedback');

      featureQuestion.textContent = `${questionData.shape} ${questionData.question}`;
      featureFeedback.textContent = '알맞은 특징을 눌러 보세요.';
      featureFeedback.style.color = '#1f2937';
      featureOptions.innerHTML = '';

      shuffle(questionData.options).forEach(option => {
        const card = document.createElement('button');
        card.className = 'item-card';
        card.innerHTML = `<div class="emoji">${questionData.shape}</div><div>${option}</div>`;
        card.onclick = () => checkFeatureAnswer(card, option === questionData.answer);
        featureOptions.appendChild(card);
      });
    }

    function checkFeatureAnswer(card, isCorrect) {
      const featureFeedback = document.getElementById('featureFeedback');
      document.querySelectorAll('#featureOptions .item-card').forEach(c => c.classList.remove('correct', 'wrong'));

      if (isCorrect) {
        card.classList.add('correct');
        playDingDongDang();
        featureFeedback.textContent = '맞아요! 모양의 특징을 잘 찾았어요.';
        featureFeedback.style.color = '#15803d';

        setTimeout(() => {
          currentFeatureQuiz += 1;
          if (currentFeatureQuiz >= featureQuestions.length) {
            currentFeatureQuiz = 0;
            featureFeedback.textContent = '모양의 특징을 모두 찾았어요!';
            showCelebration('참 잘했어요!');
          } else {
            renderFeatureQuiz();
          }
        }, 900);
      } else {
        card.classList.add('wrong');
        playWrongSound();
        featureFeedback.textContent = '다시 생각해 볼까요?';
        featureFeedback.style.color = '#b91c1c';
      }
    }

    function startQuiz(type) {
      currentQuiz = type;
      foundCount = 0;
      updateActiveQuizButton();
      renderQuiz();
    }

    function restartQuiz() {
      foundCount = 0;
      renderQuiz();
    }

    function updateActiveQuizButton() {
      ['circle', 'triangle', 'square'].forEach(shape => {
        const button = document.getElementById(shape + 'QuizBtn');
        if (button) button.classList.toggle('active-shape', currentQuiz === shape);
      });
    }

    function renderQuiz() {
      feedback.textContent = '알맞은 물건을 눌러 보세요.';
      feedback.style.color = '#1f2937';
      itemsGrid.innerHTML = '';

      quizQuestion.textContent = `${shapeSymbols[currentQuiz]} ${shapeLabels[currentQuiz]} 모양 물건을 찾아요`;

      shuffle(quizItems).forEach(item => {
        const card = document.createElement('button');
        card.className = 'item-card';
        card.dataset.shape = item.shape;
        card.dataset.found = 'false';
        card.innerHTML = `<div class="emoji">${item.emoji}</div><div>${item.name}</div>`;
        card.onclick = () => checkAnswer(card, item.shape === currentQuiz);
        itemsGrid.appendChild(card);
      });
    }

    function checkAnswer(card, isCorrect) {
      document.querySelectorAll('.item-card').forEach(c => c.classList.remove('correct', 'wrong'));

      if (isCorrect) {
        if (card.dataset.found === 'true') return;
        card.dataset.found = 'true';
        card.classList.add('correct', 'found');
        foundCount += 1;
        playDingDongDang();
        feedback.textContent = `맞아요! ${shapeLabels[currentQuiz]} 모양이에요. (${foundCount}/4)`;
        feedback.style.color = '#15803d';

        if (foundCount >= 4) {
          feedback.textContent = `모두 찾았어요! ${shapeLabels[currentQuiz]} 모양 성공!`;
          showCelebration('참 잘했어요!');
        }
      } else {
        card.classList.add('wrong');
        playWrongSound();
        feedback.textContent = `다시 찾아볼까요? ${shapeLabels[currentQuiz]} 모양을 찾아요.`;
        feedback.style.color = '#b91c1c';
      }
    }

    function getAudioContext() {
      if (!window.AudioContext && !window.webkitAudioContext) return null;
      if (!audioContext) {
        audioContext = new (window.AudioContext || window.webkitAudioContext)();
      }
      if (audioContext.state === 'suspended') {
        audioContext.resume();
      }
      return audioContext;
    }

    function beep(freq, start, duration, type = 'sine', volume = 0.2) {
      const ac = getAudioContext();
      if (!ac) return;
      const osc = ac.createOscillator();
      const gain = ac.createGain();
      osc.type = type;
      osc.frequency.setValueAtTime(freq, ac.currentTime + start);
      gain.gain.setValueAtTime(volume, ac.currentTime + start);
      gain.gain.exponentialRampToValueAtTime(0.001, ac.currentTime + start + duration);
      osc.connect(gain);
      gain.connect(ac.destination);
      osc.start(ac.currentTime + start);
      osc.stop(ac.currentTime + start + duration);
    }

    function playDingDongDang() {
      beep(660, 0, 0.18);
      beep(880, 0.18, 0.18);
      beep(1046, 0.36, 0.24);
    }

    function playWrongSound() {
      beep(180, 0, 0.34, 'sawtooth', 0.18);
    }

    function playTadaSound() {
      beep(523, 0, 0.14);
      beep(659, 0.14, 0.14);
      beep(784, 0.28, 0.14);
      beep(1046, 0.42, 0.36);
    }

    function showCelebration(text = '참 잘했어요!') {
      celebration.querySelector('.celebration-text').textContent = text;
      celebration.classList.remove('show');
      void celebration.offsetWidth;
      celebration.classList.add('show');
      makeConfetti();
      setTimeout(() => celebration.classList.remove('show'), 1600);
    }

    function makeConfetti() {
      const colors = ['#f87171', '#fbbf24', '#34d399', '#60a5fa', '#a78bfa', '#fb7185'];
      for (let i = 0; i < 60; i++) {
        const piece = document.createElement('div');
        piece.className = 'confetti';
        piece.style.left = Math.random() * 100 + 'vw';
        piece.style.background = colors[Math.floor(Math.random() * colors.length)];
        piece.style.animationDelay = Math.random() * 0.25 + 's';
        piece.style.animationDuration = 1 + Math.random() * 0.9 + 's';
        document.body.appendChild(piece);
        setTimeout(() => piece.remove(), 2200);
      }
    }

    const canvas = document.getElementById('drawCanvas');
    const ctx = canvas.getContext('2d');
    const drawHelp = document.getElementById('drawHelp');
    let drawMode = 'free';
    let currentDrawShape = 'circle';
    let drawing = false;
    let dots = [];
    let strokePoints = [];
    let autoCompletedShape = false;

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

    function setDrawShape(shape) {
      currentDrawShape = shape;
      updateActiveDrawShapeButton();
      clearCanvas();
    }

    function updateActiveDrawShapeButton() {
      ['circle', 'triangle', 'square'].forEach(shape => {
        const button = document.getElementById(shape + 'DrawBtn');
        if (button) button.classList.toggle('active-shape', currentDrawShape === shape);
      });
    }

    function initDraw(mode) {
      drawMode = mode;
      dots = [];
      strokePoints = [];
      autoCompletedShape = false;
      document.querySelectorAll('.draw-tab').forEach(tab => tab.classList.remove('active-tab'));

      if (mode === 'free') {
        document.getElementById('freeTab').classList.add('active-tab');
        drawHelp.textContent = `${shapeSymbols[currentDrawShape]} ${shapeLabels[currentDrawShape]} 모양을 자유롭게 그려 보세요.`;
      }

      if (mode === 'connect') {
        document.getElementById('connectTab').classList.add('active-tab');
        drawHelp.textContent = `빨간 점을 이어 ${shapeLabels[currentDrawShape]} 모양을 만들어 보세요.`;
      }

      if (mode === 'dot') {
        document.getElementById('dotTab').classList.add('active-tab');
        drawHelp.textContent = `점을 찍고 '모양 완성' 버튼을 눌러 보세요.`;
      }

      updateActiveDrawShapeButton();
      updateMakeShapeButton();
      resizeCanvas();
      clearCanvas();
    }

    function updateMakeShapeButton() {
      const makeShapeBtn = document.getElementById('makeShapeBtn');
      if (!makeShapeBtn) return;
      makeShapeBtn.style.display = drawMode === 'dot' ? 'inline-block' : 'none';
    }

    function getPos(event) {
      const rect = canvas.getBoundingClientRect();
      const clientX = event.touches ? event.touches[0].clientX : event.clientX;
      const clientY = event.touches ? event.touches[0].clientY : event.clientY;
      return { x: clientX - rect.left, y: clientY - rect.top };
    }

    function startDraw(event) {
      event.preventDefault();
      resizeCanvas();
      const pos = getPos(event);

      if (drawMode === 'dot') {
        const maxDots = currentDrawShape === 'circle' ? 1 : currentDrawShape === 'triangle' ? 3 : 4;
        if (dots.length < maxDots) {
          dots.push(pos);
          drawDot(pos.x, pos.y, dots.length);
          if (dots.length === maxDots) {
            drawHelp.textContent = `점을 다 찍었어요. '모양 완성' 버튼을 눌러 보세요.`;
          }
        }
        return;
      }

      drawing = true;
      strokePoints.push(pos);
      ctx.beginPath();
      ctx.moveTo(pos.x, pos.y);
    }

    function moveDraw(event) {
      if (!drawing) return;
      event.preventDefault();
      const pos = getPos(event);
      strokePoints.push(pos);
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
      if (!canvas.width || !canvas.height) return;
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      setupLineStyle();

      if (currentDrawShape === 'circle') {
        dots = [
          { x: canvas.width / 2, y: canvas.height / 2 }
        ];
      }

      if (currentDrawShape === 'triangle') {
        dots = [
          { x: canvas.width / 2, y: canvas.height * 0.18 },
          { x: canvas.width * 0.24, y: canvas.height * 0.78 },
          { x: canvas.width * 0.76, y: canvas.height * 0.78 }
        ];
      }

      if (currentDrawShape === 'square') {
        dots = [
          { x: canvas.width * 0.28, y: canvas.height * 0.22 },
          { x: canvas.width * 0.72, y: canvas.height * 0.22 },
          { x: canvas.width * 0.72, y: canvas.height * 0.76 },
          { x: canvas.width * 0.28, y: canvas.height * 0.76 }
        ];
      }

      dots.forEach((dot, index) => drawDot(dot.x, dot.y, index + 1));
    }

    function makeShape() {
      if (drawMode !== 'dot') return;

      const needed = currentDrawShape === 'circle' ? 1 : currentDrawShape === 'triangle' ? 3 : 4;
      if (dots.length < needed) {
        drawHelp.textContent = `${needed}개의 점이 필요해요.`;
        return;
      }

      setupLineStyle();
      ctx.beginPath();

      if (currentDrawShape === 'circle') {
        const center = dots[0];
        const radius = Math.min(canvas.width, canvas.height) * 0.24;
        ctx.arc(center.x, center.y, radius, 0, Math.PI * 2);
      } else {
        ctx.moveTo(dots[0].x, dots[0].y);
        for (let i = 1; i < dots.length; i++) {
          ctx.lineTo(dots[i].x, dots[i].y);
        }
        ctx.closePath();
      }

      ctx.stroke();
      dots.forEach((dot, index) => drawDot(dot.x, dot.y, index + 1));
      autoCompletedShape = true;
      drawHelp.textContent = `${shapeLabels[currentDrawShape]} 모양이 완성되었어요. 확인하기를 눌러 보세요.`;
    }

    function checkDrawing() {
      if (drawMode === 'dot' && autoCompletedShape) {
        drawHelp.textContent = `${shapeLabels[currentDrawShape]} 모양을 완성했어요!`;
        playTadaSound();
        showCelebration('짠~ 완성!');
        return;
      }

      if (strokePoints.length < 12) {
        drawHelp.textContent = '조금 더 크게 그려 볼까요?';
        playWrongSound();
        return;
      }

      const box = getBoundingBox(strokePoints);
      const width = box.maxX - box.minX;
      const height = box.maxY - box.minY;
      const start = strokePoints[0];
      const end = strokePoints[strokePoints.length - 1];
      const closed = distance(start, end) < Math.max(width, height) * 0.35;
      const corners = countCorners(strokePoints);
      const ratio = width / Math.max(height, 1);

      let success = false;
      let hint = '';

      if (currentDrawShape === 'circle') {
        success = closed && ratio > 0.55 && ratio < 1.8 && corners <= 4;
        hint = '동그라미는 둥글게 이어서 그려요.';
      }

      if (currentDrawShape === 'triangle') {
        success = closed && corners >= 2 && corners <= 5;
        hint = '세모는 반듯한 선 3개와 뾰족한 부분 3개가 있어요.';
      }

      if (currentDrawShape === 'square') {
        success = closed && corners >= 3 && corners <= 6 && ratio > 0.55 && ratio < 1.8;
        hint = '네모는 반듯한 선 4개와 뾰족한 부분 4개가 있어요.';
      }

      if (success) {
        drawHelp.textContent = `${shapeLabels[currentDrawShape]} 모양처럼 잘 그렸어요!`;
        playTadaSound();
        showCelebration('짠~ 완성!');
      } else {
        drawHelp.textContent = hint;
        playWrongSound();
      }
    }

    function getBoundingBox(points) {
      return points.reduce((box, p) => ({
        minX: Math.min(box.minX, p.x),
        minY: Math.min(box.minY, p.y),
        maxX: Math.max(box.maxX, p.x),
        maxY: Math.max(box.maxY, p.y)
      }), { minX: Infinity, minY: Infinity, maxX: -Infinity, maxY: -Infinity });
    }

    function distance(a, b) {
      return Math.hypot(a.x - b.x, a.y - b.y);
    }

    function countCorners(points) {
      if (points.length < 8) return 0;
      const sampled = [];
      const step = Math.max(4, Math.floor(points.length / 24));
      for (let i = 0; i < points.length; i += step) sampled.push(points[i]);

      let corners = 0;
      for (let i = 1; i < sampled.length - 1; i++) {
        const a = sampled[i - 1];
        const b = sampled[i];
        const c = sampled[i + 1];
        const angle1 = Math.atan2(b.y - a.y, b.x - a.x);
        const angle2 = Math.atan2(c.y - b.y, c.x - b.x);
        let diff = Math.abs(angle2 - angle1);
        diff = Math.min(diff, Math.PI * 2 - diff);
        if (diff > 0.65) corners++;
      }
      return corners;
    }

    function clearCanvas() {
      resizeCanvas();
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      setupLineStyle();
      dots = [];
      strokePoints = [];
      autoCompletedShape = false;

      if (drawMode === 'free') {
        drawHelp.textContent = `${shapeSymbols[currentDrawShape]} ${shapeLabels[currentDrawShape]} 모양을 자유롭게 그려 보세요.`;
      }

      if (drawMode === 'connect') {
        drawHelp.textContent = `빨간 점을 이어 ${shapeLabels[currentDrawShape]} 모양을 만들어 보세요.`;
        drawPresetDots();
      }

      if (drawMode === 'dot') {
        const needed = currentDrawShape === 'circle' ? 1 : currentDrawShape === 'triangle' ? 3 : 4;
        drawHelp.textContent = `빈 곳에 점을 ${needed}개 찍어 보세요.`;
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
      updateActiveQuizButton();
      updateActiveDrawShapeButton();
      updateMakeShapeButton();
    }, 100);
  </script>
</body>
</html>
