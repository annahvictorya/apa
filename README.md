<!DOCTYPE html>
<html lang="kk">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ХХІ ғасырға – 21 сабақ | Кітап оқитын ұлт</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=Raleway:wght@300;400;600&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #edf7f0;
    --surface: #dff0e6;
    --card: #ffffff;
    --accent: #2a9e50;
    --accent2: #3db86a;
    --danger: #d94f4f;
    --success: #2a9e50;
    --text: #1a3326;
    --muted: #5a7f68;
    --border: #b8dfc6;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Raleway', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Background pattern */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background:
      radial-gradient(ellipse 60% 40% at 20% 20%, rgba(42,158,80,0.07) 0%, transparent 60%),
      radial-gradient(ellipse 50% 60% at 80% 80%, rgba(61,184,106,0.05) 0%, transparent 60%);
    pointer-events: none;
    z-index: 0;
  }

  .container {
    position: relative;
    z-index: 1;
    max-width: 820px;
    margin: 0 auto;
    padding: 2rem 1.5rem 4rem;
  }

  /* ===== HEADER ===== */
  .header {
    text-align: center;
    padding: 2.5rem 0 2rem;
    border-bottom: 1px solid var(--border);
    margin-bottom: 2.5rem;
  }

  .project-badge {
    display: inline-block;
    font-size: 0.7rem;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--accent);
    border: 1px solid var(--accent);
    padding: 0.3rem 1rem;
    border-radius: 2px;
    margin-bottom: 1.2rem;
  }

  .header h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.6rem, 4vw, 2.4rem);
    font-weight: 900;
    line-height: 1.2;
    color: var(--text);
    margin-bottom: 0.5rem;
  }

  .header h1 span { color: var(--accent); }

  .header .subtitle {
    font-size: 0.85rem;
    color: var(--muted);
    letter-spacing: 0.05em;
  }

  /* ===== SCREENS ===== */
  .screen { display: none; animation: fadeIn 0.4s ease; }
  .screen.active { display: block; }
  @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

  /* ===== INTRO ===== */
  .intro-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
    margin: 2rem 0;
  }
  @media (max-width: 500px) { .intro-grid { grid-template-columns: 1fr; } }

  .info-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 1.2rem 1.4rem;
  }

  .info-card .label {
    font-size: 0.65rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 0.4rem;
  }

  .info-card .value {
    font-size: 1.5rem;
    font-family: 'Playfair Display', serif;
    font-weight: 700;
    color: var(--text);
  }

  .info-card .desc {
    font-size: 0.78rem;
    color: var(--muted);
    margin-top: 0.2rem;
  }

  .book-summary {
    background: var(--card);
    border-left: 3px solid var(--accent);
    border-radius: 0 8px 8px 0;
    padding: 1.2rem 1.5rem;
    margin: 1.5rem 0;
    font-size: 0.88rem;
    line-height: 1.7;
    color: var(--muted);
  }

  .book-summary strong { color: var(--text); }

  /* Difficulty selector */
  .difficulty-section {
    margin: 1.5rem 0;
  }

  .section-label {
    font-size: 0.7rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 0.8rem;
  }

  .difficulty-btns {
    display: flex;
    gap: 0.6rem;
    flex-wrap: wrap;
  }

  .diff-btn {
    flex: 1;
    min-width: 120px;
    padding: 0.7rem 1rem;
    border: 1px solid var(--border);
    background: var(--surface);
    border-radius: 6px;
    color: var(--muted);
    cursor: pointer;
    font-family: 'Raleway', sans-serif;
    font-size: 0.82rem;
    transition: all 0.2s;
    text-align: center;
  }

  .diff-btn:hover, .diff-btn.active {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(232,201,122,0.07);
  }

  .diff-btn .diff-name { font-weight: 600; display: block; }
  .diff-btn .diff-info { font-size: 0.7rem; opacity: 0.7; margin-top: 0.2rem; }

  /* Category selector */
  .category-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
    gap: 0.6rem;
    margin-top: 0.8rem;
  }

  .cat-btn {
    padding: 0.8rem 0.8rem;
    border: 1px solid var(--border);
    background: var(--surface);
    border-radius: 6px;
    color: var(--muted);
    cursor: pointer;
    font-family: 'Raleway', sans-serif;
    font-size: 0.78rem;
    transition: all 0.2s;
    text-align: left;
  }

  .cat-btn:hover, .cat-btn.selected {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(42,158,80,0.08);
  }

  .cat-btn .cat-icon { font-size: 1.2rem; display: block; margin-bottom: 0.3rem; }
  .cat-btn .cat-name { font-weight: 600; }

  /* ===== START BTN ===== */
  .btn-primary {
    display: block;
    width: 100%;
    padding: 1rem;
    background: linear-gradient(135deg, var(--accent) 0%, #1e7a3c 100%);
    color: #ffffff;
    color: #0d0f14;
    border: none;
    border-radius: 8px;
    font-family: 'Raleway', sans-serif;
    font-size: 0.95rem;
    font-weight: 700;
    letter-spacing: 0.05em;
    cursor: pointer;
    margin-top: 1.5rem;
    transition: all 0.2s;
  }
  .btn-primary:hover { transform: translateY(-1px); box-shadow: 0 8px 24px rgba(42,158,80,0.3); }
  .btn-primary:active { transform: translateY(0); }

  .btn-secondary {
    display: inline-block;
    padding: 0.7rem 1.5rem;
    background: transparent;
    color: var(--accent);
    border: 1px solid var(--accent);
    border-radius: 6px;
    font-family: 'Raleway', sans-serif;
    font-size: 0.85rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s;
  }
  .btn-secondary:hover { background: rgba(232,201,122,0.1); }

  /* ===== QUIZ SCREEN ===== */
  .quiz-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 1.5rem;
    gap: 1rem;
  }

  .progress-info { font-size: 0.78rem; color: var(--muted); }
  .progress-info strong { color: var(--accent); font-size: 1rem; }

  .score-badge {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 0.4rem 0.9rem;
    font-size: 0.78rem;
    color: var(--muted);
  }
  .score-badge span { color: var(--success); font-weight: 600; }

  .progress-bar {
    height: 3px;
    background: var(--border);
    border-radius: 2px;
    margin-bottom: 2rem;
    overflow: hidden;
  }

  .progress-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    border-radius: 2px;
    transition: width 0.4s ease;
  }

  /* Timer */
  .timer-wrap {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    margin-bottom: 1.5rem;
  }

  .timer-bar {
    flex: 1;
    height: 5px;
    background: var(--border);
    border-radius: 3px;
    overflow: hidden;
  }

  .timer-fill {
    height: 100%;
    background: var(--accent2);
    border-radius: 3px;
    transition: width 0.1s linear, background 0.3s;
  }

  .timer-fill.warning { background: var(--accent); }
  .timer-fill.danger { background: var(--danger); }

  .timer-num {
    font-size: 0.82rem;
    font-weight: 600;
    color: var(--accent2);
    min-width: 28px;
    text-align: right;
  }
  .timer-num.warning { color: var(--accent); }
  .timer-num.danger { color: var(--danger); }

  /* Question */
  .question-meta {
    display: flex;
    gap: 0.5rem;
    margin-bottom: 0.8rem;
    align-items: center;
    flex-wrap: wrap;
  }

  .q-chapter {
    font-size: 0.65rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--accent);
    background: rgba(232,201,122,0.1);
    border: 1px solid rgba(232,201,122,0.2);
    padding: 0.2rem 0.6rem;
    border-radius: 3px;
  }

  .q-difficulty {
    font-size: 0.65rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    padding: 0.2rem 0.6rem;
    border-radius: 3px;
  }
  .q-difficulty.easy { color: var(--success); background: rgba(122,206,160,0.1); border: 1px solid rgba(122,206,160,0.2); }
  .q-difficulty.medium { color: var(--accent); background: rgba(232,201,122,0.1); border: 1px solid rgba(232,201,122,0.2); }
  .q-difficulty.hard { color: var(--danger); background: rgba(224,122,122,0.1); border: 1px solid rgba(224,122,122,0.2); }

  .question-text {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1rem, 2.5vw, 1.25rem);
    line-height: 1.55;
    color: var(--text);
    margin-bottom: 1.5rem;
  }

  .options-grid {
    display: grid;
    gap: 0.7rem;
  }

  .option-btn {
    display: flex;
    align-items: flex-start;
    gap: 0.8rem;
    padding: 0.9rem 1.1rem;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    cursor: pointer;
    font-family: 'Raleway', sans-serif;
    font-size: 0.88rem;
    color: var(--text);
    text-align: left;
    transition: all 0.2s;
    line-height: 1.5;
  }

  .option-btn:hover:not(:disabled) {
    border-color: var(--accent);
    background: rgba(42,158,80,0.08);
    transform: translateX(4px);
  }

  .option-btn:disabled { cursor: default; }

  .option-letter {
    display: flex;
    align-items: center;
    justify-content: center;
    min-width: 26px;
    height: 26px;
    border-radius: 50%;
    border: 1px solid var(--border);
    font-size: 0.72rem;
    font-weight: 700;
    flex-shrink: 0;
    transition: all 0.2s;
    background: var(--surface);
  }

  .option-btn.correct {
    border-color: var(--success);
    background: rgba(122,206,160,0.12);
    transform: none;
  }
  .option-btn.correct .option-letter {
    background: var(--success);
    color: var(--bg);
    border-color: var(--success);
  }

  .option-btn.incorrect {
    border-color: var(--danger);
    background: rgba(224,122,122,0.1);
  }
  .option-btn.incorrect .option-letter {
    background: var(--danger);
    color: var(--bg);
    border-color: var(--danger);
  }

  /* Feedback */
  .feedback {
    display: none;
    margin-top: 1.2rem;
    padding: 1rem 1.2rem;
    border-radius: 8px;
    font-size: 0.85rem;
    line-height: 1.6;
    animation: fadeIn 0.3s ease;
  }
  .feedback.show { display: block; }
  .feedback.correct-fb { background: rgba(122,206,160,0.1); border: 1px solid rgba(122,206,160,0.25); }
  .feedback.incorrect-fb { background: rgba(224,122,122,0.08); border: 1px solid rgba(224,122,122,0.2); }
  .feedback .fb-icon { font-size: 1.1rem; margin-right: 0.4rem; }

  .next-btn-wrap {
    text-align: right;
    margin-top: 1.2rem;
    display: none;
  }
  .next-btn-wrap.show { display: block; }

  /* ===== RESULTS ===== */
  .result-hero {
    text-align: center;
    padding: 2rem 0;
    border-bottom: 1px solid var(--border);
    margin-bottom: 2rem;
  }

  .result-icon {
    font-size: 3rem;
    margin-bottom: 0.8rem;
    display: block;
  }

  .result-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.4rem, 3.5vw, 2rem);
    font-weight: 900;
    color: var(--text);
    margin-bottom: 0.5rem;
  }

  .result-subtitle {
    font-size: 0.85rem;
    color: var(--muted);
  }

  .score-display {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.5rem;
    margin: 1.5rem 0;
  }

  .score-big {
    font-family: 'Playfair Display', serif;
    font-size: 3.5rem;
    font-weight: 900;
    color: var(--accent);
    line-height: 1;
  }

  .score-total {
    font-size: 1.5rem;
    color: var(--muted);
    font-weight: 300;
  }

  .stats-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 0.8rem;
    margin: 1.5rem 0;
  }
  @media (max-width: 400px) { .stats-grid { grid-template-columns: 1fr; } }

  .stat-item {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 1rem;
    text-align: center;
  }

  .stat-num {
    font-family: 'Playfair Display', serif;
    font-size: 1.8rem;
    font-weight: 700;
  }
  .stat-num.green { color: var(--success); }
  .stat-num.red { color: var(--danger); }
  .stat-num.blue { color: var(--accent2); }

  .stat-label {
    font-size: 0.7rem;
    color: var(--muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-top: 0.3rem;
  }

  .level-badge {
    display: inline-block;
    padding: 0.5rem 1.5rem;
    border-radius: 20px;
    font-size: 0.8rem;
    font-weight: 700;
    letter-spacing: 0.1em;
    margin: 1rem 0;
  }

  .result-actions {
    display: flex;
    gap: 0.8rem;
    flex-wrap: wrap;
    margin-top: 1.5rem;
  }
  .result-actions .btn-primary { margin-top: 0; flex: 1; min-width: 140px; }
  .result-actions .btn-secondary { flex: 1; min-width: 140px; text-align: center; }

  /* Leaderboard review */
  .review-section { margin-top: 2rem; }

  .review-title {
    font-size: 0.7rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 1rem;
  }

  .review-item {
    display: flex;
    gap: 0.8rem;
    padding: 0.8rem;
    border-radius: 6px;
    margin-bottom: 0.6rem;
    border: 1px solid var(--border);
    background: var(--card);
    font-size: 0.82rem;
  }

  .review-item .r-icon { font-size: 1rem; flex-shrink: 0; margin-top: 1px; }
  .review-item .r-q { color: var(--muted); flex: 1; }
  .review-item .r-q strong { color: var(--text); display: block; margin-bottom: 0.2rem; }
  .review-item.r-correct { border-color: rgba(122,206,160,0.2); }
  .review-item.r-incorrect { border-color: rgba(224,122,122,0.2); }

  /* ===== FOOTER ===== */
  .footer {
    text-align: center;
    margin-top: 3rem;
    padding-top: 1.5rem;
    border-top: 1px solid var(--border);
    font-size: 0.72rem;
    color: var(--muted);
  }
  .footer strong { color: var(--accent); }
</style>
</head>
<body>
<div class="container">
  <div class="header">
    <div class="project-badge">🇰🇿 Кітап оқитын ұлт</div>
    <h1>ХХІ ғасырға – <span>21 сабақ</span></h1>
    <div class="subtitle">Ювал Ноаһ Харари · Білім викторинасы</div>
  </div>

  <!-- INTRO SCREEN -->
  <div class="screen active" id="screen-intro">
    <div class="intro-grid">
      <div class="info-card">
        <div class="label">Тарау саны</div>
        <div class="value">21</div>
        <div class="desc">5 бөлім бойынша</div>
      </div>
      <div class="info-card">
        <div class="label">Сұрақ саны</div>
        <div class="value">25</div>
        <div class="desc">Жан-жақты викторина</div>
      </div>
    </div>

    <div class="book-summary">
      <strong>«ХХІ ғасырға – 21 сабақ»</strong> — дүниежүзіне белгілі тарихшы Ювал Ноаһ Хараридің үшінші кітабы.
      Бүгінгі күннің өзекті мәселелері: жасанды интеллект, либерализмнің дағдарысы, терроризм, бостандық пен теңдік,
      білім беру болашағы — осы тақырыптар бойынша ойыңызды тексеріңіз!
    </div>

    <div class="difficulty-section">
      <div class="section-label">Қиындық деңгейін таңдаңыз</div>
      <div class="difficulty-btns">
        <button class="diff-btn active" data-diff="all" onclick="selectDiff(this)">
          <span class="diff-name">Барлығы</span>
          <span class="diff-info">Аралас сұрақтар</span>
        </button>
        <button class="diff-btn" data-diff="easy" onclick="selectDiff(this)">
          <span class="diff-name">🟢 Жеңіл</span>
          <span class="diff-info">Негізгі ұғымдар</span>
        </button>
        <button class="diff-btn" data-diff="medium" onclick="selectDiff(this)">
          <span class="diff-name">🟡 Орта</span>
          <span class="diff-info">Талдау сұрақтары</span>
        </button>
        <button class="diff-btn" data-diff="hard" onclick="selectDiff(this)">
          <span class="diff-name">🔴 Қиын</span>
          <span class="diff-info">Терең ойлау</span>
        </button>
      </div>
    </div>

    <div class="difficulty-section">
      <div class="section-label">Тақырыпты таңдаңыз</div>
      <div class="category-grid">
        <button class="cat-btn selected" data-cat="all" onclick="selectCat(this)">
          <span class="cat-icon">📚</span>
          <span class="cat-name">Барлық тақырып</span>
        </button>
        <button class="cat-btn" data-cat="tech" onclick="selectCat(this)">
          <span class="cat-icon">🤖</span>
          <span class="cat-name">Технология</span>
        </button>
        <button class="cat-btn" data-cat="politics" onclick="selectCat(this)">
          <span class="cat-icon">🏛️</span>
          <span class="cat-name">Саясат</span>
        </button>
        <button class="cat-btn" data-cat="truth" onclick="selectCat(this)">
          <span class="cat-icon">🔍</span>
          <span class="cat-name">Ақиқат</span>
        </button>
        <button class="cat-btn" data-cat="meaning" onclick="selectCat(this)">
          <span class="cat-icon">🧘</span>
          <span class="cat-name">Икемділік</span>
        </button>
      </div>
    </div>

    <button class="btn-primary" onclick="startGame()">▶ Ойынды бастау</button>
  </div>

  <!-- QUIZ SCREEN -->
  <div class="screen" id="screen-quiz">
    <div class="quiz-header">
      <div class="progress-info">Сұрақ <strong id="q-current">1</strong> / <span id="q-total">25</span></div>
      <div class="score-badge">Балл: <span id="live-score">0</span></div>
    </div>
    <div class="progress-bar"><div class="progress-fill" id="progress-fill"></div></div>

    <div class="timer-wrap">
      <div class="timer-bar"><div class="timer-fill" id="timer-fill"></div></div>
      <div class="timer-num" id="timer-num">30</div>
    </div>

    <div class="question-meta">
      <span class="q-chapter" id="q-chapter"></span>
      <span class="q-difficulty" id="q-diff-badge"></span>
    </div>
    <div class="question-text" id="question-text"></div>
    <div class="options-grid" id="options-grid"></div>
    <div class="feedback" id="feedback"></div>
    <div class="next-btn-wrap" id="next-wrap">
      <button class="btn-secondary" onclick="nextQuestion()">Келесі →</button>
    </div>
  </div>

  <!-- RESULTS SCREEN -->
  <div class="screen" id="screen-results">
    <div class="result-hero">
      <span class="result-icon" id="result-icon">🏆</span>
      <div class="result-title" id="result-title">Нәтиже</div>
      <div class="result-subtitle" id="result-subtitle"></div>
      <div class="score-display">
        <div class="score-big" id="result-score">0</div>
        <div class="score-total" id="result-total">/25</div>
      </div>
      <div class="level-badge" id="level-badge"></div>
    </div>

    <div class="stats-grid">
      <div class="stat-item">
        <div class="stat-num green" id="stat-correct">0</div>
        <div class="stat-label">Дұрыс</div>
      </div>
      <div class="stat-item">
        <div class="stat-num red" id="stat-wrong">0</div>
        <div class="stat-label">Қате</div>
      </div>
      <div class="stat-item">
        <div class="stat-num blue" id="stat-pct">0%</div>
        <div class="stat-label">Дәлдік</div>
      </div>
    </div>

    <div class="result-actions">
      <button class="btn-primary" onclick="restartGame()">↺ Қайта ойнау</button>
      <button class="btn-secondary" onclick="goHome()">⌂ Басты бет</button>
    </div>

    <div class="review-section">
      <div class="review-title">Жауаптарды қарау</div>
      <div id="review-list"></div>
    </div>
  </div>

  <div class="footer">
    <strong>Кітап оқитын ұлт</strong> жобасы · Кәсіби даму институты
  </div>
</div>

<script>
// ===================== QUESTION BANK =====================
const allQuestions = [
  // === TECHNOLOGY ===
  {
    cat: 'tech', diff: 'easy',
    chapter: '2-тарау: Жұмыс',
    q: 'Харари бойынша, ХХІ ғасырда жасанды интеллект пен роботтар экономикаға қандай негізгі қауіп төндіреді?',
    opts: ['Өнімділікті азайтады', 'Миллиондаған адамды жұмыссыз қалдыруы мүмкін', 'Тек ауыр жұмыстарды алмастырады', 'Тек дамушы елдерге ғана зиян тигізеді'],
    correct: 1,
    exp: 'Харари жасанды интеллект пен автоматтандырудың білімді маманды да, қарапайым жұмысшыны да жұмыссыз қалдыру қаупі бар екенін ескертеді.'
  },
  {
    cat: 'tech', diff: 'medium',
    chapter: '3-тарау: Еркіндік',
    q: '«Big Data» алгоритмдері туралы Харари қандай ойды жеткізеді?',
    opts: [
      'Алгоритмдер адамнан нашарырақ шешім қабылдайды',
      'Алгоритмдер адамның ішкі қалауын өзінен жақсырақ түсінуі мүмкін',
      'Big Data тек маркетингте пайдалы',
      'Деректерді жинау мүлде зиянсыз'
    ],
    correct: 1,
    exp: 'Харари алгоритмдердің сізді өзіңізден жақсырақ білетін жағдай туатынын — мүмкін білгенін де болашақта сіздің атыңызда шешім қабылдайтынын ескертеді.'
  },
  {
    cat: 'tech', diff: 'medium',
    chapter: '4-тарау: Теңдік',
    q: 'Харари «деректерге меншік» мәселесіне қалай қарайды?',
    opts: [
      'Деректер барлығына еркін болуы тиіс',
      'Деректерге монополия орнатқан ел немесе корпорация болашақта айрықша күшке ие болады',
      'Деректер мемлекеттің меншігі болуы керек',
      'Деректер мәселесі экономикалық теңдікке әсер етпейді'
    ],
    correct: 1,
    exp: '4-тарауда Харари «Мәліметке иелік ету – болашаққа иелік ету» деп тұжырымдайды. Деректерге бақылау орнатқандар саяси және экономикалық үстемдікке ие болады.'
  },
  {
    cat: 'tech', diff: 'hard',
    chapter: '3-тарау: Еркіндік',
    q: 'Харари «цифрлық диктатура» туралы пікірінде не деп тұжырымдайды?',
    opts: [
      'Цифрлық технология әрдайым демократияны нығайтады',
      'Биотехнология мен ЖИ-нің қосындысы демократияны бұрынғы формасында жоюы мүмкін',
      'Авторитаризм ХХІ ғасырда мүмкін емес',
      'Жасанды интеллект тек батыстық компанияларда дамиды'
    ],
    correct: 1,
    exp: 'Харари биометриялық бақылау мен ЖИ-нің жиынтығы адам психологиясын толық бақылауға мүмкіндік беретін «цифрлық диктатура» орнатуы мүмкін деп ескертеді.'
  },
  {
    cat: 'tech', diff: 'hard',
    chapter: '3-тарау: Еркіндік',
    q: 'Солтүстік Корея мысалын келтіре отырып, Харари биометриялық бақылаудың қандай қаупін сипаттайды?',
    opts: [
      'Азаматтардың денсаулық деректері ұрланады',
      'Режим азаматтардың сезімдерін нақты уақытта бақылап, ойлаған адамды жазалай алады',
      'Телефон байланысы мүмкін болмай қалады',
      'Экономикалық өсім тоқтайды'
    ],
    correct: 1,
    exp: 'Харари биометриялық білезік арқылы режим азаматтардың ашу сезімін де нақты байқап, алдын ала жазалай алатын болашақты елестетеді.'
  },

  // === POLITICS ===
  {
    cat: 'politics', diff: 'easy',
    chapter: '1-тарау: Иллюзия',
    q: 'Харари бойынша, 1990 жылдары «тарих аяқталды» деген қорытындыны қай ойшылдар жариялады?',
    opts: ['Коммунистік идеологтар', 'Либерал демократия жеңіп шықты деп санаған батыстық ойшылдар мен саясаткерлер', 'Ислам теологтары', 'Жапон экономистері'],
    correct: 1,
    exp: 'Фрэнсис Фукуяма сияқты ойшылдар либерал демократия барлық идеологиялық бәсекелесін жеңіп шықты деп тұжырымдады. Харари бұл пікірдің асығыс болғанын дәлелдейді.'
  },
  {
    cat: 'politics', diff: 'easy',
    chapter: '6-тарау: Өркениет',
    q: 'Харари «өркениеттер қақтығысы» теориясына қалай қарайды?',
    opts: [
      'Бұл теорияны толық қолдайды',
      'Шын мәнінде біртұтас жаһандық өркениет қалыптасқан деп есептейді',
      'Тек батыс пен ислам өркениеті ғана шынайы деп санайды',
      'Өркениеттер ешқашан өзара әрекеттеспейді дейді'
    ],
    correct: 1,
    exp: '6-тарауда Харари бүкіл адамзат ортақ экономика, ғылым, заң мен мәдениет бөлетін біртұтас жаһандық өркениетке айналғанын дәлелдейді.'
  },
  {
    cat: 'politics', diff: 'medium',
    chapter: '7-тарау: Ұлтшылдық',
    q: 'Ұлтшылдыққа қатысты Харари қандай пікірде?',
    opts: [
      'Ұлтшылдық жаһандық мәселелерді шеше алады',
      'Климат өзгерісі, ядролық қару, жасанды интеллект сияқты жаһандық мәселелер ұлттық деңгейдегі шешімді қажет етпейді',
      'Ұлттық мүдде мен жаһандық ынтымақтастық қоса жүре алмайды',
      'Ұлтшылдық — ХХІ ғасырдың негізгі күші'
    ],
    correct: 1,
    exp: '7-тарауда «Жаһандық мәселеге жаһандық шешім қажет» деп тұжырымдалады. Ұлтшылдық жаһандық проблемаларды шешуге жеткіліксіз деп дәлелденеді.'
  },
  {
    cat: 'politics', diff: 'medium',
    chapter: '1-тарау: Иллюзия',
    q: 'Харари Ресей ұсынатын «олигархия моделіне» қандай баға береді?',
    opts: [
      'Демократияға балама тиімді жүйе',
      'Байлықтың аз топ қолына шоғырлануы мен медиа монополиясына негізделген, бірақ жаһандық тартымдылығы жоқ модель',
      'Халықтың толық қолдауына ие жүйе',
      'Экономикалық теңдікті қамтамасыз ету жолы'
    ],
    correct: 1,
    exp: 'Харари Ресейдің байлықтың 87%-ы 10% адам қолында шоғырланған олигархиялық жүйесі жаһандық идеология ретінде тартымсыз екенін дәлелдейді.'
  },
  {
    cat: 'politics', diff: 'hard',
    chapter: '12-тарау: Мойынсұну',
    q: 'Харари «ұжымдық адасу» туралы не дейді?',
    opts: [
      'Адамдар жеке адасу қаупіне ғана ұшырайды',
      'Тарихтағы ең зор қателіктер ұжымдық нанымдар мен иллюзиялардан туындаған',
      'Ұжымдық шешімдер жеке шешімдерден әрдайым дұрыс болады',
      'Бір ғана адам тарихты өзгерте алады'
    ],
    correct: 1,
    exp: '12-тарауда Харари нацизм, коммунизм, діни экстремизм сияқты ірі адасулардың ұжымдық сенімдерден туғанын ескертеді. Адам жалғыз адасудан гөрі топпен бірге адасуға бейім.'
  },

  // === TRUTH ===
  {
    cat: 'truth', diff: 'easy',
    chapter: '15-тарау: Надандық',
    q: 'Харари «Бәрін білем» деген сенім туралы не айтады?',
    opts: [
      'Адам баласы шынымен де жан-жақты ойлай алады',
      'Адамдар өздері ойлағаннан әлдеқайда аз нәрсені біледі, ақпарат иллюзиясына берілген',
      'Білімнің артуы автоматты түрде дұрыс шешімге жеткізеді',
      'Интернет адамды шынымен де білімдірек етеді'
    ],
    correct: 1,
    exp: '15-тарауда Харари адамдардың өздері шешім қабылдамаса да, «білемін» деп санайтын иллюзиясын сипаттайды. Шын мәнінде нанымдарымыздың үлкен бөлігі топтық сенімге негізделген.'
  },
  {
    cat: 'truth', diff: 'easy',
    chapter: '17-тарау: Жалған шындық',
    q: 'Харари «жалған ақпарат» туралы не деп тұжырымдайды?',
    opts: [
      'Жалған ақпарат — тек интернет дәуірінің мәселесі',
      'Жалған ақпарат тарихтан бері бар, адамдар шындықтан гөрі тасиятқа сенгіш болып келеді',
      'Мемлекет барлық жалған ақпаратты жоя алады',
      'Ғылым жалған ақпаратты толық жоюға кепілдік береді'
    ],
    correct: 1,
    exp: '17-тарауда Харари жалған ақпараттың жаңа құбылыс еместігін, тарихта діни мифтер мен идеологиялардың ел есінде ұзақ сақталғанын дәлелдейді.'
  },
  {
    cat: 'truth', diff: 'medium',
    chapter: '16-тарау: Әділдік',
    q: 'Харари «жаһандық әділдік» туралы не айтады?',
    opts: [
      'Қазіргі адамдардың моральдық инстинктері жаһандық масштабтағы мәселелерге жауап бере алады',
      'Адамның моральдық интуициясы жаһандық масштабта жұмыс істемейді, себебі ол кішігірім топ үшін эволюциялық қалыптасқан',
      'Жаһандық ұйымдар барлық сұрақтарды шеше алады',
      'Моральдық философия ХХІ ғасырда маңыздылығын жоғалтқан'
    ],
    correct: 1,
    exp: 'Харари адамның моральдық эволюциясы 150 адамдық топ шеңберінде пайда болғанын, ал жаһандық масштабтағы мәселелерді дұрыс бағалауға бейімделмегенімізді түсіндіреді.'
  },
  {
    cat: 'truth', diff: 'medium',
    chapter: '18-тарау: Ғылыми фантастика',
    q: 'Харари ғылыми фантастика туралы не айтады?',
    opts: [
      'Ғылыми фантастика болашақты дәл бейнелейді',
      'Ғылыми фантастиканың болашақ туралы бейнесі шындыққа сәйкес келмеуі мүмкін, бірақ ол қоғамдың қалауын қалыптастырады',
      'Ғылыми фантастиканы назарға алмау керек',
      'Ғылыми фантастика тек балаларға арналған'
    ],
    correct: 1,
    exp: '18-тарауда Харари ғылыми фантастиканың болашақ туралы концепцияларды, жасанды интеллект бейнесін халыққа жеткізетін маңызды мәдени жанр екенін дәлелдейді.'
  },
  {
    cat: 'truth', diff: 'hard',
    chapter: '17-тарау: Жалған шындық',
    q: 'Мифтер мен нарративтердің қоғам үшін функциясы туралы Харари қандай парадоксальды тұжырым жасайды?',
    opts: [
      'Мифтер ешқашан қоғамды ұйыстырмайды',
      'Жалған нанымдар да миллиондаған адамды ұйыстырып, іс-қимылды үйлестіре алады — бұл олардың «пайдалы» жақтары',
      'Тек ғылыми жүйелер ғана қоғамды ұйыстыра алады',
      'Мифтер жеке тұлғаның дамуына ғана қызмет етеді'
    ],
    correct: 1,
    exp: 'Харари «Sapiens» кітабынан бастап дамытқан тезисі: адамдардың ортақ мифтер мен нанымдар негізінде бейтаныс адамдармен ынтымақтаса алуы — homo sapiens-тің бірегей қасиеті.'
  },

  // === MEANING ===
  {
    cat: 'meaning', diff: 'easy',
    chapter: '19-тарау: Білім беру',
    q: 'Харари болашақ білім берудің негізгі міндеті туралы не айтады?',
    opts: [
      'Мазмұнды мүмкіндігінше көп жаттату',
      'Қажет болса қайта оқи алу, жаңа жағдайға бейімделе алу — «4С» дағдыларын дамыту',
      'Тек кәсіптік дағдыларды меңгерту',
      'Алгоритмдерді жасауды үйрету'
    ],
    correct: 1,
    exp: '19-тарауда Харари болашақта тез ескіретін нақты білім мазмұнынан гөрі сын тұрғысынан ойлау, шығармашылық, икемділік (4С дағдылары) маңызды болатынын дәлелдейді.'
  },
  {
    cat: 'meaning', diff: 'easy',
    chapter: '21-тарау: Медитация',
    q: 'Харари неліктен медитацияны ХХІ ғасырдың маңызды дағдысы деп санайды?',
    opts: [
      'Денсаулықты жақсарту мақсатында ғана',
      'Медитация адамға өз санасын, сезімдерін және алгоритм ықпалын анықтауға мүмкіндік береді',
      'Медитация дінге оралудың белгісі',
      'Медитацияның ЖИ-мен ешқандай байланысы жоқ'
    ],
    correct: 1,
    exp: '21-тарауда Харари медитация арқылы адам өз психикасының ішкі жұмысын бақылай алатынын, бұл сыртқы алгоритмдер ықпалынан қорғайтын «ішкі бостандық» екенін жазады.'
  },
  {
    cat: 'meaning', diff: 'medium',
    chapter: '20-тарау: Өмірдің мәні',
    q: 'Харари «өмірдің мәні» туралы ойшыл ретінде қандай тұжырым жасайды?',
    opts: [
      'Өмірдің объективті мәні бар, оны ғылым анықтайды',
      'Мәні – адамдардың жасаған нарративтерінде, алайда бұл нарративтер шындыққа негізделмеуі мүмкін',
      'Діни нанымдар ғана өмірге мән береді',
      'Өмірдің мәнін іздеу бос уақытты өткізу'
    ],
    correct: 1,
    exp: '20-тарауда Харари «өмір – біреудің ойдан шығарған әңгімесі емес» деп тұжырымдайды. Мән адамзат жасаған мәдени нарративтерде жатыр, бірақ оларды ұстану — саналы таңдау.'
  },
  {
    cat: 'meaning', diff: 'medium',
    chapter: '10-тарау: Терроризм',
    q: 'Харари терроризмге берген анықтамасы қандай?',
    opts: [
      'Терроризм — ірі мемлекеттерге тән соғыс стратегиясы',
      'Терроризм — аз шығынмен жауды аса үлкен психологиялық реакцияға итермелейтін әрекет',
      'Терроризм тек дін атынан жасалады',
      'Терроризмнің мемлекет саясатына әсері шамалы'
    ],
    correct: 1,
    exp: '10-тарауда Харари террористің шынайы қаупі емес, мемлекет пен қоғамның одан шамадан тыс үрейленуі нақты зиянға алып келетінін дәлелдейді. «Абдырамаңыз» деп кеңес береді.'
  },
  {
    cat: 'meaning', diff: 'hard',
    chapter: '11-тарау: Соғыс',
    q: 'Харари «роботтар соғысы» туралы қандай этикалық дилемманы сипаттайды?',
    opts: [
      'Роботтар соғысты толық жоя алады',
      'Жауынгер роботтар диктаторлардың халыққа қарсы толық бақылай алатын күшін арттырып, революциялар мен ішкі қарсылықты мүмкін емес ете алады',
      'Роботтар тек демократиялық елдерге пайдалы',
      'Роботтардың соғыс этикасы проблемасы жоқ'
    ],
    correct: 1,
    exp: '11-тарауда Харари роботтардың Ми Лаи сияқты кездейсоқ зорлықтарды азайтса да, сонымен бірге диктаторлардың ешкімнен қорықпай халыққа роботтарды аударта алатынын дәлелдейді.'
  },
  {
    cat: 'meaning', diff: 'hard',
    chapter: '14-тарау: Секуляризм',
    q: 'Харари секуляризмнің басты ерекшелігі туралы не дейді?',
    opts: [
      'Секуляризм дінге қарсы идеология',
      'Секуляризм — догматты нанымдарға емес, шындыққа, жанашырлыққа және адамдық достыққа негізделген дүниетаным',
      'Секуляризм тек батыс мәдениетіне тән',
      'Секуляризм моральдық бос кеңістік туғызады'
    ],
    correct: 1,
    exp: '14-тарауда Харари секуляризмді сенімді дүниетаным ретінде сипаттайды: ол шындықты жариялауға, зардапты мойындауға және адами тектестікке басымдық береді.'
  },

  // EXTRA MIXED
  {
    cat: 'politics', diff: 'easy',
    chapter: '9-тарау: Иммиграция',
    q: 'Харари иммиграция мәселесіне қатысты батыс дебатын қалай сипаттайды?',
    opts: [
      'Иммиграция мүлде мәселесіз жүреді',
      'Иммиграция мен интеграция шарттары мен деңгейі туралы қоғамда шынайы ашық пікірталас болуы керек',
      'Иммиграция тек экономикалық пайда ретінде қарастырылуы керек',
      'Мәдени ерекшеліктер ешқашан интеграцияға кедергі болмайды'
    ],
    correct: 1,
    exp: '9-тарауда Харари иммиграция мәселесін ашық, шынайы талқылауды жақтайды — «асырып жіберу» де, «жаттандылықты мақтан ету» де шешім емес.'
  },
  {
    cat: 'tech', diff: 'medium',
    chapter: '3-тарау: Еркіндік',
    q: 'Палестиналық жұмысшының Facebook мысалы арқылы Харари не дәлелдейді?',
    opts: [
      'Аударма алгоритмдерінің кемшілігі',
      'Алгоритмдік қателіктер нақты адам тағдырына ықпал ете алатынын',
      'Израиль мен Палестина қарым-қатынасы',
      'Әлеуметтік желі зиянсыз'
    ],
    correct: 1,
    exp: '«Қайырлы таң» деген сөз «Құртыңдар оларды» деп аударылып, жұмысшы тұтқынға алынды. Харари алгоритмдік бақылаудың нақты зардаптарын осы мысал арқылы суреттейді.'
  },
  {
    cat: 'truth', diff: 'easy',
    chapter: 'Кіріспе',
    q: 'Харари кітаптың кіріспесінде өзі тарихшы ретінде не істей алатынын қалай анықтайды?',
    opts: [
      'Болашақты дәл болжай алады',
      'Адамдардың түсінік-ұғымын нығайтып, жаһандық пікірталасқа қатыстыра алады',
      'Нақты саяси шешімдер ұсынады',
      'Ғылыми жаңалық ашады'
    ],
    correct: 1,
    exp: 'Кіріспеде Харари «Тарихшы ретінде жұртқа нан бере алмаспын. Есесіне олардың түсінік-ұғымын сәл нығайтып, пікірталасқа қатысуға ынталандыра аламын» деп жазады.'
  },
  {
    cat: 'meaning', diff: 'hard',
    chapter: '13-тарау: Құдай',
    q: 'Харари дін мен ұлтшылдықтың қарым-қатынасы туралы қандай пікір айтады?',
    opts: [
      'Дін ұлтшылдыққа қарама-қарсы',
      'Ұлтшылдық дінді өз мақсаттары үшін пайдаланады, шын мәнінде ұлт мүддесіне қызмет етеді',
      'Діндар мемлекет ұлтшылдықтан жоғары',
      'Дін мен ұлтшылдық ешқашан бірге жүрмейді'
    ],
    correct: 1,
    exp: '13-тарауда Харари «Құдай ұлтқа қызмет етеді» деп тұжырымдайды — діни нанымдар ұлттық саясат мен соғысты қолдау үшін қолданылып келген.'
  }
];

// ===================== GAME STATE =====================
let state = {
  diff: 'all',
  cat: 'all',
  questions: [],
  idx: 0,
  score: 0,
  correct: 0,
  wrong: 0,
  answered: false,
  history: [],
  timer: null,
  timeLeft: 30,
  totalTime: 30
};

function selectDiff(btn) {
  document.querySelectorAll('.diff-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  state.diff = btn.dataset.diff;
}

function selectCat(btn) {
  document.querySelectorAll('.cat-btn').forEach(b => b.classList.remove('selected'));
  btn.classList.add('selected');
  state.cat = btn.dataset.cat;
}

function shuffle(arr) {
  let a = [...arr];
  for (let i = a.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [a[i], a[j]] = [a[j], a[i]];
  }
  return a;
}

function startGame() {
  let pool = allQuestions;
  if (state.cat !== 'all') pool = pool.filter(q => q.cat === state.cat);
  if (state.diff !== 'all') pool = pool.filter(q => q.diff === state.diff);
  if (pool.length === 0) { alert('Таңдалған сүзгі бойынша сұрақ жоқ. Басқа таңдаңыз.'); return; }

  state.questions = shuffle(pool).slice(0, Math.min(15, pool.length));
  state.idx = 0;
  state.score = 0;
  state.correct = 0;
  state.wrong = 0;
  state.history = [];

  showScreen('screen-quiz');
  renderQuestion();
}

function showScreen(id) {
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
}

function renderQuestion() {
  const q = state.questions[state.idx];
  state.answered = false;

  document.getElementById('q-current').textContent = state.idx + 1;
  document.getElementById('q-total').textContent = state.questions.length;
  document.getElementById('live-score').textContent = state.score;

  const pct = (state.idx / state.questions.length) * 100;
  document.getElementById('progress-fill').style.width = pct + '%';

  document.getElementById('q-chapter').textContent = q.chapter;
  const db = document.getElementById('q-diff-badge');
  const diffLabels = { easy: '🟢 Жеңіл', medium: '🟡 Орта', hard: '🔴 Қиын' };
  db.textContent = diffLabels[q.diff];
  db.className = 'q-difficulty ' + q.diff;

  document.getElementById('question-text').textContent = q.q;

  // Shuffle options so correct answer position is random each time
  const indices = q.opts.map((_, i) => i);
  for (let i = indices.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [indices[i], indices[j]] = [indices[j], indices[i]];
  }
  const shuffledOpts = indices.map(i => q.opts[i]);
  const shuffledCorrect = indices.indexOf(q.correct);
  state.shuffledCorrect = shuffledCorrect;
  state.shuffledOpts = shuffledOpts;

  const grid = document.getElementById('options-grid');
  grid.innerHTML = '';
  const letters = ['А', 'Ә', 'Б', 'В'];
  shuffledOpts.forEach((opt, i) => {
    const btn = document.createElement('button');
    btn.className = 'option-btn';
    btn.innerHTML = `<span class="option-letter">${letters[i]}</span><span>${opt}</span>`;
    btn.onclick = () => selectAnswer(i);
    grid.appendChild(btn);
  });

  document.getElementById('feedback').className = 'feedback';
  document.getElementById('next-wrap').className = 'next-btn-wrap';

  startTimer();
}

function startTimer() {
  clearInterval(state.timer);
  state.timeLeft = state.totalTime;
  updateTimer();
  state.timer = setInterval(() => {
    state.timeLeft--;
    updateTimer();
    if (state.timeLeft <= 0) {
      clearInterval(state.timer);
      if (!state.answered) timeUp();
    }
  }, 1000);
}

function updateTimer() {
  const pct = (state.timeLeft / state.totalTime) * 100;
  const fill = document.getElementById('timer-fill');
  const num = document.getElementById('timer-num');
  fill.style.width = pct + '%';
  num.textContent = state.timeLeft;
  fill.className = 'timer-fill';
  num.className = 'timer-num';
  if (state.timeLeft <= 10) { fill.classList.add('warning'); num.classList.add('warning'); }
  if (state.timeLeft <= 5) { fill.classList.add('danger'); num.classList.add('danger'); }
}

function timeUp() {
  state.answered = true;
  const q = state.questions[state.idx];
  const btns = document.querySelectorAll('.option-btn');
  btns.forEach(b => b.disabled = true);
  btns[state.shuffledCorrect].classList.add('correct');
  showFeedback(false, '⏰ Уақыт аяқталды! ' + q.exp);
  state.history.push({ q: q.q, userAns: null, correct: false, correctOpt: state.shuffledOpts[state.shuffledCorrect] });
  state.wrong++;
  document.getElementById('next-wrap').classList.add('show');
}

function selectAnswer(idx) {
  if (state.answered) return;
  clearInterval(state.timer);
  state.answered = true;
  const q = state.questions[state.idx];
  const btns = document.querySelectorAll('.option-btn');
  btns.forEach(b => b.disabled = true);

  const isCorrect = idx === state.shuffledCorrect;
  btns[state.shuffledCorrect].classList.add('correct');
  if (!isCorrect) btns[idx].classList.add('incorrect');

  if (isCorrect) {
    const pts = q.diff === 'easy' ? 1 : q.diff === 'medium' ? 2 : 3;
    state.score += pts;
    state.correct++;
    showFeedback(true, '✅ Дұрыс! ' + q.exp);
  } else {
    state.wrong++;
    showFeedback(false, '❌ Дұрыс жауап: «' + state.shuffledOpts[state.shuffledCorrect] + '». ' + q.exp);
  }

  state.history.push({ q: q.q, userAns: state.shuffledOpts[idx], correct: isCorrect, correctOpt: state.shuffledOpts[state.shuffledCorrect] });
  document.getElementById('live-score').textContent = state.score;
  document.getElementById('next-wrap').classList.add('show');
}

function showFeedback(ok, text) {
  const fb = document.getElementById('feedback');
  fb.className = 'feedback show ' + (ok ? 'correct-fb' : 'incorrect-fb');
  fb.textContent = text;
}

function nextQuestion() {
  state.idx++;
  if (state.idx >= state.questions.length) {
    showResults();
  } else {
    renderQuestion();
  }
}

function showResults() {
  showScreen('screen-results');
  const total = state.questions.length;
  const pct = Math.round((state.correct / total) * 100);

  let icon, title, sub, level, lvlColor;
  if (pct >= 90) {
    icon = '🏆'; title = 'Керемет нәтиже!'; sub = 'Сіз кітапты тереңінен түсінгенсіз!';
    level = '⭐ Білімді оқырман'; lvlColor = '#e8c97a';
  } else if (pct >= 70) {
    icon = '📚'; title = 'Жақсы нәтиже!'; sub = 'Кітаптың негізгі идеяларын жақсы меңгергенсіз.';
    level = '📖 Белсенді оқырман'; lvlColor = '#7acea0';
  } else if (pct >= 50) {
    icon = '🌱'; title = 'Жаман емес!'; sub = 'Кітапты қайта оқысаңыз, нәтиже артады.';
    level = '🌱 Жаңа оқырман'; lvlColor = '#6cb8f0';
  } else {
    icon = '💡'; title = 'Алғашқы қадам!'; sub = '«ХХІ ғасырға – 21 сабақты» оқуды бастаңыз!';
    level = '💡 Оқуды бастаушы'; lvlColor = '#e07a7a';
  }

  document.getElementById('result-icon').textContent = icon;
  document.getElementById('result-title').textContent = title;
  document.getElementById('result-subtitle').textContent = sub;
  document.getElementById('result-score').textContent = state.score;
  document.getElementById('result-total').textContent = '/ ' + (total * 2) + ' балл';
  document.getElementById('stat-correct').textContent = state.correct;
  document.getElementById('stat-wrong').textContent = state.wrong;
  document.getElementById('stat-pct').textContent = pct + '%';
  const lb = document.getElementById('level-badge');
  lb.textContent = level;
  lb.style.background = lvlColor + '22';
  lb.style.color = lvlColor;
  lb.style.border = '1px solid ' + lvlColor + '44';

  const reviewList = document.getElementById('review-list');
  reviewList.innerHTML = '';
  state.history.forEach(h => {
    const div = document.createElement('div');
    div.className = 'review-item ' + (h.correct ? 'r-correct' : 'r-incorrect');
    div.innerHTML = `
      <span class="r-icon">${h.correct ? '✅' : '❌'}</span>
      <div class="r-q">
        <strong>${h.q.length > 80 ? h.q.slice(0, 80) + '...' : h.q}</strong>
        ${!h.correct ? `Дұрыс жауап: <em>${h.correctOpt}</em>` : 'Дұрыс жауап бердіңіз'}
      </div>
    `;
    reviewList.appendChild(div);
  });
}

function restartGame() {
  startGame();
}

function goHome() {
  clearInterval(state.timer);
  showScreen('screen-intro');
}
</script>
</body>
</html>
