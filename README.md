<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Study Hub | مركز المذاكرة</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Arabic:wght@300;400;500;600&family=DM+Mono:wght@300;400;500&family=Noto+Sans+SC:wght@300;400;500&display=swap" rel="stylesheet">

<style>
  :root {
    --bg: #F7F5F0;
    --surface: #FFFFFF;
    --surface2: #F0EDE8;
    --border: #E2DDD6;
    --text: #1A1612;
    --text-muted: #7A7068;
    --accent: #2D6A4F;
    --accent2: #E76F51;
    --accent3: #457B9D;
    --accent-soft: #EAF4EE;
    --tag-bg: #F0EDE8;
    --shadow: 0 2px 12px rgba(0,0,0,0.06);
    --shadow-md: 0 4px 24px rgba(0,0,0,0.10);
    --radius: 12px;
    --radius-sm: 8px;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'IBM Plex Sans Arabic', sans-serif;
    font-size: 15px;
    line-height: 1.7;
    min-height: 100vh;
  }

  /* ─── NAV ─── */
  nav {
    background: var(--surface);
    border-bottom: 1px solid var(--border);
    padding: 0 24px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 60px;
    position: sticky;
    top: 0;
    z-index: 100;
  }
  .nav-logo {
    font-weight: 600;
    font-size: 17px;
    color: var(--accent);
    letter-spacing: -0.3px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .nav-logo span { font-size: 20px; }
  .nav-tabs {
    display: flex;
    gap: 4px;
    list-style: none;
  }
  .nav-tabs li button {
    padding: 6px 14px;
    border: none;
    background: transparent;
    color: var(--text-muted);
    font-family: inherit;
    font-size: 14px;
    cursor: pointer;
    border-radius: var(--radius-sm);
    transition: all 0.2s;
    font-weight: 400;
  }
  .nav-tabs li button:hover { background: var(--surface2); color: var(--text); }
  .nav-tabs li button.active {
    background: var(--accent-soft);
    color: var(--accent);
    font-weight: 500;
  }

  /* ─── PAGES ─── */
  .page { display: none; padding: 32px 24px; max-width: 900px; margin: 0 auto; }
  .page.active { display: block; animation: fadeIn 0.3s ease; }
  @keyframes fadeIn { from { opacity: 0; transform: translateY(6px); } to { opacity: 1; transform: translateY(0); } }

  /* ─── PAGE HEADER ─── */
  .page-header { margin-bottom: 28px; }
  .page-header h1 { font-size: 24px; font-weight: 600; color: var(--text); margin-bottom: 4px; }
  .page-header p { color: var(--text-muted); font-size: 14px; font-weight: 300; }

  /* ─── SUBJECT CARDS ─── */
  .subjects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 16px;
  }
  .subject-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 20px;
    cursor: pointer;
    transition: all 0.2s;
    position: relative;
    overflow: hidden;
  }
  .subject-card:hover {
    border-color: var(--accent);
    box-shadow: var(--shadow-md);
    transform: translateY(-2px);
  }
  .subject-card .card-accent {
    position: absolute;
    top: 0; right: 0;
    width: 4px;
    height: 100%;
    border-radius: 0 var(--radius) var(--radius) 0;
  }
  .subject-card .card-icon { font-size: 26px; margin-bottom: 10px; }
  .subject-card h3 { font-size: 15px; font-weight: 600; margin-bottom: 6px; }
  .subject-card p { font-size: 13px; color: var(--text-muted); font-weight: 300; line-height: 1.6; }
  .card-tag {
    display: inline-block;
    margin-top: 10px;
    padding: 2px 10px;
    background: var(--tag-bg);
    border-radius: 20px;
    font-size: 11px;
    color: var(--text-muted);
    font-weight: 500;
  }

  /* ─── SUBJECT DETAIL ─── */
  .subject-detail { display: none; }
  .subject-detail.active { display: block; animation: fadeIn 0.3s ease; }
  .back-btn {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 7px 14px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius-sm);
    font-family: inherit;
    font-size: 13px;
    cursor: pointer;
    margin-bottom: 24px;
    color: var(--text-muted);
    transition: all 0.2s;
  }
  .back-btn:hover { border-color: var(--accent); color: var(--accent); }

  .detail-header {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 24px;
    margin-bottom: 20px;
    display: flex;
    align-items: flex-start;
    gap: 16px;
  }
  .detail-icon { font-size: 36px; line-height: 1; }
  .detail-header h2 { font-size: 20px; font-weight: 600; margin-bottom: 6px; }
  .detail-header p { color: var(--text-muted); font-size: 14px; font-weight: 300; }

  /* ─── TOPICS ─── */
  .topics-section { margin-bottom: 20px; }
  .section-title {
    font-size: 13px;
    font-weight: 600;
    color: var(--text-muted);
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 12px;
  }
  .topic-item {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius-sm);
    overflow: hidden;
    margin-bottom: 8px;
  }
  .topic-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 14px 16px;
    cursor: pointer;
    transition: background 0.2s;
  }
  .topic-header:hover { background: var(--surface2); }
  .topic-title { font-size: 14px; font-weight: 500; }
  .topic-toggle { color: var(--text-muted); font-size: 12px; transition: transform 0.2s; }
  .topic-item.open .topic-toggle { transform: rotate(180deg); }
  .topic-body {
    display: none;
    padding: 0 16px 16px;
    border-top: 1px solid var(--border);
  }
  .topic-item.open .topic-body { display: block; padding-top: 14px; }
  .topic-body p { font-size: 14px; color: var(--text-muted); margin-bottom: 12px; font-weight: 300; }

  /* ─── VIDEO SECTION ─── */
  .video-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap: 12px;
    margin-top: 12px;
  }
  .video-card {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: var(--radius-sm);
    overflow: hidden;
    text-decoration: none;
    color: inherit;
    transition: all 0.2s;
    display: block;
  }
  .video-card:hover { border-color: var(--accent); box-shadow: var(--shadow); }
  .video-thumb {
    background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
    height: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 28px;
    position: relative;
  }
  .video-thumb::after {
    content: '▶';
    position: absolute;
    font-size: 14px;
    color: white;
    background: rgba(255,255,255,0.15);
    width: 36px;
    height: 36px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .video-info { padding: 10px 12px; }
  .video-title { font-size: 13px; font-weight: 500; margin-bottom: 3px; }
  .video-lang { font-size: 11px; color: var(--text-muted); }

  /* ─── BOOK SECTION ─── */
  .books-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 14px;
    margin-top: 12px;
  }
  .book-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius-sm);
    overflow: hidden;
    transition: all 0.2s;
  }
  .book-card:hover { border-color: var(--accent3); box-shadow: var(--shadow); }
  .book-spine {
    height: 8px;
    width: 100%;
  }
  .book-body { padding: 14px; }
  .book-lang-badge {
    display: inline-block;
    padding: 2px 8px;
    border-radius: 20px;
    font-size: 10px;
    font-weight: 600;
    letter-spacing: 0.5px;
    margin-bottom: 8px;
  }
  .book-lang-badge.ar { background: #FFF3E0; color: #E65100; }
  .book-lang-badge.en { background: #E3F2FD; color: #1565C0; }
  .book-title-ar { font-size: 14px; font-weight: 600; color: var(--text); margin-bottom: 3px; }
  .book-title-en { font-size: 12px; color: var(--text-muted); font-style: italic; margin-bottom: 8px; }
  .book-author { font-size: 12px; color: var(--accent3); margin-bottom: 6px; }
  .book-desc { font-size: 12px; color: var(--text-muted); line-height: 1.6; margin-bottom: 10px; font-weight: 300; }
  .book-actions { display: flex; gap: 8px; flex-wrap: wrap; }
  .book-btn {
    display: inline-flex;
    align-items: center;
    gap: 5px;
    padding: 5px 11px;
    border-radius: 20px;
    font-size: 11px;
    font-weight: 500;
    text-decoration: none;
    transition: all 0.2s;
    border: 1px solid var(--border);
    color: var(--text-muted);
    background: var(--surface2);
    cursor: pointer;
    font-family: inherit;
  }
  .book-btn:hover { border-color: var(--accent); color: var(--accent); background: var(--accent-soft); }
  .book-btn.primary { background: var(--accent); border-color: var(--accent); color: white; }
  .book-btn.primary:hover { background: #245c40; }

  /* ─── RESOURCES TABS ─── */
  .resource-tabs {
    display: flex;
    gap: 6px;
    margin-bottom: 14px;
    border-bottom: 1px solid var(--border);
    padding-bottom: 0;
  }
  .res-tab {
    padding: 8px 14px;
    border: none;
    background: transparent;
    font-family: inherit;
    font-size: 13px;
    cursor: pointer;
    color: var(--text-muted);
    border-bottom: 2px solid transparent;
    margin-bottom: -1px;
    transition: all 0.2s;
    font-weight: 400;
  }
  .res-tab.active { color: var(--accent); border-bottom-color: var(--accent); font-weight: 500; }
  .res-tab:hover:not(.active) { color: var(--text); }
  .res-panel { display: none; }
  .res-panel.active { display: block; animation: fadeIn 0.25s ease; }

  /* ─── TRANSLATOR ─── */
  .translator-wrap {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    overflow: hidden;
  }
  .translator-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 14px 20px;
    border-bottom: 1px solid var(--border);
    background: var(--surface2);
  }
  .lang-selector {
    display: flex;
    gap: 8px;
    align-items: center;
  }
  .lang-btn {
    padding: 5px 12px;
    border: 1px solid var(--border);
    border-radius: 20px;
    background: var(--surface);
    font-family: inherit;
    font-size: 13px;
    cursor: pointer;
    transition: all 0.2s;
    color: var(--text-muted);
  }
  .lang-btn.active {
    background: var(--accent);
    border-color: var(--accent);
    color: white;
  }
  .swap-btn {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 50%;
    width: 32px;
    height: 32px;
    cursor: pointer;
    font-size: 14px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.2s;
  }
  .swap-btn:hover { border-color: var(--accent); color: var(--accent); }

  .translator-body {
    display: grid;
    grid-template-columns: 1fr 1fr;
    min-height: 200px;
  }
  .translator-body textarea {
    padding: 18px 20px;
    border: none;
    outline: none;
    font-family: 'IBM Plex Sans Arabic', sans-serif;
    font-size: 15px;
    resize: none;
    background: transparent;
    color: var(--text);
    line-height: 1.7;
    min-height: 200px;
  }
  .translator-body .output-panel {
    padding: 18px 20px;
    border-right: 1px solid var(--border);
    background: var(--surface2);
    font-size: 15px;
    line-height: 1.7;
    min-height: 200px;
    color: var(--text-muted);
    font-style: italic;
    white-space: pre-wrap;
  }
  .translate-btn {
    display: block;
    width: 100%;
    padding: 14px;
    background: var(--accent);
    color: white;
    border: none;
    font-family: inherit;
    font-size: 15px;
    font-weight: 500;
    cursor: pointer;
    transition: background 0.2s;
  }
  .translate-btn:hover { background: #245c40; }
  .translate-btn:disabled { background: var(--text-muted); cursor: not-allowed; }

  .quick-phrases {
    padding: 16px 20px;
    border-top: 1px solid var(--border);
  }
  .quick-phrases h4 { font-size: 12px; font-weight: 600; color: var(--text-muted); text-transform: uppercase; letter-spacing: 1px; margin-bottom: 10px; }
  .phrases-list { display: flex; flex-wrap: wrap; gap: 8px; }
  .phrase-btn {
    padding: 5px 12px;
    border: 1px solid var(--border);
    border-radius: 20px;
    background: var(--surface);
    font-family: inherit;
    font-size: 13px;
    cursor: pointer;
    transition: all 0.2s;
    color: var(--text);
  }
  .phrase-btn:hover { border-color: var(--accent); color: var(--accent); }

  /* ─── CHINESE ─── */
  .chinese-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
    gap: 12px;
  }
  .char-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 16px;
    text-align: center;
    cursor: pointer;
    transition: all 0.2s;
  }
  .char-card:hover { border-color: var(--accent3); box-shadow: var(--shadow); transform: translateY(-2px); }
  .char-card.flipped { background: var(--accent-soft); border-color: var(--accent); }
  .char-big {
    font-family: 'Noto Sans SC', sans-serif;
    font-size: 42px;
    line-height: 1;
    margin-bottom: 6px;
    color: var(--text);
  }
  .char-pinyin {
    font-family: 'DM Mono', monospace;
    font-size: 13px;
    color: var(--accent3);
    margin-bottom: 4px;
  }
  .char-arabic { font-size: 13px; color: var(--text-muted); }
  .char-english { font-size: 12px; color: var(--accent2); font-style: italic; }

  .categories-tabs {
    display: flex;
    gap: 8px;
    margin-bottom: 20px;
    flex-wrap: wrap;
  }
  .cat-btn {
    padding: 6px 14px;
    border: 1px solid var(--border);
    border-radius: 20px;
    background: var(--surface);
    font-family: inherit;
    font-size: 13px;
    cursor: pointer;
    transition: all 0.2s;
    color: var(--text-muted);
  }
  .cat-btn.active { background: var(--accent); border-color: var(--accent); color: white; }
  .cat-btn:hover:not(.active) { border-color: var(--accent); color: var(--accent); }

  /* ─── QUIZ ─── */
  .quiz-setup {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 28px;
    text-align: center;
    max-width: 500px;
    margin: 0 auto;
  }
  .quiz-setup h2 { font-size: 20px; margin-bottom: 8px; }
  .quiz-setup p { color: var(--text-muted); font-size: 14px; margin-bottom: 24px; font-weight: 300; }
  .quiz-options {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin-bottom: 20px;
    text-align: right;
  }
  .quiz-option {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: var(--radius-sm);
    padding: 12px 16px;
    cursor: pointer;
    transition: all 0.2s;
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 14px;
  }
  .quiz-option:hover { border-color: var(--accent); }
  .quiz-option.selected { background: var(--accent-soft); border-color: var(--accent); color: var(--accent); font-weight: 500; }
  .start-btn {
    background: var(--accent);
    color: white;
    border: none;
    border-radius: var(--radius-sm);
    padding: 12px 28px;
    font-family: inherit;
    font-size: 15px;
    font-weight: 500;
    cursor: pointer;
    transition: background 0.2s;
  }
  .start-btn:hover { background: #245c40; }

  .quiz-question-wrap {
    display: none;
    max-width: 600px;
    margin: 0 auto;
  }
  .quiz-question-wrap.active { display: block; animation: fadeIn 0.3s ease; }
  .quiz-progress {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 20px;
  }
  .progress-bar {
    flex: 1;
    height: 4px;
    background: var(--border);
    border-radius: 2px;
    margin: 0 12px;
    overflow: hidden;
  }
  .progress-fill {
    height: 100%;
    background: var(--accent);
    border-radius: 2px;
    transition: width 0.4s ease;
  }
  .quiz-num { font-size: 13px; color: var(--text-muted); font-family: 'DM Mono', monospace; }

  .question-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 28px;
    margin-bottom: 16px;
    text-align: center;
  }
  .question-card .q-label { font-size: 12px; color: var(--text-muted); text-transform: uppercase; letter-spacing: 1px; margin-bottom: 12px; }
  .question-card .q-text { font-size: 22px; font-weight: 600; }

  .answers-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
  }
  .answer-btn {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius-sm);
    padding: 14px 16px;
    font-family: inherit;
    font-size: 14px;
    cursor: pointer;
    transition: all 0.2s;
    text-align: center;
  }
  .answer-btn:hover:not(:disabled) { border-color: var(--accent3); color: var(--accent3); }
  .answer-btn.correct { background: #EAF4EE; border-color: var(--accent); color: var(--accent); font-weight: 600; }
  .answer-btn.wrong { background: #FEF0EC; border-color: var(--accent2); color: var(--accent2); }

  .quiz-result {
    display: none;
    text-align: center;
    max-width: 500px;
    margin: 0 auto;
  }
  .quiz-result.active { display: block; animation: fadeIn 0.3s ease; }
  .result-score {
    font-family: 'DM Mono', monospace;
    font-size: 64px;
    font-weight: 500;
    color: var(--accent);
    margin: 20px 0 8px;
  }
  .result-score span { font-size: 28px; color: var(--text-muted); }
  .retry-btn {
    margin-top: 20px;
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: var(--radius-sm);
    padding: 10px 24px;
    font-family: inherit;
    font-size: 14px;
    cursor: pointer;
    transition: all 0.2s;
  }
  .retry-btn:hover { border-color: var(--accent); color: var(--accent); }

  /* ─── RESPONSIVE ─── */
  @media (max-width: 600px) {
    .translator-body { grid-template-columns: 1fr; }
    .translator-body .output-panel { border-right: none; border-top: 1px solid var(--border); }
    nav { padding: 0 14px; }
    .nav-tabs li button { padding: 6px 10px; font-size: 13px; }
    .page { padding: 20px 14px; }
    .answers-grid { grid-template-columns: 1fr; }
    .quiz-options { grid-template-columns: 1fr; }
  }

  /* ─── LOADING ─── */
  .loading { display: inline-block; width: 14px; height: 14px; border: 2px solid rgba(255,255,255,0.3); border-top-color: white; border-radius: 50%; animation: spin 0.6s linear infinite; vertical-align: middle; margin-left: 8px; }
  @keyframes spin { to { transform: rotate(360deg); } }

  /* ─── NOTICE ─── */
  .notice {
    background: #FFF8F0;
    border: 1px solid #FFD199;
    border-radius: var(--radius-sm);
    padding: 10px 14px;
    font-size: 13px;
    color: #8B5E00;
    margin-bottom: 16px;
  }

  .subjects-list-view { display: none; }
  .subjects-grid-view { display: grid; }
</style>
</head>
<body>

<nav>
  <div class="nav-logo"><span>📚</span> Study Hub</div>
  <ul class="nav-tabs">
    <li><button class="active" onclick="showPage('subjects')">المواد</button></li>
    <li><button onclick="showPage('translator')">المترجم</button></li>
    <li><button onclick="showPage('chinese')">الصينية 中文</button></li>
    <li><button onclick="showPage('quiz')">الاختبارات</button></li>
  </ul>
</nav>

<!-- ═══════════════ SUBJECTS PAGE ═══════════════ -->
<div id="page-subjects" class="page active">

  <div id="subjects-grid-view">
    <div class="page-header">
      <h1>مواد هذا الترم</h1>
      <p>اختاري مادة لتشوفي شرح وفيديوهات</p>
    </div>
    <div class="subjects-grid">

      <div class="subject-card" onclick="openSubject('comparative')">
        <div class="card-accent" style="background:#2D6A4F"></div>
        <div class="card-icon">📖</div>
        <h3>الأدب المقارن</h3>
        <p>Comparative Literature — مقارنة النصوص من ثقافات مختلفة</p>
        <span class="card-tag">أدب وثقافة</span>
      </div>

      <div class="subject-card" onclick="openSubject('academic')">
        <div class="card-accent" style="background:#457B9D"></div>
        <div class="card-icon">✍️</div>
        <h3>القراءة والكتابة الأكاديمية</h3>
        <p>Academic Reading & Writing 2 — كتابة المقالات وتحليل النصوص</p>
        <span class="card-tag">مهارات أكاديمية</span>
      </div>

      <div class="subject-card" onclick="openSubject('phonetics')">
        <div class="card-accent" style="background:#E76F51"></div>
        <div class="card-icon">🔊</div>
        <h3>الصوتيات وعلم الأصوات</h3>
        <p>Phonetics & Phonology — تحليل أصوات اللغة الإنجليزية</p>
        <span class="card-tag">لغويات</span>
      </div>

      <div class="subject-card" onclick="openSubject('digital')">
        <div class="card-accent" style="background:#9B5DE5"></div>
        <div class="card-icon">💻</div>
        <h3>أساسيات التكنولوجيا الرقمية</h3>
        <p>Foundations of Digital Technology — أدوات الترجمة والتكنولوجيا</p>
        <span class="card-tag">تقنية</span>
      </div>

      <div class="subject-card" onclick="openSubject('arabic')">
        <div class="card-accent" style="background:#F4A261"></div>
        <div class="card-icon">📝</div>
        <h3>العربية — أساسيات الكتابة والقواميس</h3>
        <p>Arabic Writing & Dictionary Skills — الكتابة الصحيحة واستخدام القواميس</p>
        <span class="card-tag">لغة عربية</span>
      </div>

      <div class="subject-card" onclick="openSubject('media')">
        <div class="card-accent" style="background:#2D6A4F"></div>
        <div class="card-icon">📰</div>
        <h3>الترجمة الإعلامية والصحفية</h3>
        <p>Media & Journalistic Translation — ترجمة الأخبار والمقالات</p>
        <span class="card-tag">ترجمة</span>
      </div>

      <div class="subject-card" onclick="openSubject('scientific')">
        <div class="card-accent" style="background:#457B9D"></div>
        <div class="card-icon">🔬</div>
        <h3>الترجمة العلمية</h3>
        <p>Scientific Translation — ترجمة الأبحاث والنصوص العلمية</p>
        <span class="card-tag">ترجمة متخصصة</span>
      </div>

    </div>
  </div>

  <!-- Subject Details -->
  <div id="subject-detail" class="subject-detail">
    <button class="back-btn" onclick="closeSubject()">← العودة للمواد</button>
    <div id="detail-content"></div>
  </div>

</div>

<!-- ═══════════════ TRANSLATOR PAGE ═══════════════ -->
<div id="page-translator" class="page">
  <div class="page-header">
    <h1>المترجم</h1>
    <p>ترجمة بين العربية والإنجليزية والصينية</p>
  </div>

  <div class="notice">💡 المترجم يستخدم Claude AI — مدعوم بالذكاء الاصطناعي لترجمة دقيقة للمصطلحات الأكاديمية والترجمة</div>

  <div class="translator-wrap">
    <div class="translator-header">
      <div class="lang-selector">
        <button class="lang-btn active" id="from-ar" onclick="setFromLang('ar')">عربي</button>
        <button class="lang-btn" id="from-en" onclick="setFromLang('en')">English</button>
        <button class="lang-btn" id="from-zh" onclick="setFromLang('zh')">中文</button>
      </div>
      <button class="swap-btn" onclick="swapLangs()" title="عكس الترجمة">⇄</button>
      <div class="lang-selector">
        <button class="lang-btn" id="to-en" onclick="setToLang('en')">English</button>
        <button class="lang-btn active" id="to-zh" onclick="setToLang('zh')">中文</button>
        <button class="lang-btn" id="to-ar" onclick="setToLang('ar')">عربي</button>
      </div>
    </div>

    <div class="translator-body">
      <div class="output-panel" id="translation-output">الترجمة ستظهر هنا...</div>
      <textarea id="translation-input" placeholder="اكتبي النص هنا..." oninput="clearOutput()"></textarea>
    </div>

    <button class="translate-btn" id="translate-btn" onclick="doTranslate()">
      ترجم الآن
    </button>

    <div class="quick-phrases">
      <h4>جمل سريعة للترجمة</h4>
      <div class="phrases-list">
        <button class="phrase-btn" onclick="usePhrase('مصطلح أكاديمي')">مصطلح أكاديمي</button>
        <button class="phrase-btn" onclick="usePhrase('نص صحفي')">نص صحفي</button>
        <button class="phrase-btn" onclick="usePhrase('مقتطف أدبي')">مقتطف أدبي</button>
        <button class="phrase-btn" onclick="usePhrase('جملة علمية')">جملة علمية</button>
        <button class="phrase-btn" onclick="usePhrase('تحية باللغة الصينية')">تحية صينية</button>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════ CHINESE PAGE ═══════════════ -->
<div id="page-chinese" class="page">
  <div class="page-header">
    <h1>تعلمي الصينية 学中文</h1>
    <p>اضغطي على أي حرف لتري الترجمة الكاملة</p>
  </div>

  <div class="categories-tabs" id="chinese-cats">
    <button class="cat-btn active" onclick="showChinese('greetings')">تحيات 问候</button>
    <button class="cat-btn" onclick="showChinese('numbers')">أرقام 数字</button>
    <button class="cat-btn" onclick="showChinese('academic')">أكاديمي 学术</button>
    <button class="cat-btn" onclick="showChinese('translation')">ترجمة 翻译</button>
    <button class="cat-btn" onclick="showChinese('daily')">يومي 日常</button>
  </div>

  <div id="chinese-cards" class="chinese-grid"></div>
</div>

<!-- ═══════════════ QUIZ PAGE ═══════════════ -->
<div id="page-quiz" class="page">
  <div class="page-header">
    <h1>الاختبارات</h1>
    <p>اختبري نفسك في المواد المختلفة</p>
  </div>

  <div id="quiz-setup" class="quiz-setup">
    <h2>اختاري المادة</h2>
    <p>ابدئي باختبار قصير 10 أسئلة</p>
    <div class="quiz-options" id="quiz-options">
      <div class="quiz-option selected" data-subject="phonetics" onclick="selectQuizSubject(this)">
        <span>🔊</span> الصوتيات
      </div>
      <div class="quiz-option" data-subject="media" onclick="selectQuizSubject(this)">
        <span>📰</span> الترجمة الإعلامية
      </div>
      <div class="quiz-option" data-subject="comparative" onclick="selectQuizSubject(this)">
        <span>📖</span> الأدب المقارن
      </div>
      <div class="quiz-option" data-subject="chinese" onclick="selectQuizSubject(this)">
        <span>🀄</span> الصينية
      </div>
    </div>
    <button class="start-btn" onclick="startQuiz()">ابدئي الاختبار ←</button>
  </div>

  <div id="quiz-question-wrap" class="quiz-question-wrap">
    <div class="quiz-progress">
      <span class="quiz-num" id="q-current">1</span>
      <div class="progress-bar"><div class="progress-fill" id="q-progress" style="width:10%"></div></div>
      <span class="quiz-num" id="q-total">/ 10</span>
    </div>
    <div class="question-card">
      <div class="q-label" id="q-subject-label">سؤال</div>
      <div class="q-text" id="q-text">...</div>
    </div>
    <div class="answers-grid" id="q-answers"></div>
  </div>

  <div id="quiz-result" class="quiz-result">
    <div style="font-size:48px">🎉</div>
    <h2>انتهى الاختبار!</h2>
    <div class="result-score"><span id="r-score">0</span><span> / 10</span></div>
    <p id="r-message" style="color:var(--text-muted); font-size:14px;"></p>
    <button class="retry-btn" onclick="resetQuiz()">حاولي مرة تانية</button>
    <button class="retry-btn" onclick="showPage('quiz')" style="margin-right:8px">اختاري مادة تانية</button>
  </div>
</div>

<script>
// ══════════════════════════════════════════
// NAVIGATION
// ══════════════════════════════════════════
function showPage(id) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.nav-tabs button').forEach(b => b.classList.remove('active'));
  document.getElementById('page-' + id).classList.add('active');
  const idx = ['subjects','translator','chinese','quiz'].indexOf(id);
  document.querySelectorAll('.nav-tabs button')[idx].classList.add('active');
  if (id === 'chinese') showChinese('greetings');
  if (id === 'quiz') resetQuiz();
}

// ══════════════════════════════════════════
// SUBJECTS DATA
// ══════════════════════════════════════════
const subjects = {
  comparative: {
    icon: '📖', color: '#2D6A4F',
    name: 'الأدب المقارن', nameEn: 'Comparative Literature',
    desc: 'دراسة وتحليل النصوص الأدبية من ثقافات متعددة، مع المقارنة في الموضوع والأسلوب والتأثير.',
    topics: [
      { title: 'مقدمة في الأدب المقارن', body: 'الأدب المقارن هو دراسة الأعمال الأدبية من ثقافات ولغات مختلفة، بهدف إيجاد أوجه الشبه والاختلاف. يشمل: الموضوعات المشتركة، الأسلوب الأدبي، التأثيرات الثقافية عبر الحضارات.', videos: [{title: 'Intro to Comparative Literature', lang: 'English', url: 'https://www.youtube.com/results?search_query=introduction+comparative+literature'}, {title: 'مقدمة الأدب المقارن', lang: 'عربي', url: 'https://www.youtube.com/results?search_query=الأدب+المقارن+مقدمة'}] },
      { title: 'تحليل النصوص الأدبية', body: 'تعلمي كيف تحللي نصاً أدبياً من حيث: الشخصيات، الحبكة، الزمان والمكان، الرمزية، والأسلوب. استخدمي نموذج PEEL في الكتابة التحليلية.', videos: [{title: 'Literary Analysis Skills', lang: 'English', url: 'https://www.youtube.com/results?search_query=literary+analysis+how+to'}] },
      { title: 'التأثير الثقافي في الأدب', body: 'كيف تؤثر الثقافة على الكتابة الأدبية؟ ندرس الأدب من خلفيات: أوروبية، عربية، آسيوية، وأفريقية ونوازن بينها.', videos: [{title: 'Cultural Context in Literature', lang: 'English', url: 'https://www.youtube.com/results?search_query=cultural+context+in+literature+analysis'}] }
    ],
    books: [
      { titleAr: 'الأدب المقارن — دراسة منهجية', titleEn: 'Comparative Literature: A Critical Introduction', author: 'Susan Bassnett', authorAr: 'سوزان باسنيت', lang: 'en', color: '#2D6A4F', descAr: 'مرجع أساسي في الأدب المقارن يغطي المناهج والنظريات الحديثة', descEn: 'A fundamental reference covering modern comparative methods and theories', download: 'https://archive.org/search?query=comparative+literature+bassnett', preview: 'https://www.goodreads.com/book/show/591000' },
      { titleAr: 'في الأدب المقارن', titleEn: 'Fi al-Adab al-Muqaran', author: 'محمد غنيمي هلال', authorAr: 'د. محمد غنيمي هلال', lang: 'ar', color: '#E76F51', descAr: 'أشهر مرجع عربي في الأدب المقارن، يشرح النظرية والتطبيق بالعربية', descEn: 'The most famous Arabic reference in comparative literature', download: 'https://archive.org/search?query=محمد+غنيمي+هلال+الأدب+المقارن', preview: 'https://www.neelwafurat.com/itempage.aspx?id=egb107390' },
      { titleAr: 'نظرية الأدب', titleEn: 'Theory of Literature', author: 'René Wellek & Austin Warren', authorAr: 'رينيه ويليك وأوستن وارين', lang: 'en', color: '#457B9D', descAr: 'من أهم كتب نظرية الأدب في القرن العشرين', descEn: 'One of the most important books of 20th-century literary theory', download: 'https://archive.org/search?query=theory+of+literature+wellek+warren', preview: 'https://www.goodreads.com/book/show/71274' },
    ]
  },
  academic: {
    icon: '✍️', color: '#457B9D',
    name: 'القراءة والكتابة الأكاديمية', nameEn: 'Academic Reading & Writing 2',
    desc: 'تطوير مهارات الكتابة الأكاديمية من مقالات وتحليل نصوص وتوثيق مصادر.',
    topics: [
      { title: 'كيفية كتابة المقالة الأكاديمية', body: 'المقالة الأكاديمية تتكون من: مقدمة (Introduction) — جسم المقالة (Body Paragraphs) — خاتمة (Conclusion). كل فقرة تبدأ بـ Topic Sentence ثم الشرح والأمثلة والتعليق.', videos: [{title: 'How to Write an Academic Essay', lang: 'English', url: 'https://www.youtube.com/results?search_query=how+to+write+academic+essay+beginners'}, {title: 'Academic Writing Tips', lang: 'English', url: 'https://www.youtube.com/results?search_query=academic+writing+tips+university'}] },
      { title: 'القراءة النقدية', body: 'القراءة النقدية تعني: تحليل الحجج، تقييم الأدلة، تمييز الرأي من الحقيقة، والتساؤل عن المصادر.', videos: [{title: 'Critical Reading Strategies', lang: 'English', url: 'https://www.youtube.com/results?search_query=critical+reading+strategies+academic'}] },
      { title: 'التوثيق والمراجع (APA/MLA)', body: 'طرق التوثيق الأكاديمي: APA يُستخدم في العلوم الاجتماعية، MLA في الآداب واللغويات. تعلمي كيفية توثيق: كتب، مقالات، مواقع إلكترونية.', videos: [{title: 'APA Citation Tutorial', lang: 'English', url: 'https://www.youtube.com/results?search_query=APA+citation+tutorial+2024'}, {title: 'MLA Format Guide', lang: 'English', url: 'https://www.youtube.com/results?search_query=MLA+format+guide'}] }
    ],
    books: [
      { titleAr: 'الكتابة الأكاديمية من الفقرة إلى البحث', titleEn: 'Academic Writing: From Paragraph to Essay', author: 'Dorothy E. Zemach', authorAr: 'دوروثي زيماك', lang: 'en', color: '#457B9D', descAr: 'كتاب شامل لتعلم الكتابة الأكاديمية من الفقرة وحتى البحث الكامل', descEn: 'Comprehensive guide from paragraph writing to full research papers', download: 'https://archive.org/search?query=academic+writing+paragraph+to+essay+zemach', preview: 'https://www.goodreads.com/book/show/2303875' },
      { titleAr: 'مهارات الكتابة الأكاديمية', titleEn: 'Academic Writing Skills', author: 'Peter Chin et al.', authorAr: 'بيتر تشين وآخرون', lang: 'en', color: '#2D6A4F', descAr: 'يغطي مهارات القراءة والكتابة النقدية والتوثيق', descEn: 'Covers critical reading, writing and documentation skills', download: 'https://archive.org/search?query=academic+writing+skills+cambridge', preview: 'https://www.cambridge.org/core' },
      { titleAr: 'الكتابة الوظيفية والإبداعية', titleEn: 'Arabic Academic & Functional Writing', author: 'د. علي الحمد', authorAr: 'د. علي الحمد', lang: 'ar', color: '#E76F51', descAr: 'مرجع عربي يشرح أسس الكتابة الوظيفية والأكاديمية باللغة العربية', descEn: 'Arabic reference explaining functional and academic writing fundamentals', download: 'https://archive.org/search?query=الكتابة+الأكاديمية+عربي', preview: 'https://www.neelwafurat.com' },
    ]
  },
  phonetics: {
    icon: '🔊', color: '#E76F51',
    name: 'الصوتيات وعلم الأصوات', nameEn: 'Phonetics & Phonology',
    desc: 'تحليل أصوات اللغة الإنجليزية وفهم نظام النطق والحروف الصوتية.',
    topics: [
      { title: 'الأبجدية الصوتية الدولية IPA', body: 'الـ IPA هو نظام رموز يمثل كل صوت في أي لغة. يحتوي الإنجليزية على 44 صوتاً تقريباً. تعلمي رموزها مثل: /æ/ في cat، /iː/ في see، /ʌ/ في but.', videos: [{title: 'IPA for English - Full Guide', lang: 'English', url: 'https://www.youtube.com/results?search_query=IPA+International+Phonetic+Alphabet+English+full'}, {title: 'شرح IPA عربي', lang: 'عربي', url: 'https://www.youtube.com/results?search_query=الأبجدية+الصوتية+الدولية+شرح'}] },
      { title: 'الحروف الساكنة والمتحركة', body: 'الحروف المتحركة (Vowels): /iː/ /ɪ/ /e/ /æ/ /ɑː/ /ɒ/ /ɔː/ /ʊ/ /uː/ /ʌ/ /ɜː/ /ə/. الحروف الساكنة (Consonants): /p/ /b/ /t/ /d/ /k/ /g/ /f/ /v/ /s/ /z/...', videos: [{title: 'English Vowel Sounds', lang: 'English', url: 'https://www.youtube.com/results?search_query=English+vowel+sounds+IPA+tutorial'}, {title: 'English Consonants', lang: 'English', url: 'https://www.youtube.com/results?search_query=English+consonant+sounds+pronunciation'}] },
      { title: 'الفونيمات والأللوفونات', body: 'الفونيم هو أصغر وحدة صوتية تميز بين كلمتين. الأللوفون هو تغيير غير مميز للفونيم نفسه. مثال: /p/ في "pin" و"spin" — نطقان مختلفان لنفس الفونيم.', videos: [{title: 'Phonemes vs Allophones', lang: 'English', url: 'https://www.youtube.com/results?search_query=phonemes+vs+allophones+linguistics'}] }
    ],
    books: [
      { titleAr: 'علم الأصوات', titleEn: 'Phonetics: The Science of Speech', author: 'Martin J. Ball & Joan Rahilly', authorAr: 'مارتن بول وجون راهيلي', lang: 'en', color: '#E76F51', descAr: 'مرجع شامل في علم الأصوات يغطي النطق والتحليل الصوتي', descEn: 'Comprehensive reference in phonetics covering articulation and acoustic analysis', download: 'https://archive.org/search?query=phonetics+science+of+speech', preview: 'https://www.goodreads.com/book/show/1802919' },
      { titleAr: 'مقدمة في اللسانيات', titleEn: 'An Introduction to Language', author: 'Victoria Fromkin et al.', authorAr: 'فيكتوريا فرومكين وآخرون', lang: 'en', color: '#457B9D', descAr: 'الكتاب الأشهر لتعلم اللسانيات والصوتيات للمبتدئين', descEn: 'The most popular textbook for learning linguistics and phonetics for beginners', download: 'https://archive.org/search?query=introduction+to+language+fromkin', preview: 'https://www.goodreads.com/book/show/466239' },
      { titleAr: 'علم الأصوات العربي', titleEn: 'Arabic Phonetics & Phonology', author: 'د. كمال بشر', authorAr: 'د. كمال بشر', lang: 'ar', color: '#2D6A4F', descAr: 'مرجع عربي متخصص يشرح علم الأصوات بالتطبيق على اللغة العربية والإنجليزية', descEn: 'Arabic specialized reference explaining phonetics applied to Arabic and English', download: 'https://archive.org/search?query=علم+الأصوات+كمال+بشر', preview: 'https://www.neelwafurat.com/itempage.aspx?id=egb39020' },
    ]
  },
  digital: {
    icon: '💻', color: '#9B5DE5',
    name: 'أساسيات التكنولوجيا الرقمية', nameEn: 'Foundations of Digital Technology',
    desc: 'أدوات الترجمة بمساعدة الحاسوب CAT Tools، وبرامج التحرير والنشر.',
    topics: [
      { title: 'أدوات الترجمة CAT Tools', body: 'أشهر أدوات الترجمة بمساعدة الحاسوب: SDL Trados Studio، memoQ، OmegaT (مجانية)، Wordfast. تساعدك في بناء ذاكرة ترجمة وقواعد مصطلحات.', videos: [{title: 'CAT Tools Introduction', lang: 'English', url: 'https://www.youtube.com/results?search_query=CAT+tools+computer+assisted+translation+introduction'}, {title: 'OmegaT Tutorial', lang: 'English', url: 'https://www.youtube.com/results?search_query=OmegaT+tutorial+beginners'}] },
      { title: 'برامج التحرير والـ DTP', body: 'Desktop Publishing للمترجمين: Adobe InDesign، Microsoft Word Styles، PDF editing. مهمة جداً للترجمة المتخصصة في المجلات والكتب.', videos: [{title: 'DTP for Translators', lang: 'English', url: 'https://www.youtube.com/results?search_query=desktop+publishing+for+translators'}] },
      { title: 'الذكاء الاصطناعي والترجمة', body: 'أدوات الذكاء الاصطناعي في الترجمة: DeepL، Google Translate، ChatGPT. كيف تستخدميها كمساعدة لا كبديل؟ أهمية post-editing — تحرير الترجمة الآلية.', videos: [{title: 'AI Translation Tools 2024', lang: 'English', url: 'https://www.youtube.com/results?search_query=AI+translation+tools+translators+2024'}] }
    ],
    books: [
      { titleAr: 'الترجمة بمساعدة الحاسوب', titleEn: 'Computer-Aided Translation Technology', author: 'Déirdre Bowker & Jennifer Pearson', authorAr: 'بوكر وبيرسون', lang: 'en', color: '#9B5DE5', descAr: 'مرجع أكاديمي شامل لتكنولوجيا الترجمة وأدوات CAT', descEn: 'Comprehensive academic reference for translation technology and CAT tools', download: 'https://archive.org/search?query=computer+aided+translation+technology+bowker', preview: 'https://www.goodreads.com/book/show/1427349' },
      { titleAr: 'الترجمة الآلية ومعالجة اللغات', titleEn: 'Machine Translation', author: 'Thierry Poibeau', authorAr: 'تيري بويبو', lang: 'en', color: '#457B9D', descAr: 'شرح الترجمة الآلية وكيف تعمل أنظمة الذكاء الاصطناعي في الترجمة', descEn: 'Explains machine translation and how AI systems work in translation', download: 'https://archive.org/search?query=machine+translation+poibeau+MIT', preview: 'https://mitpress.mit.edu/books/machine-translation' },
      { titleAr: 'تكنولوجيا الترجمة والترجمة الرقمية', titleEn: 'Translation Technology & Digital Tools Guide', author: 'SDL / Trados', authorAr: 'SDL ترادوس', lang: 'en', color: '#2D6A4F', descAr: 'الدليل الرسمي لأشهر برنامج ترجمة في العالم SDL Trados', descEn: 'Official guide for the world\'s most popular translation software SDL Trados', download: 'https://docs.rws.com/trados', preview: 'https://www.trados.com/learning/' },
    ]
  },
  arabic: {
    icon: '📝', color: '#F4A261',
    name: 'العربية — الكتابة والقواميس', nameEn: 'Arabic Writing & Dictionary Skills',
    desc: 'تقوية مهارات الكتابة العربية الصحيحة والاحترافية في استخدام القواميس.',
    topics: [
      { title: 'أسس الكتابة العربية الصحيحة', body: 'أهم قواعد الكتابة: الهمزة (أ/إ/آ/ء/ؤ/ئ)، التاء المربوطة والمبسوطة، الفصل بين كلمتين مثل "بعض" و"البعض"، علامات الترقيم العربية.', videos: [{title: 'قواعد الإملاء العربي', lang: 'عربي', url: 'https://www.youtube.com/results?search_query=قواعد+الإملاء+العربي+شرح'}, {title: 'الكتابة الاحترافية عربي', lang: 'عربي', url: 'https://www.youtube.com/results?search_query=مهارات+الكتابة+العربية+الاحترافية'}] },
      { title: 'استخدام القواميس احترافياً', body: 'أنواع القواميس: أحادية اللغة (عربي-عربي)، ثنائية (عربي-إنجليزي)، متخصصة. أهم القواميس: لسان العرب، المعجم الوسيط، أكسفورد عربي-إنجليزي، المورد.', videos: [{title: 'استخدام القواميس في الترجمة', lang: 'عربي', url: 'https://www.youtube.com/results?search_query=استخدام+المعجم+في+الترجمة'}] },
      { title: 'المصطلحات التخصصية', body: 'كيفية بناء قاموسك الخاص بالمصطلحات المتخصصة في: الطب، القانون، الاقتصاد، التقنية. استخدام أدوات مثل IATE وGlossarissimo.', videos: [{title: 'Terminology Management', lang: 'English', url: 'https://www.youtube.com/results?search_query=terminology+management+for+translators'}] }
    ],
    books: [
      { titleAr: 'لسان العرب', titleEn: 'Lisan al-Arab (Arabic Dictionary)', author: 'ابن منظور', authorAr: 'ابن منظور', lang: 'ar', color: '#F4A261', descAr: 'أعظم وأشمل قاموس في تاريخ اللغة العربية — لا غنى عنه لكل طالب لغة', descEn: 'The greatest and most comprehensive dictionary in Arabic language history', download: 'https://archive.org/search?query=لسان+العرب+ابن+منظور', preview: 'https://www.almaany.com/ar/dict/ar-ar/لسان+العرب/' },
      { titleAr: 'المعجم الوسيط', titleEn: 'Al-Mu\'jam Al-Waseet', author: 'مجمع اللغة العربية', authorAr: 'مجمع اللغة العربية بالقاهرة', lang: 'ar', color: '#2D6A4F', descAr: 'المرجع الأكاديمي الرسمي للغة العربية الفصحى المعاصرة', descEn: 'Official academic reference for Modern Standard Arabic', download: 'https://archive.org/search?query=المعجم+الوسيط+مجمع+اللغة+العربية', preview: 'https://www.arabicstudies.org' },
      { titleAr: 'قاموس المورد', titleEn: 'Al-Mawrid: Arabic-English Dictionary', author: 'منير البعلبكي', authorAr: 'منير البعلبكي', lang: 'ar', color: '#457B9D', descAr: 'أشهر قاموس عربي-إنجليزي معاصر للمترجمين والطلاب', descEn: 'The most famous modern Arabic-English dictionary for translators and students', download: 'https://archive.org/search?query=المورد+البعلبكي+عربي+إنجليزي', preview: 'https://www.neelwafurat.com/itempage.aspx?id=egb20671' },
    ]
  },
  media: {
    icon: '📰', color: '#2D6A4F',
    name: 'الترجمة الإعلامية والصحفية', nameEn: 'Media & Journalistic Translation',
    desc: 'ترجمة الأخبار والمقالات الصحفية مع مراعاة الأسلوب الإعلامي والدقة.',
    topics: [
      { title: 'خصائص الأسلوب الصحفي', body: 'الكتابة الصحفية تتميز بـ: الجملة القصيرة، الأسلوب المباشر، الهرم المقلوب (الأهم أولاً)، العنوان الجاذب. في الترجمة احترفي هذه الخصائص ولا تحرفي المعنى.', videos: [{title: 'Journalistic Writing Style', lang: 'English', url: 'https://www.youtube.com/results?search_query=journalistic+writing+style+inverted+pyramid'}, {title: 'الترجمة الصحفية', lang: 'عربي', url: 'https://www.youtube.com/results?search_query=الترجمة+الصحفية+والإعلامية+شرح'}] },
      { title: 'ترجمة الأخبار والتقارير', body: 'تحديات ترجمة الأخبار: السرعة، المصطلحات السياسية، اختلاف الثقافة الإعلامية. مصادر مفيدة: BBC Arabic، Aljazeera English، Reuters بالعربي.', videos: [{title: 'News Translation Challenges', lang: 'English', url: 'https://www.youtube.com/results?search_query=news+translation+challenges+Arabic'}, {title: 'Media Translation Practice', lang: 'English', url: 'https://www.youtube.com/results?search_query=media+translation+Arabic+English+practice'}] },
      { title: 'ترجمة العناوين والـ Headlines', body: 'العناوين الصحفية لها قواعد خاصة: إيجاز مع إثارة الاهتمام، استخدام المضارع للأحداث الماضية، حذف الأفعال المساعدة. التحدي: الإبداع مع الدقة.', videos: [{title: 'How to Translate Headlines', lang: 'English', url: 'https://www.youtube.com/results?search_query=translating+headlines+Arabic+English'}] }
    ],
    books: [
      { titleAr: 'الترجمة الإعلامية', titleEn: 'Media Translation: A Practical Guide', author: 'Minako O\'Hagan & David Ashworth', authorAr: 'أوهاغان وآشوورث', lang: 'en', color: '#2D6A4F', descAr: 'دليل عملي شامل للترجمة الإعلامية يغطي الأخبار والإعلانات والترجمة المرئية', descEn: 'Comprehensive practical guide covering news, ads and audiovisual translation', download: 'https://archive.org/search?query=media+translation+practical+guide', preview: 'https://www.routledge.com/Media-Translation' },
      { titleAr: 'الترجمة والإعلام في العالم العربي', titleEn: 'Translation & Media in the Arab World', author: 'د. نجوى السمان', authorAr: 'د. نجوى السمان', lang: 'ar', color: '#E76F51', descAr: 'يتناول واقع الترجمة الإعلامية في الوطن العربي والتحديات الراهنة', descEn: 'Addresses the reality of media translation in the Arab world and current challenges', download: 'https://archive.org/search?query=الترجمة+الإعلامية+عربي', preview: 'https://www.neelwafurat.com' },
      { titleAr: 'الصحافة والترجمة الصحفية', titleEn: 'Journalism & News Translation', author: 'Kyle Conway', authorAr: 'كايل كونواي', lang: 'en', color: '#457B9D', descAr: 'يدرس العلاقة بين الصحافة والترجمة وكيف تُبنى الأخبار عبر اللغات', descEn: 'Studies the relationship between journalism and translation across languages', download: 'https://archive.org/search?query=journalism+news+translation+conway', preview: 'https://www.goodreads.com/book/show/17571424' },
    ]
  },
  scientific: {
    icon: '🔬', color: '#457B9D',
    name: 'الترجمة العلمية', nameEn: 'Scientific Translation',
    desc: 'ترجمة النصوص العلمية كالأبحاث والمقالات الطبية والتقنية بدقة عالية.',
    topics: [
      { title: 'خصائص النص العلمي', body: 'النص العلمي يتميز بـ: الموضوعية، الدقة، المصطلحات المتخصصة، الجمل السلبية (Passive Voice)، البنية المنطقية. المترجم يجب ألا يضيف أو يحذف معلومة.', videos: [{title: 'Scientific Text Features', lang: 'English', url: 'https://www.youtube.com/results?search_query=features+of+scientific+writing+style'}, {title: 'الترجمة العلمية مقدمة', lang: 'عربي', url: 'https://www.youtube.com/results?search_query=الترجمة+العلمية+والتقنية+شرح'}] },
      { title: 'المصطلحات الطبية والبيولوجية', body: 'أهمية المصطلحات اللاتينية واليونانية في الطب: cardio=قلب، neuro=عصب، hepato=كبد. استخدام قواميس متخصصة: Dorland Medical Dictionary، WHO المصطلحات الطبية.', videos: [{title: 'Medical Terminology for Translators', lang: 'English', url: 'https://www.youtube.com/results?search_query=medical+terminology+translation+Arabic+English'}] },
      { title: 'ترجمة الأبحاث الأكاديمية', body: 'هيكل البحث العلمي: Abstract — Introduction — Methods — Results — Discussion — Conclusion. كل جزء له أسلوب خاص يجب الحفاظ عليه في الترجمة.', videos: [{title: 'Research Paper Translation', lang: 'English', url: 'https://www.youtube.com/results?search_query=research+paper+translation+strategies'}] }
    ],
    books: [
      { titleAr: 'الترجمة العلمية والتقنية', titleEn: 'Scientific and Technical Translation', author: 'Jody Byrne', authorAr: 'جودي بيرن', lang: 'en', color: '#457B9D', descAr: 'أحد أفضل المراجع في الترجمة العلمية والتقنية مع أمثلة تطبيقية', descEn: 'One of the best references in scientific and technical translation with practical examples', download: 'https://archive.org/search?query=scientific+technical+translation+byrne', preview: 'https://www.goodreads.com/book/show/3250617' },
      { titleAr: 'المصطلح العلمي بين العربية والإنجليزية', titleEn: 'Scientific Terminology: Arabic-English', author: 'د. عبد الصبور شاهين', authorAr: 'د. عبد الصبور شاهين', lang: 'ar', color: '#2D6A4F', descAr: 'مرجع متخصص في المصطلحات العلمية المقابلة بين العربية والإنجليزية', descEn: 'Specialized reference in scientific terminology between Arabic and English', download: 'https://archive.org/search?query=المصطلح+العلمي+عبد+الصبور+شاهين', preview: 'https://www.neelwafurat.com' },
      { titleAr: 'الترجمة الطبية', titleEn: 'Medical Translation Step by Step', author: 'Vicent Montalt & Maria González', authorAr: 'مونتالت وغونزاليس', lang: 'en', color: '#E76F51', descAr: 'دليل خطوة بخطوة لتعلم الترجمة الطبية للمبتدئين والمحترفين', descEn: 'Step-by-step guide to learning medical translation for beginners and professionals', download: 'https://archive.org/search?query=medical+translation+step+by+step+montalt', preview: 'https://www.goodreads.com/book/show/6478332' },
    ]
  }
};

function openSubject(id) {
  const s = subjects[id];
  document.getElementById('subjects-grid-view').style.display = 'none';

  let topicsHTML = s.topics.map((t, i) => `
    <div class="topic-item" id="topic-${id}-${i}">
      <div class="topic-header" onclick="toggleTopic('topic-${id}-${i}')">
        <span class="topic-title">${t.title}</span>
        <span class="topic-toggle">▼</span>
      </div>
      <div class="topic-body">
        <p>${t.body}</p>
        <div class="section-title" style="margin-top:16px">📹 فيديوهات شرح</div>
        <div class="video-grid">
          ${t.videos.map(v => `
            <a href="${v.url}" target="_blank" class="video-card">
              <div class="video-thumb" style="font-size:22px">▶</div>
              <div class="video-info">
                <div class="video-title">${v.title}</div>
                <div class="video-lang">${v.lang} • YouTube</div>
              </div>
            </a>
          `).join('')}
        </div>
      </div>
    </div>
  `).join('');

  let booksHTML = (s.books || []).map(b => `
    <div class="book-card">
      <div class="book-spine" style="background:${b.color}"></div>
      <div class="book-body">
        <span class="book-lang-badge ${b.lang}">${b.lang === 'ar' ? '🇪🇬 عربي' : '🇬🇧 English'}</span>
        <div class="book-title-ar">${b.titleAr}</div>
        <div class="book-title-en">${b.titleEn}</div>
        <div class="book-author">✍️ ${b.authorAr}</div>
        <div class="book-desc">${b.lang === 'ar' ? b.descAr : b.descAr}<br><span style="color:var(--accent3);font-style:italic;font-size:11px">${b.descEn}</span></div>
        <div class="book-actions">
          <a href="${b.download}" target="_blank" class="book-btn primary">⬇ تحميل / بحث</a>
          <a href="${b.preview}" target="_blank" class="book-btn">👁 معاينة</a>
        </div>
      </div>
    </div>
  `).join('');

  document.getElementById('detail-content').innerHTML = `
    <div class="detail-header">
      <div class="detail-icon">${s.icon}</div>
      <div>
        <h2>${s.name}</h2>
        <p>${s.nameEn}</p>
        <p style="margin-top:6px">${s.desc}</p>
      </div>
    </div>

    <div class="resource-tabs">
      <button class="res-tab active" onclick="switchTab(this,'tab-topics-${id}', '${id}')">📋 الموضوعات والفيديوهات</button>
      <button class="res-tab" onclick="switchTab(this,'tab-books-${id}', '${id}')">📚 الكتب الموثقة (${(s.books||[]).length})</button>
    </div>

    <div id="tab-topics-${id}" class="res-panel active">
      ${topicsHTML}
    </div>

    <div id="tab-books-${id}" class="res-panel">
      <div style="margin-bottom:14px; padding:10px 14px; background:var(--accent-soft); border-radius:var(--radius-sm); font-size:13px; color:var(--accent);">
        📌 الكتب مرتبة بالعربية والإنجليزية — روابط التحميل تفتح Archive.org أو الموقع الرسمي
      </div>
      <div class="books-grid">
        ${booksHTML}
      </div>
    </div>
  `;

  document.getElementById('subject-detail').classList.add('active');
}

function switchTab(btn, panelId, subjectId) {
  // deactivate all tabs in this subject
  btn.closest('.resource-tabs').querySelectorAll('.res-tab').forEach(t => t.classList.remove('active'));
  btn.classList.add('active');
  // deactivate all panels for this subject
  document.querySelectorAll(`[id^="tab-topics-${subjectId}"], [id^="tab-books-${subjectId}"]`).forEach(p => p.classList.remove('active'));
  document.getElementById(panelId).classList.add('active');
}

function closeSubject() {
  document.getElementById('subjects-grid-view').style.display = 'block';
  document.getElementById('subject-detail').classList.remove('active');
}

function toggleTopic(id) {
  const el = document.getElementById(id);
  el.classList.toggle('open');
}

// ══════════════════════════════════════════
// TRANSLATOR
// ══════════════════════════════════════════
let fromLang = 'ar', toLang = 'zh';

function setFromLang(lang) {
  fromLang = lang;
  document.querySelectorAll('[id^="from-"]').forEach(b => b.classList.remove('active'));
  document.getElementById('from-' + lang).classList.add('active');
  clearOutput();
}
function setToLang(lang) {
  toLang = lang;
  document.querySelectorAll('[id^="to-"]').forEach(b => b.classList.remove('active'));
  document.getElementById('to-' + lang).classList.add('active');
  clearOutput();
}
function swapLangs() {
  const tmp = fromLang; fromLang = toLang; toLang = tmp;
  ['ar','en','zh'].forEach(l => {
    document.getElementById('from-' + l).classList.toggle('active', fromLang === l);
    document.getElementById('to-' + l).classList.toggle('active', toLang === l);
  });
  const input = document.getElementById('translation-input');
  const output = document.getElementById('translation-output');
  if (output.dataset.translated) {
    const tmp2 = input.value;
    input.value = output.textContent;
    output.textContent = tmp2;
    output.dataset.translated = '1';
  }
}
function clearOutput() {
  const o = document.getElementById('translation-output');
  o.textContent = 'الترجمة ستظهر هنا...';
  o.style.color = 'var(--text-muted)';
  o.style.fontStyle = 'italic';
  delete o.dataset.translated;
}
function usePhrase(phrase) {
  document.getElementById('translation-input').value = phrase;
  clearOutput();
}

const langNames = { ar: 'العربية', en: 'الإنجليزية', zh: 'الصينية' };

async function doTranslate() {
  const text = document.getElementById('translation-input').value.trim();
  if (!text) return;
  const btn = document.getElementById('translate-btn');
  btn.disabled = true;
  btn.innerHTML = 'جاري الترجمة <span class="loading"></span>';

  const output = document.getElementById('translation-output');
  output.textContent = '...';
  output.style.color = 'var(--text-muted)';

  try {
    const prompt = `Translate the following text from ${langNames[fromLang]} to ${langNames[toLang]}. 
    Context: This is for a translation/literature student studying academic and literary texts.
    Return ONLY the translation, nothing else. No explanations.
    
    Text to translate: "${text}"`;

    const response = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        model: 'claude-sonnet-4-20250514',
        max_tokens: 1000,
        messages: [{ role: 'user', content: prompt }]
      })
    });
    const data = await response.json();
    const translated = data.content[0].text.trim();
    output.textContent = translated;
    output.style.color = 'var(--text)';
    output.style.fontStyle = 'normal';
    output.dataset.translated = '1';
  } catch(e) {
    output.textContent = '❌ حدث خطأ. حاولي مرة تانية.';
  }

  btn.disabled = false;
  btn.innerHTML = 'ترجم الآن';
}

