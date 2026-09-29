
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover" />
  <meta name="theme-color" content="#1b1715" />
  <title>The Little Book of Omar</title>
  <link rel="manifest" href="manifest.json" />

  <style>
    :root {
      --ink: #27201c;
      --muted: #756a61;
      --paper: #f2e8d7;
      --paper-2: #eadcc5;
      --night: #171412;
      --night-2: #201b18;
      --gold: #9f7f50;
      --shadow: rgba(20, 14, 10, .35);
      --line: rgba(71, 50, 35, .18);
    }

    * { box-sizing: border-box; }

    html, body {
      margin: 0;
      min-height: 100%;
    }

    body {
      font-family: Georgia, 'Times New Roman', serif;
      background:
        radial-gradient(circle at 20% 10%, rgba(255,255,255,.035), transparent 28%),
        radial-gradient(circle at 85% 90%, rgba(255,255,255,.025), transparent 28%),
        linear-gradient(135deg, var(--night), var(--night-2));
      color: #f7efe4;
      min-height: 100vh;
      overflow-x: hidden;
    }

    .app-shell {
      min-height: 100vh;
      display: grid;
      grid-template-columns: 290px minmax(0, 1fr);
    }

    aside {
      border-right: 1px solid rgba(255,255,255,.08);
      padding: 22px 18px 28px;
      position: sticky;
      top: 0;
      height: 100vh;
      background: rgba(16,13,12,.78);
      backdrop-filter: blur(18px);
      overflow-y: auto;
    }

    .brand {
      margin-bottom: 22px;
    }

    .brand h1 {
      font-size: 1.45rem;
      margin: 0 0 4px;
      font-weight: 600;
      letter-spacing: .01em;
    }

    .brand p {
      margin: 0;
      color: #b9aa9b;
      font-size: .86rem;
      line-height: 1.4;
    }

    .toolbar {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 8px;
      margin-bottom: 14px;
    }

    button,
    input,
    textarea {
      font: inherit;
    }

    button {
      border: 1px solid rgba(255,255,255,.1);
      color: #f8f0e7;
      background: rgba(255,255,255,.055);
      border-radius: 12px;
      padding: 10px 12px;
      cursor: pointer;
      transition: .18s ease;
    }

    button:hover {
      transform: translateY(-1px);
      background: rgba(255,255,255,.1);
    }

    button.primary {
      background: linear-gradient(180deg, #a88757, #7b603d);
      color: #160f0c;
      border-color: rgba(255,255,255,.18);
      font-weight: 700;
    }

    .search {
      width: 100%;
      padding: 11px 12px;
      border-radius: 12px;
      border: 1px solid rgba(255,255,255,.08);
      background: rgba(255,255,255,.05);
      color: #f7efe4;
      outline: none;
      margin-bottom: 13px;
    }

    .search::placeholder {
      color: #988b7e;
    }

    .entry-list {
      display: grid;
      gap: 8px;
    }

    .entry-card {
      text-align: left;
      width: 100%;
      padding: 11px 12px;
      border-radius: 12px;
      border: 1px solid transparent;
      background: transparent;
      color: inherit;
    }

    .entry-card.active {
      background: rgba(255,255,255,.08);
      border-color: rgba(255,255,255,.1);
    }

    .entry-card strong {
      display: block;
      font-size: .92rem;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      margin-bottom: 4px;
    }

    .entry-card span {
      color: #9f9185;
      font-size: .78rem;
    }

    .aside-footer {
      margin-top: 18px;
      padding-top: 16px;
      border-top: 1px solid rgba(255,255,255,.07);
      display: grid;
      gap: 8px;
    }

    main {
      display: grid;
      place-items: start center;
      padding: 34px 24px 70px;
      min-width: 0;
    }

    .book-wrap {
      width: min(980px, 100%);
    }

    .topline {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      margin-bottom: 14px;
      color: #b8a99b;
      font-size: .86rem;
    }

    .status-dot {
      width: 7px;
      height: 7px;
      border-radius: 50%;
      background: #8ea078;
      display: inline-block;
      margin-right: 7px;
      box-shadow: 0 0 16px rgba(142,160,120,.45);
    }

    .book {
      position: relative;
      background:
        linear-gradient(
          90deg,
          #eadcc9 0%,
          #f6ecdc 48%,
          #e9dac4 52%,
          #f4ead9 100%
        );
      color: var(--ink);
      min-height: 690px;
      border-radius: 20px;
      box-shadow:
        0 30px 70px rgba(0,0,0,.42),
        inset 0 0 55px rgba(105,72,45,.09);
      overflow: hidden;
      border: 1px solid rgba(255,255,255,.18);
    }

    .book:before {
      content: '';
      position: absolute;
      left: 50%;
      top: 0;
      bottom: 0;
      width: 1px;
      background:
        linear-gradient(
          to bottom,
          transparent,
          rgba(68,46,31,.18),
          transparent
        );
      box-shadow: 0 0 18px rgba(67,45,30,.15);
      pointer-events: none;
    }

    .page {
      width: 50%;
      min-height: 690px;
      padding: 48px 46px 52px;
      float: left;
      position: relative;
    }

    .page.left {
      border-right: 1px solid rgba(85,60,40,.08);
    }

    .ornament {
      font-size: 1rem;
      letter-spacing: .32em;
      color: var(--gold);
      margin-bottom: 14px;
    }

    .date {
      color: #75695e;
      font-size: .86rem;
      margin-bottom: 10px;
      letter-spacing: .03em;
      text-transform: uppercase;
    }

    .title-input {
      width: 100%;
      border: 0;
      outline: 0;
      background: transparent;
      color: var(--ink);
      font-family: 'Palatino Linotype', Georgia, serif;
      font-size: clamp(1.8rem, 4vw, 3.1rem);
      line-height: 1.05;
      padding: 0;
      margin-bottom: 20px;
    }

    .body-input {
      width: 100%;
      min-height: 470px;
      border: 0;
      resize: none;
      outline: 0;
      background: transparent;
      color: #2d2520;
      font-size: 1.03rem;
      line-height: 1.78;
      padding: 0;
      background-image:
        repeating-linear-gradient(
          to bottom,
          transparent 0,
          transparent 31px,
          rgba(80,55,38,.08) 32px
        );
      background-size: 100% 32px;
    }

    .right-page-content {
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    .quote {
      margin-top: 30px;
      color: #665b52;
      font-size: .95rem;
      line-height: 1.65;
      border-left: 2px solid rgba(126,95,61,.28);
      padding-left: 16px;
    }

    .meta-box {
      border: 1px solid rgba(88,61,40,.15);
      border-radius: 16px;
      padding: 16px;
      background: rgba(255,255,255,.22);
      backdrop-filter: blur(3px);
    }

    .meta-box h3 {
      margin: 0 0 10px;
      font-size: .95rem;
      font-weight: 600;
      color: #5f534a;
    }

    .meta-row {
      display: flex;
      justify-content: space-between;
      gap: 12px;
      color: #6f6359;
      font-size: .86rem;
      padding: 7px 0;
      border-bottom: 1px dashed rgba(83,58,39,.12);
    }

    .meta-row:last-child {
      border-bottom: 0;
    }

    .page-number {
      position: absolute;
      bottom: 18px;
      font-size: .78rem;
      color: #988a7e;
    }

    .left .page-number {
      left: 46px;
    }

    .right .page-number {
      right: 46px;
    }

    .mobile-bar {
      display: none;
    }

    .toast {
      position: fixed;
      right: 18px;
      bottom: 18px;
      background: rgba(23,19,17,.94);
      color: #f6eee5;
      border: 1px solid rgba(255,255,255,.1);
      padding: 11px 14px;
      border-radius: 12px;
      opacity: 0;
      transform: translateY(8px);
      transition: .2s ease;
      pointer-events: none;
      z-index: 50;
      box-shadow: 0 12px 30px rgba(0,0,0,.35);
    }

    .toast.show {
      opacity: 1;
      transform: translateY(0);
    }

    @media (max-width: 820px) {
      .app-shell {
        grid-template-columns: 1fr;
      }

      aside {
        position: fixed;
        inset: 0 auto 0 0;
        width: min(86vw, 330px);
        transform: translateX(-102%);
        z-index: 40;
        transition: .22s ease;
        box-shadow: 20px 0 40px rgba(0,0,0,.35);
      }

      aside.open {
        transform: translateX(0);
      }

      main {
        padding: 18px 12px 80px;
      }

      .book {
        min-height: 0;
        border-radius: 16px;
      }

      .book:before {
        display: none;
      }

      .page {
        width: 100%;
        float: none;
        min-height: auto;
        padding: 34px 24px 44px;
      }

      .page.right {
        display: none;
      }

      .body-input {
        min-height: 56vh;
      }

      .topline {
        padding: 0 3px;
      }

      .mobile-bar {
        display: flex;
        position: fixed;
        left: 12px;
        right: 12px;
        bottom: 12px;
        gap: 8px;
        z-index: 30;
        padding: 8px;
        border-radius: 16px;
        background: rgba(20,17,15,.9);
        backdrop-filter: blur(16px);
        border: 1px solid rgba(255,255,255,.09);
      }

      .mobile-bar button {
        flex: 1;
      }
    }
  </style>
</head>

<body>

  <div class="app-shell">

    <aside id="sidebar">

      <div class="brand">
        <h1>The Little Book</h1>

        <p>
          No prompts. No productivity score.
          Just somewhere for your brain to land.
        </p>
      </div>

      <div class="toolbar">
        <button class="primary" id="newBtn">
          ＋ New
        </button>

        <button id="randomBtn">
          ✦ Random
        </button>
      </div>

      <input
        class="search"
        id="searchInput"
        placeholder="Search old thoughts…"
      />

      <div
        class="entry-list"
        id="entryList">
      </div>

      <div class="aside-footer">

        <button id="exportBtn">
          Export journal
        </button>

        <button id="importBtn">
          Import journal
        </button>

        <input
          type="file"
          id="fileInput"
          accept="application/json"
          hidden
        />

      </div>

    </aside>

    <main>

      <div class="book-wrap">

        <div class="topline">

          <div>
            <span class="status-dot"></span>
            <span id="saveStatus">
              Saved locally
            </span>
          </div>

          <div id="wordCount">
            0 words
          </div>

        </div>

        <section class="book">

          <div class="page left">

            <div class="ornament">
              ✦ ☾ ✧
            </div>

            <div
              class="date"
              id="entryDate">
            </div>

            <input
              class="title-input"
              id="titleInput"
              placeholder="Untitled thought"
            />

            <textarea
              class="body-input"
              id="bodyInput"
              placeholder="Start typing. Anything counts."
            ></textarea>

            <div class="page-number">
              I
            </div>

          </div>

          <div class="page right">

            <div class="right-page-content">

              <div>

                <div class="ornament">
                  ☼ ✦ ☾
                </div>

                <div
                  class="quote"
                  id="quoteBox">
                  Some entries will matter.
                  Some will be completely pointless.
                  Keep both.
                </div>

              </div>

              <div class="meta-box">

                <h3>
                  About this page
                </h3>

                <div class="meta-row">
                  <span>Created</span>
                  <strong id="createdMeta">
                    —
                  </strong>
                </div>

                <div class="meta-row">
                  <span>Last edited</span>
                  <strong id="editedMeta">
                    —
                  </strong>
                </div>

                <div class="meta-row">
                  <span>Characters</span>
                  <strong id="charMeta">
                    0
                  </strong>
                </div>

              </div>

            </div>

            <div class="page-number">
              II
            </div>

          </div>

        </section>

      </div>

    </main>

  </div>

  <div class="mobile-bar">

    <button id="menuBtn">
      ☰ Entries
    </button>

    <button
      class="primary"
      id="saveBtn">
      Save
    </button>

  </div>

  <div
    class="toast"
    id="toast">
  </div>

  <script>
    const STORAGE_KEY =
      'little-book-of-omar-v1';

    const $ = (id) =>
      document.getElementById(id);

    let state = {
      entries: [],
      activeId: null
    };

    let saveTimer = null;

    function uid() {
      return (
        'e_' +
        Date.now().toString(36) +
        Math.random()
          .toString(36)
          .slice(2, 7)
      );
    }

    function nowISO() {
      return new Date().toISOString();
    }

    function prettyDate(
      iso,
      long = true
    ) {
      const d = new Date(iso);

      return new Intl.DateTimeFormat(
        undefined,
        long
          ? {
              weekday: 'long',
              month: 'long',
              day: 'numeric',
              year: 'numeric'
            }
          : {
              month: 'short',
              day: 'numeric'
            }
      ).format(d);
    }

    function prettyTime(iso) {

      const d =
        new Date(iso);

      return new Intl.DateTimeFormat(
        undefined,
        {
          month: 'short',
          day: 'numeric',
          hour: 'numeric',
          minute: '2-digit'
        }
      ).format(d);
    }

    function load() {

      try {

        const raw =
          localStorage.getItem(
            STORAGE_KEY
          );

        if (raw) {
          state =
            JSON.parse(raw);
        }

      } catch (_) {}

      if (!state.entries?.length) {

        const entry = {

          id: uid(),

          title: '',

          body: '',

          createdAt:
            nowISO(),

          updatedAt:
            nowISO()

        };

        state = {

          entries: [entry],

          activeId: entry.id

        };

        persist();
      }

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

    function persist() {

      localStorage.setItem(
        STORAGE_KEY,
        JSON.stringify(state)
      );

      $('saveStatus').textContent =
        'Saved locally';
    }

    function active() {

      return state.entries.find(
        e =>
          e.id ===
          state.activeId
      );
    }

    function renderEntry() {

      const e = active();

      if (!e) return;

      $('titleInput').value =
        e.title || '';

      $('bodyInput').value =
        e.body || '';

      $('entryDate').textContent =
        prettyDate(e.createdAt);

      $('createdMeta').textContent =
        prettyTime(e.createdAt);

      $('editedMeta').textContent =
        prettyTime(e.updatedAt);

      updateCounts();

      renderList();
    }

    function renderList() {

      const q =
        $('searchInput')
          .value
          .trim()
          .toLowerCase();

      const list =
        $('entryList');

      list.innerHTML = '';

      [...state.entries]

        .sort(
          (a, b) =>
            new Date(b.updatedAt) -
            new Date(a.updatedAt)
        )

        .filter(
          e =>
            !q ||
            (
              e.title +
              ' ' +
              e.body
            )
            .toLowerCase()
            .includes(q)
        )

        .forEach(e => {

          const btn =
            document.createElement(
              'button'
            );

          btn.className =
            'entry-card' +
            (
              e.id ===
              state.activeId
                ? ' active'
                : ''
            );

          const firstLine =
            (e.body || '')
              .trim()
              .split('\n')[0];

          btn.innerHTML = `
            <strong>
              ${
                escapeHtml(
                  e.title ||
                  firstLine ||
                  'Untitled thought'
                )
              }
            </strong>

            <span>
              ${prettyTime(
                e.updatedAt
              )}
            </span>
          `;

          btn.onclick = () => {

            flushCurrent();

            state.activeId =
              e.id;

            persist();

            renderEntry();

            $('sidebar')
              .classList
              .remove('open');
          };

          list.appendChild(btn);
        });
    }

    function escapeHtml(s) {

      return s.replace(
        /[&<>'"]/g,
        c => ({
          '&': '&amp;',
          '<': '&lt;',
          '>': '&gt;',
          "'": '&#39;',
          '"': '&quot;'
        }[c])
      );
    }

    function updateCounts() {

      const text =
        $('bodyInput')
          .value
          .trim();

      const words =
        text
          ? text
              .split(/\s+/)
              .length
          : 0;

      $('wordCount').textContent =
        `${words} word${
          words === 1
            ? ''
            : 's'
        }`;

      $('charMeta').textContent =
        $('bodyInput')
          .value
          .length
          .toLocaleString();
    }

    function markDirty() {

      $('saveStatus').textContent =
        'Writing…';

      updateCounts();

      clearTimeout(saveTimer);

      saveTimer =
        setTimeout(
          () =>
            saveCurrent(false),
          650
        );
    }

    function flushCurrent() {

      clearTimeout(saveTimer);

      saveCurrent(false);
    }

    function saveCurrent(
      showToast = true
    ) {

      const e =
        active();

      if (!e) return;

      e.title =
        $('titleInput').value;

      e.body =
        $('bodyInput').value;

      e.updatedAt =
        nowISO();

      persist();

      $('editedMeta').textContent =
        prettyTime(
          e.updatedAt
        );

      renderList();

      if (showToast) {
        toast('Page saved');
      }
    }

    function newEntry() {

      flushCurrent();

      const e = {

        id: uid(),

        title: '',

        body: '',

        createdAt:
          nowISO(),

        updatedAt:
          nowISO()

      };

      state.entries.unshift(e);

      state.activeId =
        e.id;

      persist();

      renderEntry();

      $('titleInput').focus();

      toast('Fresh page');
    }

    function randomEntry() {

      flushCurrent();

      if (
        state.entries.length <
        2
      ) {
        return toast(
          'You need a few more memories first'
        );
      }

      const pool =
        state.entries.filter(
          e =>
            e.id !==
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

      renderEntry();

      toast(
        'Pulled an old page'
      );
    }

    function exportJournal() {

      flushCurrent();

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
              'application/json'
          }
        );

      const url =
        URL.createObjectURL(
          blob
        );

      const a =
        document.createElement(
          'a'
        );

      a.href = url;

      a.download =
        `little-book-journal-${
          new Date()
            .toISOString()
            .slice(0,10)
        }.json`;

      a.click();

      URL.revokeObjectURL(
        url
      );

      toast(
        'Journal exported'
      );
    }

    function importJournal(
      file
    ) {

      const reader =
        new FileReader();

      reader.onload = () => {

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
              'bad'
            );
          }

          state = incoming;

          if (
            !state.activeId &&
            state.entries[0]
          ) {
            state.activeId =
              state.entries[0].id;
          }

          persist();

          renderEntry();

          toast(
            'Journal imported'
          );

        } catch (_) {

          toast(
            'That file does not look like a journal'
          );
        }
      };

      reader.readAsText(
        file
      );
    }

    function toast(msg) {

      const t =
        $('toast');

      t.textContent =
        msg;

      t.classList.add(
        'show'
      );

      setTimeout(
        () =>
          t.classList.remove(
            'show'
          ),
        1500
      );
    }

    $('newBtn').onclick =
      newEntry;

    $('randomBtn').onclick =
      randomEntry;

    $('saveBtn').onclick =
      () =>
        saveCurrent(true);

    $('searchInput').oninput =
      renderList;

    $('titleInput').oninput =
      markDirty;

    $('bodyInput').oninput =
      markDirty;

    $('exportBtn').onclick =
      exportJournal;

    $('importBtn').onclick =
      () =>
        $('fileInput').click();

    $('fileInput').onchange =
      (e) =>
        e.target.files[0] &&
        importJournal(
          e.target.files[0]
        );

    $('menuBtn').onclick =
      () =>
        $('sidebar')
          .classList
          .toggle('open');

    window.addEventListener(
      'beforeunload',
      flushCurrent
    );

    load();

    renderEntry();

    if (
      'serviceWorker' in navigator &&
      location.protocol.startsWith(
        'http'
      )
    ) {
      navigator
        .serviceWorker
        .register(
          './service-worker.js'
        )
        .catch(() => {});
    }
  </script>

</body>
</html>
