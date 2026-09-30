
<html lang="en">
<head>
  <meta charset="UTF-8" />

  <meta
    name="viewport"
    content="width=device-width, initial-scale=1, viewport-fit=cover"
  />

  <meta name="theme-color" content="#17110e" />
  <meta name="apple-mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />
  <meta name="apple-mobile-web-app-title" content="The Little Book" />

  <link rel="apple-touch-icon" href="apple-touch-icon.png" />

  <title>The Little Book</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

  <link
    href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;500;600;700&family=EB+Garamond:ital,wght@0,400;0,500;0,600;1,400&display=swap"
    rel="stylesheet"
  >

  <style>
    :root {
      --night: #120d0b;
      --night-2: #1d1511;
      --night-3: #291c15;

      --panel: rgba(29, 20, 16, .94);
      --panel-soft: rgba(45, 31, 23, .84);

      --paper: #f1e3c8;
      --paper-2: #e8d4b3;
      --paper-3: #dbc39c;

      --ink: #33251a;
      --ink-soft: #6e5a46;

      --cream: #f7ead2;
      --muted: #b59d82;

      --gold: #c89a54;
      --gold-soft: #e2bc79;
      --green: #7f8d6a;

      --line-dark: rgba(255,255,255,.08);
      --line-paper: rgba(82, 59, 38, .14);

      --shadow:
        0 24px 60px rgba(0,0,0,.48),
        0 8px 22px rgba(0,0,0,.28);
    }

    * {
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
    }

    html,
    body {
      margin: 0;
      min-height: 100%;
    }

    body,
    button,
    input,
    textarea {
      font-family: "EB Garamond", Georgia, serif;
    }

    body {
      min-height: 100vh;
      min-height: 100dvh;
      overflow: hidden;
      color: var(--cream);

      background:
        radial-gradient(circle at 10% 10%, rgba(196, 132, 65, .11), transparent 26%),
        radial-gradient(circle at 88% 14%, rgba(92, 59, 120, .07), transparent 28%),
        radial-gradient(circle at 50% 100%, rgba(116, 67, 35, .12), transparent 32%),
        linear-gradient(145deg, #0f0b09, #1b130f 50%, #0f0b09);
    }

    button,
    input,
    textarea {
      font: inherit;
    }

    button {
      cursor: pointer;
    }

    /* =========================================
       APP
    ========================================== */

    .app {
      position: relative;
      height: 100vh;
      height: 100dvh;
      overflow: hidden;
    }

    .ambient {
      position: absolute;
      inset: 0;
      pointer-events: none;
      z-index: 0;
    }

    .ambient::before {
      content: "";
      position: absolute;
      inset: 0;

      background:
        linear-gradient(
          90deg,
          rgba(255,255,255,.01),
          transparent 30%,
          rgba(255,255,255,.01) 70%,
          transparent
        );

      opacity: .5;
    }

    .glow {
      position: absolute;
      border-radius: 999px;
      filter: blur(40px);
      pointer-events: none;
    }

    .glow.one {
      width: 190px;
      height: 190px;
      left: -80px;
      top: 40px;
      background: rgba(216, 135, 62, .17);
    }

    .glow.two {
      width: 180px;
      height: 180px;
      right: -90px;
      top: 120px;
      background: rgba(97, 65, 130, .09);
    }

    .glow.three {
      width: 240px;
      height: 120px;
      left: 40%;
      bottom: -60px;
      background: rgba(183, 112, 47, .10);
    }

    .shell {
      position: relative;
      z-index: 2;

      width: min(1100px, 100%);
      height: 100%;

      margin: 0 auto;

      display: flex;
      flex-direction: column;
    }

    /* =========================================
       HEADER ATMOSPHERE
    ========================================== */

    .header {
      position: relative;
      flex: 0 0 auto;

      padding:
        calc(env(safe-area-inset-top) + 10px)
        14px
        10px;

      border-bottom: 1px solid var(--line-dark);

      background:
        linear-gradient(
          180deg,
          rgba(22,15,12,.97),
          rgba(22,15,12,.91)
        );

      overflow: hidden;
    }

    .header-atmosphere {
      position: absolute;
      inset: 0;
      pointer-events: none;
    }

    .star {
      position: absolute;
      color: var(--gold);
      opacity: .88;
      text-shadow: 0 0 12px rgba(200,154,84,.4);
    }

    .s1 { left: 29%; top: 20px; font-size: 15px; }
    .s2 { left: 35%; top: 40px; font-size: 8px; }
    .s3 { right: 28%; top: 16px; font-size: 13px; }
    .s4 { right: 23%; top: 55px; font-size: 9px; }
    .s5 { left: 23%; top: 72px; font-size: 8px; }

    .moon {
      position: absolute;
      right: 25%;
      top: 20px;

      color: var(--gold-soft);
      font-size: 28px;

      transform: rotate(-10deg);

      text-shadow:
        0 0 12px rgba(225,187,118,.25);
    }

    .ivy-left,
    .ivy-right {
      position: absolute;
      top: 0;
      color: #657052;
      font-size: 22px;
      opacity: .75;
      line-height: 1.1;
    }

    .ivy-left {
      left: 0;
      transform: rotate(-10deg);
    }

    .ivy-right {
      right: 0;
      transform: scaleX(-1) rotate(-6deg);
    }

    .character {
      position: absolute;
      bottom: 8px;

      display: flex;
      align-items: flex-end;
      gap: 3px;

      opacity: .84;
    }

    .character.left {
      left: 18px;
    }

    .character.right {
      right: 18px;
    }

    .character-icon {
      font-size: 28px;
      filter:
        sepia(.8)
        saturate(.55)
        brightness(.92);
    }

    .mini-books {
      font-size: 15px;
      opacity: .7;
      letter-spacing: -4px;
    }

    .brand {
      position: relative;
      z-index: 2;
      text-align: center;
      padding: 5px 70px 12px;
    }

    .brand-kicker {
      color: var(--muted);
      font-family: "Cormorant Garamond", serif;
      font-size: 10px;
      letter-spacing: .32em;
      text-transform: uppercase;
      margin-bottom: 1px;
    }

    .brand h1 {
      margin: 0;
      font-family: "Cormorant Garamond", serif;
      font-size: clamp(40px, 9vw, 66px);
      line-height: .92;
      font-weight: 600;
      color: #f1d5a7;
      text-shadow:
        0 2px 16px rgba(0,0,0,.28);
    }

    .brand-subtitle {
      margin-top: 6px;

      color: #bca78e;

      font-family: "Cormorant Garamond", serif;

      font-size: 10px;
      text-transform: uppercase;
      letter-spacing: .20em;
    }

    /* =========================================
       TOP CONTROLS
    ========================================== */

    .controls {
      position: relative;
      z-index: 4;

      display: grid;
      grid-template-columns: auto auto minmax(0,1fr);

      gap: 8px;

      padding-top: 4px;
    }

    .control-btn {
      min-height: 42px;

      border:
        1px solid
        rgba(221,180,113,.25);

      border-radius: 12px;

      padding: 8px 12px;

      color: #ead8bc;

      background:
        linear-gradient(
          180deg,
          rgba(99,63,34,.28),
          rgba(50,32,23,.20)
        );

      font-family: "Cormorant Garamond", serif;
      font-weight: 600;

      box-shadow:
        inset 0 1px 0 rgba(255,255,255,.05);
    }

    .control-btn.primary {
      color: #21150f;

      background:
        linear-gradient(
          180deg,
          #d4a463,
          #a9793f
        );

      border-color:
        rgba(255,224,168,.34);
    }

    .search-shell {
      min-height: 42px;

      display: flex;
      align-items: center;
      gap: 8px;

      border:
        1px solid
        rgba(255,255,255,.12);

      border-radius: 12px;

      padding: 0 12px;

      background:
        rgba(255,255,255,.035);
    }

    .search-shell span {
      color: #c9b196;
      font-size: 20px;
    }

    .search-input {
      width: 100%;

      border: 0;
      outline: 0;

      background: transparent;

      color: #e9d8bf;

      font-size: 16px;
    }

    .search-input::placeholder {
      color: #9b8977;
    }

    /* =========================================
       MAIN AREA
    ========================================== */

    .workspace {
      min-height: 0;
      flex: 1;

      display: grid;
      grid-template-columns: 245px minmax(0,1fr);

      gap: 0;

      padding:
        10px
        10px
        calc(env(safe-area-inset-bottom) + 10px);
    }

    /* =========================================
       SIDEBAR
    ========================================== */

    .sidebar {
      min-height: 0;

      display: flex;
      flex-direction: column;

      background:
        linear-gradient(
          180deg,
          rgba(48,32,24,.96),
          rgba(27,19,15,.98)
        );

      border:
        1px solid
        rgba(255,255,255,.08);

      border-radius:
        18px 0 0 18px;

      overflow: hidden;

      box-shadow:
        8px 18px 30px rgba(0,0,0,.25);
    }

    .sidebar-title {
      display: flex;
      align-items: center;
      justify-content: space-between;

      padding: 14px 14px 10px;

      border-bottom:
        1px solid
        rgba(255,255,255,.06);

      font-family:
        "Cormorant Garamond",
        serif;

      color: #e5cda9;
    }

    .sidebar-title strong {
      font-size: 19px;
    }

    .sidebar-count {
      color: #9c8065;
    }

    .entries-list {
      min-height: 0;
      flex: 1;

      overflow-y: auto;

      padding: 8px;
    }

    .entry-card {
      position: relative;

      width: 100%;

      border: 0;

      border-bottom:
        1px solid
        rgba(255,255,255,.05);

      border-radius: 10px;

      padding: 11px 12px;

      text-align: left;

      background: transparent;

      color: #e7d6bd;

      transition: .15s ease;
    }

    .entry-card:active {
      transform: scale(.985);
    }

    .entry-card.active {
      background:
        linear-gradient(
          90deg,
          rgba(176,117,60,.25),
          rgba(176,117,60,.08)
        );

      outline:
        1px solid
        rgba(212,164,99,.22);
    }

    .entry-card-title {
      font-family:
        "Cormorant Garamond",
        serif;

      font-weight: 600;

      font-size: 16px;

      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;

      margin-bottom: 3px;
    }

    .entry-card-meta {
      display: flex;
      justify-content: space-between;
      gap: 8px;

      color: #9d8269;
      font-size: 12px;
    }

    .entry-card-symbol {
      color: #bc9259;
    }

    .sidebar-footer {
      padding: 9px;

      border-top:
        1px solid
        rgba(255,255,255,.06);

      display: grid;
      grid-template-columns: 1fr 1fr;

      gap: 7px;
    }

    .small-btn {
      border:
        1px solid
        rgba(255,255,255,.09);

      border-radius: 9px;

      padding: 8px;

      background:
        rgba(255,255,255,.035);

      color: #bca990;

      font-size: 12px;
    }

    /* =========================================
       BOOK
    ========================================== */

    .book-shell {
      min-width: 0;
      min-height: 0;

      position: relative;

      background:
        linear-gradient(
          90deg,
          #c7a875 0%,
          #d9bc8c 1.5%,
          #eddab8 4%,
          #f1e4cb 50%,
          #ead7b7 96%,
          #c4a06e 100%
        );

      border-radius:
        0 20px 20px 0;

      border:
        1px solid
        rgba(255,255,255,.18);

      box-shadow:
        var(--shadow);

      overflow: hidden;
    }

    .book-shell::before {
      content: "";

      position: absolute;
      inset: 0;

      pointer-events: none;

      background:
        radial-gradient(
          ellipse at 3% 50%,
          rgba(85,52,27,.13),
          transparent 14%
        ),
        radial-gradient(
          ellipse at 97% 50%,
          rgba(85,52,27,.09),
          transparent 16%
        ),
        repeating-linear-gradient(
          0deg,
          rgba(94,66,42,.015),
          rgba(94,66,42,.015) 1px,
          transparent 1px,
          transparent 4px
        );
    }

    .book-shell::after {
      content: "";

      position: absolute;

      left: 0;
      top: 0;
      bottom: 0;

      width: 16px;

      background:
        linear-gradient(
          90deg,
          rgba(65,41,25,.24),
          transparent
        );

      pointer-events: none;
    }

    .book-page {
      position: relative;
      z-index: 2;

      height: 100%;
      min-height: 0;

      overflow-y: auto;

      padding:
        30px
        clamp(24px, 5vw, 60px)
        52px;
    }

    .paper-ivy {
      position: absolute;
      right: 10px;
      top: 20px;

      color: #7e7e58;
      opacity: .66;

      font-size: 21px;
      line-height: 1.15;

      transform: rotate(5deg);

      pointer-events: none;
    }

    .paper-moon {
      position: absolute;
      right: 34px;
      top: 53px;

      font-size: 35px;

      color: #c8a25e;

      opacity: .72;

      pointer-events: none;
    }

    .paper-lantern {
      position: absolute;
      right: 28px;
      top: 100px;

      font-size: 26px;
      opacity: .66;
    }

    .paper-sparkles {
      position: absolute;
      right: 83px;
      top: 82px;

      color: #b98e4e;
      letter-spacing: .3em;
      font-size: 10px;
    }

    .entry-date {
      color: #826c55;

      font-style: italic;

      font-size: 17px;

      margin-bottom: 4px;
    }

    .entry-title-input {
      display: block;

      width: calc(100% - 58px);

      border: 0;
      outline: 0;

      background: transparent;

      color: #35261b;

      font-family:
        "Cormorant Garamond",
        serif;

      font-size:
        clamp(36px, 7vw, 62px);

      line-height: 1;

      font-weight: 500;

      padding: 0;
      margin: 0;

      min-height: 60px;
    }

    .entry-title-input::placeholder {
      color: #4a3829;
      opacity: .45;
    }

    .divider {
      display: flex;
      align-items: center;
      gap: 6px;

      width: 180px;

      margin:
        7px
        0
        21px;

      color: #b68c51;
    }

    .divider-line {
      flex: 1;
      height: 1px;
      background:
        linear-gradient(
          90deg,
          #c29b60,
          rgba(194,155,96,.2)
        );
    }

    .divider-symbol {
      font-size: 12px;
    }

    .entry-body-input {
      display: block;

      width: 100%;
      min-height: 42vh;

      border: 0;
      outline: 0;
      resize: none;

      background: transparent;

      color: #3b2b1e;

      font-family:
        "EB Garamond",
        Georgia,
        serif;

      font-size:
        clamp(21px, 4vw, 30px);

      line-height: 1.45;

      padding: 0 0 120px;
      margin: 0;
    }

    .entry-body-input::placeholder {
      color: #8b735c;
    }

    .bottom-ornament {
      position: absolute;

      right: 16px;
      bottom: 72px;

      color: #7c7653;
      opacity: .72;

      font-size: 20px;
      line-height: 1.05;

      text-align: right;

      pointer-events: none;
    }

    .mushrooms {
      font-size: 30px;
      letter-spacing: 2px;
    }

    .tiny-magic {
      color: #b08b55;
      font-size: 11px;
      letter-spacing: .3em;
    }

    /* =========================================
       PAGE META
    ========================================== */

    .page-meta {
      position: absolute;

      left: 26px;
      right: 26px;
      bottom: 13px;

      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      gap: 12px;

      color: #75604c;

      font-size: 11px;

      border-top:
        1px solid
        rgba(93,67,43,.13);

      padding-top: 8px;
    }

    .timestamps {
      display: grid;
      gap: 2px;
    }

    .timestamp-row {
      display: grid;
      grid-template-columns: 52px 1fr;

      gap: 8px;
    }

    .page-status {
      display: flex;
      align-items: center;
      gap: 9px;

      text-align: right;

      white-space: nowrap;
    }

    .autosave {
      color: #64775d;
    }

    .word-count {
      color: #75604c;
    }

    /* =========================================
       MOBILE
    ========================================== */

    .mobile-entry-btn {
      display: none;
    }

    .overlay {
      display: none;
    }

    @media (max-width: 760px) {
      .header {
        padding-left: 10px;
        padding-right: 10px;
      }

      .brand {
        padding-left: 62px;
        padding-right: 62px;
      }

      .character.left {
        left: 8px;
      }

      .character.right {
        right: 8px;
      }

      .character-icon {
        font-size: 22px;
      }

      .controls {
        grid-template-columns:
          1fr
          1fr
          minmax(0, 1.4fr);
      }

      .control-btn {
        padding-left: 7px;
        padding-right: 7px;
        font-size: 13px;
      }

      .search-input {
        font-size: 14px;
      }

      .workspace {
        display: block;
        padding:
          7px
          7px
          calc(env(safe-area-inset-bottom) + 7px);
      }

      .sidebar {
        position: fixed;

        left: 0;
        top: 0;
        bottom: 0;

        z-index: 50;

        width: min(84vw, 320px);

        border-radius: 0 18px 18px 0;

        transform:
          translateX(-103%);

        transition:
          transform .22s ease;

        padding-top:
          calc(
            env(safe-area-inset-top)
            + 12px
          );
      }

      .sidebar.open {
        transform:
          translateX(0);
      }

      .overlay {
        display: block;

        position: fixed;
        inset: 0;

        z-index: 49;

        pointer-events: none;

        opacity: 0;

        background:
          rgba(0,0,0,.45);

        backdrop-filter:
          blur(3px);

        transition:
          opacity .2s ease;
      }

      .overlay.show {
        opacity: 1;
        pointer-events: auto;
      }

      .book-shell {
        height: 100%;
        border-radius: 20px;
      }

      .book-page {
        padding:
          28px
          25px
          65px;
      }

      .entry-title-input {
        font-size: 44px;
      }

      .entry-body-input {
        font-size: 23px;
        min-height: 48vh;
      }

      .page-meta {
        left: 20px;
        right: 20px;
      }

      .mobile-entry-btn {
        display: flex;

        position: absolute;

        left: 13px;
        bottom:
          calc(
            env(safe-area-inset-bottom)
            + 14px
          );

        z-index: 15;

        align-items: center;
        gap: 6px;

        border:
          1px solid
          rgba(255,255,255,.12);

        border-radius: 999px;

        padding: 9px 13px;

        color: #efdbbe;

        background:
          rgba(26,17,13,.93);

        box-shadow:
          0 8px 25px
          rgba(0,0,0,.3);
      }

      .paper-ivy {
        opacity: .46;
      }

      .paper-moon {
        opacity: .56;
      }
    }

    /* =========================================
       TOAST
    ========================================== */

    .toast {
      position: fixed;

      left: 50%;
      top:
        calc(
          env(safe-area-inset-top)
          + 10px
        );

      transform:
        translateX(-50%)
        translateY(-12px);

      z-index: 100;

      opacity: 0;

      pointer-events: none;

      padding: 7px 15px;

      border:
        1px solid
        rgba(255,255,255,.1);

      border-radius: 999px;

      background:
        rgba(22,15,12,.96);

      color: #ebd8bb;

      box-shadow:
        0 8px 24px
        rgba(0,0,0,.3);

      transition:
        .18s ease;
    }

    .toast.show {
      opacity: 1;

      transform:
        translateX(-50%)
        translateY(0);
    }

    .hidden-file {
      display: none;
    }
  </style>
</head>

<body>

  <div class="app">

    <div class="ambient">
      <div class="glow one"></div>
      <div class="glow two"></div>
      <div class="glow three"></div>
    </div>

    <div class="toast" id="toast">
      saved
    </div>

    <div class="shell">

      <!-- =====================================
           HEADER
      ====================================== -->

      <header class="header">

        <div class="header-atmosphere">

          <div class="star s1">✦</div>
          <div class="star s2">✧</div>
          <div class="star s3">✦</div>
          <div class="star s4">✧</div>
          <div class="star s5">✶</div>

          <div class="moon">☾</div>

          <div class="ivy-left">
            ❧<br>❧
          </div>

          <div class="ivy-right">
            ❧<br>❧
          </div>

          <div class="character left">
            <div class="character-icon">🧙‍♂️</div>
            <div class="mini-books">▰▰</div>
          </div>

          <div class="character right">
            <div class="mini-books">▰▰</div>
            <div class="character-icon">🧝</div>
          </div>

        </div>

        <div class="brand">

          <div class="brand-kicker">
            your private journal
          </div>

          <h1>
            The<br>Little Book
          </h1>

          <div class="brand-subtitle">
            somewhere for your brain to wander
          </div>

        </div>

        <div class="controls">

          <button
            class="control-btn primary"
            id="newBtn">
            ＋ New Entry
          </button>

          <button
            class="control-btn"
            id="randomBtn">
            ✦ Random
          </button>

          <div class="search-shell">

            <span>⌕</span>

            <input
              id="searchInput"
              class="search-input"
              placeholder="Search entries..."
            />

          </div>

        </div>

      </header>

      <!-- =====================================
           MAIN
      ====================================== -->

      <section class="workspace">

        <aside
          class="sidebar"
          id="sidebar">

          <div class="sidebar-title">

            <strong>
              ☷ All Entries
            </strong>

            <span
              class="sidebar-count"
              id="entryCount">
              0
            </span>

          </div>

          <div
            class="entries-list"
            id="entriesList">
          </div>

          <div class="sidebar-footer">

            <button
              class="small-btn"
              id="exportBtn">
              Export
            </button>

            <button
              class="small-btn"
              id="importBtn">
              Import
            </button>

            <input
              id="fileInput"
              class="hidden-file"
              type="file"
              accept="application/json"
            />

          </div>

        </aside>

        <div class="book-shell">

          <div class="book-page">

            <!-- page decorations -->

            <div class="paper-ivy">
              ❧<br>
              ❧<br>
              ❧
            </div>

            <div class="paper-moon">
              ☾
            </div>

            <div class="paper-lantern">
              🏮
            </div>

            <div class="paper-sparkles">
              ✦ ✧ ✦
            </div>

            <!-- journal -->

            <div
              class="entry-date"
              id="entryDate">
            </div>

            <input
              id="titleInput"
              class="entry-title-input"
              placeholder="Untitled thought"
              autocomplete="off"
            />

            <div class="divider">

              <div class="divider-line"></div>

              <span class="divider-symbol">
                ✦
              </span>

              <div class="divider-line"></div>

            </div>

            <textarea
              id="bodyInput"
              class="entry-body-input"
              placeholder="Start typing. Anything counts."
            ></textarea>

            <!-- bottom atmosphere -->

            <div class="bottom-ornament">

              <div class="tiny-magic">
                ✦ ✧ ✦
              </div>

              <div class="mushrooms">
                🍄 ❧ 🍄
              </div>

            </div>

            <!-- page metadata -->

            <div class="page-meta">

              <div class="timestamps">

                <div class="timestamp-row">

                  <span>
                    Created
                  </span>

                  <strong
                    id="createdMeta">
                    —
                  </strong>

                </div>

                <div class="timestamp-row">

                  <span>
                    Edited
                  </span>

                  <strong
                    id="editedMeta">
                    —
                  </strong>

                </div>

              </div>

              <div class="page-status">

                <div
                  class="word-count"
                  id="wordCount">
                  0 words
                </div>

                <div
                  class="autosave"
                  id="saveStatus">
                  ☁︎ Auto-saved
                </div>

              </div>

            </div>

          </div>

        </div>

      </section>

      <button
        class="mobile-entry-btn"
        id="mobileEntriesBtn">
        ☷ Entries
      </button>

    </div>

  </div>

  <div
    class="overlay"
    id="overlay">
  </div>

  <script>

    /*
      Keeping the original storage key
      means your older Little Book entries
      can still appear.
    */

    const STORAGE_KEY =
      "little-book-of-omar-v1";

    const $ = id =>
      document.getElementById(id);

    let state = {
      entries: [],
      activeId: null
    };

    let saveTimer = null;
    let toastTimer = null;

    const symbols = [
      "❧",
      "✦",
      "☾",
      "🍄",
      "✧",
      "⚝",
      "❀"
    ];

    function uid() {

      return (
        "e_" +
        Date.now().toString(36) +
        Math.random()
          .toString(36)
          .slice(2, 8)
      );

    }

    function nowISO() {

      return new Date()
        .toISOString();

    }

    function prettyDate(iso) {

      return new Date(iso)
        .toLocaleDateString(
          "en-US",
          {
            month: "long",
            day: "numeric",
            year: "numeric"
          }
        );

    }

    function prettyShortDate(iso) {

      return new Date(iso)
        .toLocaleDateString(
          "en-US",
          {
            month: "short",
            day: "numeric",
            year: "numeric"
          }
        );

    }

    function prettyTime(iso) {

      return new Date(iso)
        .toLocaleString(
          "en-US",
          {
            month: "short",
            day: "numeric",
            year: "numeric",
            hour: "numeric",
            minute: "2-digit"
          }
        );

    }

    function showToast(message) {

      const toast =
        $("toast");

      toast.textContent =
        message;

      toast.classList.add(
        "show"
      );

      clearTimeout(
        toastTimer
      );

      toastTimer =
        setTimeout(
          () => {
            toast.classList
              .remove("show");
          },
          1300
        );

    }

    function persist() {

      localStorage.setItem(
        STORAGE_KEY,
        JSON.stringify(state)
      );

      $("saveStatus")
        .textContent =
        "☁︎ Auto-saved";

    }

    function loadState() {

      try {

        const raw =
          localStorage.getItem(
            STORAGE_KEY
          );

        if (raw) {

          const parsed =
            JSON.parse(raw);

          if (
            parsed &&
            Array.isArray(
              parsed.entries
            )
          ) {

            state =
              parsed;

          }

        }

      } catch (error) {}

      if (
        !state.entries ||
        state.entries.length === 0
      ) {

        const entry = {
          id: uid(),
          title: "",
          body: "",
          createdAt: nowISO(),
          updatedAt: nowISO(),
          symbol: "✦"
        };

        state = {
          entries: [entry],
          activeId: entry.id
        };

        persist();

      }

      state.entries =
        state.entries.map(
          (entry, index) => ({
            ...entry,
            symbol:
              entry.symbol ||
              symbols[
                index %
                symbols.length
              ]
          })
        );

      if (
        !state.activeId ||
        !state.entries.find(
          e =>
            e.id ===
            state.activeId
        )
      ) {

        state.activeId =
          state.entries[0].id;

      }

    }

    function activeEntry() {

      return state.entries.find(
        e =>
          e.id ===
          state.activeId
      );

    }

    function escapeHTML(string) {

      return (
        string || ""
      ).replace(
        /[&<>"']/g,
        char => ({
          "&": "&amp;",
          "<": "&lt;",
          ">": "&gt;",
          "\"": "&quot;",
          "'": "&#39;"
        }[char])
      );

    }

    function updateCounts() {

      const text =
        $("bodyInput")
          .value
          .trim();

      const words =
        text
          ? text
              .split(/\s+/)
              .filter(Boolean)
              .length
          : 0;

      $("wordCount")
        .textContent =
        `${words} ${
          words === 1
            ? "word"
            : "words"
        }`;

    }

    function renderActive() {

      const entry =
        activeEntry();

      if (!entry) return;

      $("titleInput")
        .value =
        entry.title || "";

      $("bodyInput")
        .value =
        entry.body || "";

      $("entryDate")
        .textContent =
        prettyDate(
          entry.createdAt
        );

      $("createdMeta")
        .textContent =
        prettyTime(
          entry.createdAt
        );

      $("editedMeta")
        .textContent =
        prettyTime(
          entry.updatedAt
        );

      updateCounts();

      renderEntries(
        $("searchInput").value
      );

      $("saveStatus")
        .textContent =
        "☁︎ Auto-saved";

    }

    function renderEntries(
      query = ""
    ) {

      const q =
        query
          .trim()
          .toLowerCase();

      const list =
        $("entriesList");

      list.innerHTML = "";

      const entries =
        [...state.entries]
          .sort(
            (a, b) =>
              new Date(
                b.updatedAt
              ) -
              new Date(
                a.updatedAt
              )
          )
          .filter(
            entry => {

              const haystack =
                (
                  (entry.title || "")
                  +
                  " "
                  +
                  (entry.body || "")
                )
                .toLowerCase();

              return (
                !q ||
                haystack.includes(q)
              );

            }
          );

      $("entryCount")
        .textContent =
        state.entries.length;

      entries.forEach(
        entry => {

          const button =
            document.createElement(
              "button"
            );

          button.className =
            "entry-card" +
            (
              entry.id ===
              state.activeId
                ? " active"
                : ""
            );

          const title =
            entry.title.trim() ||
            "Untitled thought";

          button.innerHTML = `
            <div class="entry-card-title">
              ${escapeHTML(title)}
            </div>

            <div class="entry-card-meta">
              <span>
                ${prettyShortDate(entry.updatedAt)}
              </span>

              <span class="entry-card-symbol">
                ${entry.symbol || "✦"}
              </span>
            </div>
          `;

          button.addEventListener(
            "click",
            () => {

              flushSave();

              state.activeId =
                entry.id;

              persist();

              renderActive();

              closeSidebar();

            }
          );

          list.appendChild(
            button
          );

        }
      );

    }

    function queueSave() {

      $("saveStatus")
        .textContent =
        "Writing…";

      updateCounts();

      clearTimeout(
        saveTimer
      );

      saveTimer =
        setTimeout(
          () =>
            saveCurrent(false),
          450
        );

    }

    function saveCurrent(
      showMessage = false
    ) {

      const entry =
        activeEntry();

      if (!entry) return;

      entry.title =
        $("titleInput").value;

      entry.body =
        $("bodyInput").value;

      entry.updatedAt =
        nowISO();

      persist();

      $("editedMeta")
        .textContent =
        prettyTime(
          entry.updatedAt
        );

      updateCounts();

      renderEntries(
        $("searchInput").value
      );

      if (showMessage) {

        showToast(
          "Page saved"
        );

      }

    }

    function flushSave() {

      clearTimeout(
        saveTimer
      );

      saveCurrent(false);

    }

    function newEntry() {

      flushSave();

      const index =
        state.entries.length;

      const entry = {

        id: uid(),

        title: "",

        body: "",

        createdAt:
          nowISO(),

        updatedAt:
          nowISO(),

        symbol:
          symbols[
            index %
            symbols.length
          ]

      };

      state.entries.unshift(
        entry
      );

      state.activeId =
        entry.id;

      persist();

      renderActive();

      $("titleInput")
        .focus();

      showToast(
        "Fresh page"
      );

    }

    function randomEntry() {

      flushSave();

      if (
        state.entries.length <
        2
      ) {

        showToast(
          "Write a few more pages first"
        );

        return;

      }

      const pool =
        state.entries.filter(
          entry =>
            entry.id !==
            state.activeId
        );

      const pick =
        pool[
          Math.floor(
            Math.random() *
            pool.length
          )
        ];

      state.activeId =
        pick.id;

      persist();

      renderActive();

      showToast(
        "Pulled an old page"
      );

    }

    function openSidebar() {

      $("sidebar")
        .classList.add(
          "open"
        );

      $("overlay")
        .classList.add(
          "show"
        );

    }

    function closeSidebar() {

      $("sidebar")
        .classList.remove(
          "open"
        );

      $("overlay")
        .classList.remove(
          "show"
        );

    }

    function exportJournal() {

      flushSave();

      const blob =
        new Blob(
          [
            JSON.stringify(
              state,
              null,
              2
            )
          ],
          {
            type:
              "application/json"
          }
        );

      const url =
        URL.createObjectURL(
          blob
        );

      const link =
        document.createElement(
          "a"
        );

      link.href =
        url;

      link.download =
        `little-book-${
          new Date()
            .toISOString()
            .slice(0,10)
        }.json`;

      link.click();

      URL.revokeObjectURL(
        url
      );

      showToast(
        "Journal exported"
      );

    }

    function importJournal(
      file
    ) {

      const reader =
        new FileReader();

      reader.onload =
        () => {

          try {

            const incoming =
              JSON.parse(
                reader.result
              );

            if (
              !incoming.entries ||
              !Array.isArray(
                incoming.entries
              )
            ) {

              throw new Error(
                "Invalid journal"
              );

            }

            state =
              incoming;

            if (
              !state.activeId &&
              state.entries[0]
            ) {

              state.activeId =
                state.entries[0].id;

            }

            persist();

            renderActive();

            showToast(
              "Journal imported"
            );

          } catch (error) {

            showToast(
              "That file isn't a journal"
            );

          }

        };

      reader.readAsText(
        file
      );

    }

    $("newBtn")
      .addEventListener(
        "click",
        newEntry
      );

    $("randomBtn")
      .addEventListener(
        "click",
        randomEntry
      );

    $("titleInput")
      .addEventListener(
        "input",
        queueSave
      );

    $("bodyInput")
      .addEventListener(
        "input",
        queueSave
      );

    $("searchInput")
      .addEventListener(
        "input",
        event =>
          renderEntries(
            event.target.value
          )
      );

    $("mobileEntriesBtn")
      .addEventListener(
        "click",
        openSidebar
      );

    $("overlay")
      .addEventListener(
        "click",
        closeSidebar
      );

    $("exportBtn")
      .addEventListener(
        "click",
        exportJournal
      );

    $("importBtn")
      .addEventListener(
        "click",
        () =>
          $("fileInput")
            .click()
      );

    $("fileInput")
      .addEventListener(
        "change",
        event => {

          const file =
            event.target
              .files[0];

          if (file) {

            importJournal(
              file
            );

          }

          event.target.value =
            "";

        }
      );

    window.addEventListener(
      "beforeunload",
      flushSave
    );

    document.addEventListener(
      "visibilitychange",
      () => {

        if (
          document.hidden
        ) {

          flushSave();

        }

      }
    );

    loadState();

    renderActive();

  </script>

</body>
</html>