// ══════════════════════════════════════════
// CHINESE DATA
// ══════════════════════════════════════════
const chineseData = {
  greetings: [
    { char: '你好', pinyin: 'nǐ hǎo', ar: 'مرحباً', en: 'Hello' },
    { char: '谢谢', pinyin: 'xiè xie', ar: 'شكراً', en: 'Thank you' },
    { char: '再见', pinyin: 'zài jiàn', ar: 'وداعاً', en: 'Goodbye' },
    { char: '对不起', pinyin: 'duì bu qǐ', ar: 'آسف/معلش', en: 'Sorry' },
    { char: '请', pinyin: 'qǐng', ar: 'من فضلك', en: 'Please' },
    { char: '是的', pinyin: 'shì de', ar: 'نعم', en: 'Yes' },
    { char: '不是', pinyin: 'bú shì', ar: 'لا', en: 'No' },
    { char: '好的', pinyin: 'hǎo de', ar: 'حسناً/تمام', en: 'OK' },
  ],
  numbers: [
    { char: '一', pinyin: 'yī', ar: 'واحد', en: 'One' },
    { char: '二', pinyin: 'èr', ar: 'اثنان', en: 'Two' },
    { char: '三', pinyin: 'sān', ar: 'ثلاثة', en: 'Three' },
    { char: '四', pinyin: 'sì', ar: 'أربعة', en: 'Four' },
    { char: '五', pinyin: 'wǔ', ar: 'خمسة', en: 'Five' },
    { char: '六', pinyin: 'liù', ar: 'ستة', en: 'Six' },
    { char: '七', pinyin: 'qī', ar: 'سبعة', en: 'Seven' },
    { char: '八', pinyin: 'bā', ar: 'ثمانية', en: 'Eight' },
    { char: '九', pinyin: 'jiǔ', ar: 'تسعة', en: 'Nine' },
    { char: '十', pinyin: 'shí', ar: 'عشرة', en: 'Ten' },
  ],
  academic: [
    { char: '大学', pinyin: 'dà xué', ar: 'جامعة', en: 'University' },
    { char: '学生', pinyin: 'xué shēng', ar: 'طالب', en: 'Student' },
    { char: '老师', pinyin: 'lǎo shī', ar: 'أستاذ/معلم', en: 'Teacher' },
    { char: '书', pinyin: 'shū', ar: 'كتاب', en: 'Book' },
    { char: '作业', pinyin: 'zuò yè', ar: 'واجب منزلي', en: 'Homework' },
    { char: '考试', pinyin: 'kǎo shì', ar: 'اختبار/امتحان', en: 'Exam' },
    { char: '学习', pinyin: 'xué xí', ar: 'يتعلم/يذاكر', en: 'Study/Learn' },
    { char: '课堂', pinyin: 'kè táng', ar: 'فصل دراسي', en: 'Classroom' },
  ],
  translation: [
    { char: '翻译', pinyin: 'fān yì', ar: 'ترجمة/يترجم', en: 'Translation' },
    { char: '语言', pinyin: 'yǔ yán', ar: 'لغة', en: 'Language' },
    { char: '文化', pinyin: 'wén huà', ar: 'ثقافة', en: 'Culture' },
    { char: '文学', pinyin: 'wén xué', ar: 'أدب', en: 'Literature' },
    { char: '词典', pinyin: 'cí diǎn', ar: 'قاموس', en: 'Dictionary' },
    { char: '句子', pinyin: 'jù zi', ar: 'جملة', en: 'Sentence' },
    { char: '意思', pinyin: 'yì si', ar: 'معنى', en: 'Meaning' },
    { char: '词语', pinyin: 'cí yǔ', ar: 'كلمة/مصطلح', en: 'Word/Term' },
  ],
  daily: [
    { char: '吃饭', pinyin: 'chī fàn', ar: 'يأكل', en: 'Eat' },
    { char: '睡觉', pinyin: 'shuì jiào', ar: 'ينام', en: 'Sleep' },
    { char: '朋友', pinyin: 'péng yǒu', ar: 'صديق', en: 'Friend' },
    { char: '家', pinyin: 'jiā', ar: 'بيت/منزل', en: 'Home/Family' },
    { char: '水', pinyin: 'shuǐ', ar: 'ماء', en: 'Water' },
    { char: '时间', pinyin: 'shí jiān', ar: 'وقت', en: 'Time' },
    { char: '喜欢', pinyin: 'xǐ huān', ar: 'يحب/يعجبه', en: 'Like/Love' },
    { char: '今天', pinyin: 'jīn tiān', ar: 'اليوم', en: 'Today' },
  ]
};

function showChinese(cat) {
  document.querySelectorAll('.cat-btn').forEach(b => b.classList.remove('active'));
  event && event.target && event.target.classList.add('active');
  
  const cards = chineseData[cat];
  document.getElementById('chinese-cards').innerHTML = cards.map(c => `
    <div class="char-card" onclick="this.classList.toggle('flipped')">
      <div class="char-big">${c.char}</div>
      <div class="char-pinyin">${c.pinyin}</div>
      <div class="char-arabic">${c.ar}</div>
      <div class="char-english">${c.en}</div>
    </div>
  `).join('');
}

// Fix category button active on click
document.addEventListener('DOMContentLoaded', () => {
  document.querySelectorAll('.cat-btn').forEach(btn => {
    btn.addEventListener('click', function() {
      document.querySelectorAll('.cat-btn').forEach(b => b.classList.remove('active'));
      this.classList.add('active');
    });
  });
  showChinese('greetings');
});

// ══════════════════════════════════════════
// QUIZ DATA
// ══════════════════════════════════════════
const quizData = {
  phonetics: [
    { q: 'ما الرمز IPA الصحيح لصوت "a" في كلمة "cat"؟', a: '/æ/', opts: ['/æ/', '/ɑː/', '/e/', '/ʌ/'] },
    { q: 'الفونيم هو...', a: 'أصغر وحدة صوتية تميز بين كلمتين', opts: ['أصغر وحدة صوتية تميز بين كلمتين', 'حرف من الأبجدية', 'نبرة الكلمة', 'طريقة نطق الجملة'] },
    { q: 'ما نوع الصوت /b/ في "book"؟', a: 'صامت انفجاري', opts: ['صامت انفجاري', 'صوت متحرك', 'صامت احتكاكي', 'صامت أنفي'] },
    { q: 'ما معنى مصطلح Phonology؟', a: 'علم الأصوات الوظيفية في اللغة', opts: ['علم الأصوات الوظيفية في اللغة', 'دراسة الجمل', 'تحليل النصوص', 'قواعد اللغة'] },
    { q: '/iː/ هو صوت...', a: 'صوت طويل كما في see', opts: ['صوت طويل كما في see', 'صوت في كلمة sit', 'صوت في كلمة set', 'صوت في كلمة cat'] },
    { q: 'الأللوفون هو...', a: 'تغيير غير مميز لنفس الفونيم', opts: ['تغيير غير مميز لنفس الفونيم', 'فونيم جديد', 'صوت أجنبي', 'حرف ساكن'] },
    { q: 'كم عدد أصوات اللغة الإنجليزية تقريباً؟', a: '44', opts: ['44', '26', '36', '52'] },
    { q: 'ما الفرق بين Phonetics و Phonology؟', a: 'Phonetics يدرس الأصوات فيزيائياً، Phonology يدرسها وظيفياً', opts: ['Phonetics يدرس الأصوات فيزيائياً، Phonology يدرسها وظيفياً', 'لا فرق بينهما', 'Phonology للإنجليزية فقط', 'Phonetics للكتابة'] },
    { q: '/θ/ هو صوت...', a: 'كما في "think"', opts: ['كما في "think"', 'كما في "the"', 'كما في "cheese"', 'كما في "she"'] },
    { q: 'الـ Minimal Pair هو...', a: 'كلمتان تختلفان في فونيم واحد فقط مثل pin/bin', opts: ['كلمتان تختلفان في فونيم واحد فقط مثل pin/bin', 'كلمتان متشابهتان في المعنى', 'جملتان قصيرتان', 'كلمتان مترادفتان'] },
  ],
  media: [
    { q: 'ما مبدأ الهرم المقلوب في الكتابة الصحفية؟', a: 'وضع الأهم أولاً ثم التفاصيل', opts: ['وضع الأهم أولاً ثم التفاصيل', 'البدء بالتفاصيل الصغيرة', 'كتابة المقدمة في النهاية', 'ترتيب الأحداث زمنياً'] },
    { q: 'ما التحدي الأكبر في الترجمة الصحفية؟', a: 'السرعة مع الدقة', opts: ['السرعة مع الدقة', 'ترجمة الشعر', 'الترجمة الأدبية', 'تعلم اللغة'] },
    { q: 'الأسلوب الصحفي يتميز بـ...', a: 'الجملة القصيرة والمباشرة', opts: ['الجملة القصيرة والمباشرة', 'الجمل الطويلة والمعقدة', 'الاستخدام المكثف للاستعارات', 'الأسلوب الأدبي الرفيع'] },
    { q: '"Lead" في الخبر الصحفي هو...', a: 'أول فقرة تلخص الخبر', opts: ['أول فقرة تلخص الخبر', 'عنوان الخبر', 'خاتمة الخبر', 'صورة الخبر'] },
    { q: 'ما المقصود بـ Byline في المقال الصحفي؟', a: 'اسم الكاتب أسفل العنوان', opts: ['اسم الكاتب أسفل العنوان', 'العنوان الفرعي', 'آخر سطر', 'المصدر'] },
    { q: 'في ترجمة العناوين الصحفية يُستخدم...', a: 'المضارع للأحداث الماضية', opts: ['المضارع للأحداث الماضية', 'الماضي دائماً', 'المستقبل دائماً', 'الفعل الناقص'] },
    { q: 'Hard News تعني...', a: 'الأخبار العاجلة والسياسية المهمة', opts: ['الأخبار العاجلة والسياسية المهمة', 'أخبار الترفيه', 'التقارير الاقتصادية الطويلة', 'الأخبار الرياضية'] },
    { q: 'Op-Ed هو...', a: 'مقال رأي', opts: ['مقال رأي', 'خبر عاجل', 'تقرير علمي', 'مقابلة صحفية'] },
    { q: 'مصطلح Newsworthiness يعني...', a: 'أهمية الحدث وجدارته بالنشر', opts: ['أهمية الحدث وجدارته بالنشر', 'تاريخ نشر الخبر', 'جودة الترجمة', 'طول الخبر'] },
    { q: 'Feature Article تختلف عن News Article في...', a: 'تركيزها على الخلفية والتحليل', opts: ['تركيزها على الخلفية والتحليل', 'أنها أقصر', 'أنها بلا عنوان', 'أنها تُكتب بالعربية فقط'] },
  ],
  comparative: [
    { q: 'الأدب المقارن يدرس...', a: 'النصوص من ثقافات ولغات مختلفة', opts: ['النصوص من ثقافات ولغات مختلفة', 'الأدب العربي فقط', 'القصائد الكلاسيكية', 'قواعد اللغة'] },
    { q: 'الـ Motif في الأدب هو...', a: 'عنصر متكرر له دلالة رمزية', opts: ['عنصر متكرر له دلالة رمزية', 'شخصية رئيسية', 'نهاية القصة', 'أسلوب الكاتب'] },
    { q: 'الإنتيرتكستيوالتي (Intertextuality) تعني...', a: 'تأثر نص بنصوص أخرى', opts: ['تأثر نص بنصوص أخرى', 'ترجمة النص', 'تلخيص النص', 'تحليل الشخصيات'] },
    { q: 'ما معنى Genre في الأدب؟', a: 'نوع أو تصنيف أدبي', opts: ['نوع أو تصنيف أدبي', 'لغة الكاتب', 'حجم الكتاب', 'تاريخ النشر'] },
    { q: 'الـ Archetype في الأدب المقارن هو...', a: 'نموذج أصلي متكرر في ثقافات مختلفة', opts: ['نموذج أصلي متكرر في ثقافات مختلفة', 'كاتب شهير', 'رواية كلاسيكية', 'أسلوب كتابة'] },
    { q: 'نظرية ما بعد الاستعمار في الأدب تهتم بـ...', a: 'تأثير الاستعمار على الأدب والهوية', opts: ['تأثير الاستعمار على الأدب والهوية', 'الأدب الروسي فقط', 'الشعر الكلاسيكي', 'الروايات البوليسية'] },
    { q: 'الـ Narrative تعني...', a: 'طريقة سرد القصة', opts: ['طريقة سرد القصة', 'نهاية القصة', 'بداية القصة', 'شخصيات القصة'] },
    { q: 'الرمزية (Symbolism) في الأدب تعني...', a: 'استخدام عناصر للتعبير عن معانٍ أعمق', opts: ['استخدام عناصر للتعبير عن معانٍ أعمق', 'وصف المكان', 'حوار الشخصيات', 'ترتيب الأحداث'] },
    { q: 'الـ Theme في الأدب هو...', a: 'الفكرة المحورية للعمل', opts: ['الفكرة المحورية للعمل', 'اسم الكاتب', 'تاريخ النشر', 'طول الكتاب'] },
    { q: 'الـ Canon الأدبي يشير إلى...', a: 'الأعمال الأدبية المعترف بقيمتها الكبرى', opts: ['الأعمال الأدبية المعترف بقيمتها الكبرى', 'الأدب الحديث فقط', 'الأدب الشعبي', 'كتب القواعد'] },
  ],
  chinese: [
    { q: 'ما معنى 你好؟', a: 'مرحباً/Hello', opts: ['مرحباً/Hello', 'شكراً', 'وداعاً', 'من فضلك'] },
    { q: 'كيف تنطق 谢谢؟', a: 'xiè xie', opts: ['xiè xie', 'nǐ hǎo', 'zài jiàn', 'qǐng'] },
    { q: 'ما معنى 学生؟', a: 'طالب/Student', opts: ['طالب/Student', 'أستاذ', 'كتاب', 'امتحان'] },
    { char: '翻译 يعني...', q: '翻译 يعني...', a: 'ترجمة', opts: ['ترجمة', 'لغة', 'أدب', 'جملة'] },
    { q: 'كيف ينطق رقم 1 بالصينية؟', a: 'yī', opts: ['yī', 'èr', 'sān', 'sì'] },
    { q: 'ما معنى 大学؟', a: 'جامعة', opts: ['جامعة', 'مدرسة', 'مكتبة', 'كلية'] },
    { q: '再见 تعني...', a: 'وداعاً', opts: ['وداعاً', 'مرحباً', 'شكراً', 'آسف'] },
    { q: 'كيف تنطق كلمة "يحب" بالصينية؟', a: 'xǐ huān', opts: ['xǐ huān', 'chī fàn', 'shuì jiào', 'shí jiān'] },
    { q: 'ما الـ Pinyin؟', a: 'نظام كتابة أصوات الصينية بالحروف اللاتينية', opts: ['نظام كتابة أصوات الصينية بالحروف اللاتينية', 'لهجة صينية', 'نوع من الكتابة الصينية', 'تطبيق تعليمي'] },
    { q: '考试 يعني...', a: 'امتحان/اختبار', opts: ['امتحان/اختبار', 'كتاب', 'فصل', 'واجب'] },
  ]
};

let currentSubject = 'phonetics';
let currentQ = 0;
let score = 0;
let questions = [];

function selectQuizSubject(el) {
  document.querySelectorAll('.quiz-option').forEach(o => o.classList.remove('selected'));
  el.classList.add('selected');
  currentSubject = el.dataset.subject;
}

function startQuiz() {
  questions = [...quizData[currentSubject]].sort(() => Math.random() - 0.5).slice(0, 10);
  currentQ = 0; score = 0;
  document.getElementById('quiz-setup').style.display = 'none';
  document.getElementById('quiz-result').classList.remove('active');
  document.getElementById('quiz-question-wrap').classList.add('active');
  showQuestion();
}

function showQuestion() {
  const q = questions[currentQ];
  document.getElementById('q-current').textContent = currentQ + 1;
  document.getElementById('q-total').textContent = '/ ' + questions.length;
  document.getElementById('q-progress').style.width = ((currentQ + 1) / questions.length * 100) + '%';

  const labels = { phonetics: 'الصوتيات', media: 'الترجمة الإعلامية', comparative: 'الأدب المقارن', chinese: 'الصينية' };
  document.getElementById('q-subject-label').textContent = labels[currentSubject];
  document.getElementById('q-text').textContent = q.q;

  const shuffled = [...q.opts].sort(() => Math.random() - 0.5);
  document.getElementById('q-answers').innerHTML = shuffled.map(opt => `
    <button class="answer-btn" onclick="checkAnswer(this, '${opt.replace(/'/g,"\\'")}', '${q.a.replace(/'/g,"\\'")}')">
      ${opt}
    </button>
  `).join('');
}

function checkAnswer(btn, chosen, correct) {
  document.querySelectorAll('.answer-btn').forEach(b => {
    b.disabled = true;
    if (b.textContent.trim() === correct) b.classList.add('correct');
  });
  if (chosen === correct) { btn.classList.add('correct'); score++; }
  else btn.classList.add('wrong');

  setTimeout(() => {
    currentQ++;
    if (currentQ < questions.length) showQuestion();
    else showResult();
  }, 1100);
}

function showResult() {
  document.getElementById('quiz-question-wrap').classList.remove('active');
  document.getElementById('quiz-result').classList.add('active');
  document.getElementById('r-score').textContent = score;
  const msgs = ['حاولي تاني! انتي قادرة 💪', 'كويس! في تحسن 😊', 'ممتاز! استمري 🌟', 'رائع جداً! احترافية 🏆', 'مثالي! عبقرية 🎯'];
  const idx = Math.min(Math.floor(score / 2), 4);
  document.getElementById('r-message').textContent = msgs[idx];
}

function resetQuiz() {
  document.getElementById('quiz-result').classList.remove('active');
  document.getElementById('quiz-question-wrap').classList.remove('active');
  document.getElementById('quiz-setup').style.display = 'block';
}
</script>
</body>
</html>
