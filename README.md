<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta
    name="viewport"
    content="width=device-width, initial-scale=1, viewport-fit=cover"
  />

  <title>think</title>

  <meta name="theme-color" content="#f8f5ee" />
  <meta name="apple-mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-status-bar-style" content="default" />
  <meta name="apple-mobile-web-app-title" content="think" />
  <link rel="apple-touch-icon" href="apple-touch-icon.png" />

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link
    href="https://fonts.googleapis.com/css2?family=Patrick+Hand&display=swap"
    rel="stylesheet"
  >

  <style>
    * {
      box-sizing: border-box;
    }

    :root {
      --paper: #fbf8f1;
      --ink: #121212;
      --soft-ink: #535353;
      --line-blue: rgba(93, 175, 255, 0.35);
      --line-red: rgba(255, 84, 84, 0.6);
      --border: #1e1e1e;
      --search-border: #666;
      --shadow: rgba(0, 0, 0, 0.08);
    }

    html,
    body {
      margin: 0;
      width: 100%;
      min-height: 100%;
      background: var(--paper);
      color: var(--ink);
      font-family: "Patrick Hand", cursive;
      -webkit-font-smoothing: antialiased;
      text-rendering: optimizeLegibility;
    }

    body {
      min-height: 100vh;
      overflow: hidden;
    }

    .app {
      min-height: 100vh;
      height: 100vh;
      display: flex;
      flex-direction: column;
      background: var(--paper);
      position: relative;
      overflow: hidden;
    }

    .app::before {
      content: "";
      position: absolute;
      inset: 0;
      background:
        linear-gradient(to bottom, transparent 0, transparent 171px, var(--line-blue) 172px, transparent 173px),
        repeating-linear-gradient(
          to bottom,
          transparent 0,
          transparent 51px,
          var(--line-blue) 52px,
          transparent 53px
        );
      pointer-events: none;
      z-index: 0;
    }

    .paper-margin {
      position: absolute;
      top: 200px;
      bottom: 38px;
      left: 26px;
      width: 2px;
      background: var(--line-red);
      z-index: 0;
      pointer-events: none;
    }

    .top-safe {
      padding-top: calc(env(safe-area-inset-top) + 18px);
    }

    .topbar {
      position: relative;
      z-index: 2;
      padding-left: 18px;
      padding-right: 18px;
      padding-bottom: 8px;
    }

    .topbar-row {
      display: grid;
      grid-template-columns: 84px 1fr 84px;
      align-items: start;
      gap: 8px;
    }

    .mini-button {
      border: none;
      background: transparent;
      padding: 0;
      font-family: inherit;
      color: var(--ink);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 4px;
      cursor: pointer;
      user-select: none;
    }

    .mini-button .label {
      font-size: 22px;
      line-height: 1;
      text-align: center;
    }

    .mini-button .sub {
      font-size: 17px;
      line-height: 0.95;
    }

    .title-wrap {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding-top: 2px;
    }

    .app-title {
      font-size: 56px;
      line-height: 0.95;
      margin: 0;
      font-weight: 400;
      letter-spacing: 0.02em;
    }

    .title-dashes {
      display: flex;
      align-items: center;
      gap: 10px;
      margin-bottom: 2px;
      font-size: 20px;
    }

    .title-underline {
      font-size: 26px;
      line-height: 1;
      margin-top: -8px;
    }

    .icon-stack {
      width: 44px;
      height: 44px;
      border: 3px solid var(--ink);
      border-radius: 6px;
      position: relative;
    }

    .icon-stack::before,
    .icon-stack::after {
      content: "";
      position: absolute;
      left: 8px;
      right: 8px;
      height: 3px;
      background: var(--ink);
      border-radius: 999px;
    }

    .icon-stack::before {
      top: 11px;
    }

    .icon-stack::after {
      top: 22px;
      box-shadow: 0 11px 0 0 var(--ink);
    }

    .icon-plus {
      width: 58px;
      height: 58px;
      border: 3px solid var(--ink);
      border-radius: 999px;
      display: grid;
      place-items: center;
      font-size: 40px;
      line-height: 1;
    }

    .search-row {
      position: relative;
      z-index: 2;
      padding: 10px 18px 0;
    }

    .search-shell {
      height: 52px;
      border: 3px solid var(--search-border);
      border-radius: 17px;
      background: rgba(255,255,255,0.45);
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 0 16px;
      box-shadow: 0 2px 0 var(--shadow);
    }

    .search-icon {
      font-size: 30px;
      line-height: 1;
      margin-top: -2px;
    }

    .search-input {
      width: 100%;
      border: none;
      outline: none;
      background: transparent;
      font-family: inherit;
      font-size: 26px;
      color: #7a7a7a;
    }

    .search-input::placeholder {
      color: #8b8b8b;
    }

    .content {
      position: relative;
      z-index: 2;
      flex: 1;
      overflow: auto;
      padding: 26px 18px calc(env(safe-area-inset-bottom) + 24px);
    }

    .entry-inner {
      padding-left: 38px;
      padding-right: 10px;
      min-height: 100%;
    }

    .entry-date {
      font-size: 34px;
      line-height: 1.05;
      margin-bottom: 8px;
      display: inline-block;
      border-bottom: 4px solid var(--ink);
      padding-bottom: 1px;
    }

    .star-right {
      position: absolute;
      right: 32px;
      top: 34px;
      font-size: 40px;
      transform: rotate(10deg);
    }

    .entry-title {
      width: 100%;
      border: none;
      outline: none;
      background: transparent;
      font-family: inherit;
      color: var(--ink);
      font-size: clamp(42px, 8vw, 70px);
      line-height: 1;
      margin-top: 30px;
      margin-bottom: 14px;
      padding: 0;
      font-weight: 400;
    }

    .entry-title::placeholder {
      color: var(--ink);
      opacity: 0.95;
    }

    .title-scribble {
      font-size: 32px;
      color: #7b7b7b;
      line-height: 1;
      margin-top: -18px;
      margin-bottom: 8px;
    }

    .entry-body {
      width: 100%;
      min-height: 52vh;
      border: none;
      outline: none;
      resize: none;
      background: transparent;
      font-family: inherit;
      color: var(--ink);
      font-size: clamp(25px, 4.2vw, 36px);
      line-height: 1.45;
      padding: 0;
      margin: 0;
    }

    .entry-body::placeholder {
      color: #727272;
    }

    .bottom-meta {
      position: relative;
      z-index: 2;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 14px;
      padding: 8px 18px calc(env(safe-area-inset-bottom) + 10px);
      font-size: 24px;
      background: linear-gradient(to top, rgba(251,248,241,0.97), rgba(251,248,241,0.88), transparent);
    }

    .saved-wrap {
      display: flex;
      align-items: center;
      gap: 8px;
      white-space: nowrap;
    }

    .check-circle {
      width: 34px;
      height: 34px;
      border: 3px solid var(--ink);
      border-radius: 999px;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      font-size: 22px;
      line-height: 1;
    }

    .bottom-doodles {
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      height: 76px;
      pointer-events: none;
      z-index: 1;
    }

    .doodle-left,
    .doodle-right {
      position: absolute;
      bottom: 6px;
      font-size: 42px;
    }

    .doodle-left {
      left: 10px;
    }

    .doodle-right {
      right: 10px;
    }

    .doodle-wave {
      position: absolute;
      left: 72px;
      right: 72px;
      bottom: 6px;
      text-align: center;
      font-size: 34px;
      letter-spacing: 2px;
      color: var(--ink);
    }

    .sidebar-overlay {
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,0.18);
      opacity: 0;
      pointer-events: none;
      transition: 0.2s ease;
      z-index: 20;
    }

    .sidebar-overlay.show {
      opacity: 1;
      pointer-events: auto;
    }

    .sidebar {
      position: fixed;
      left: 0;
      top: 0;
      bottom: 0;
      width: min(82vw, 360px);
      background: #fffdf7;
      border-right: 3px solid var(--ink);
      transform: translateX(-102%);
      transition: 0.22s ease;
      z-index: 21;
      display: flex;
      flex-direction: column;
      padding:
        calc(env(safe-area-inset-top) + 16px)
        14px
        calc(env(safe-area-inset-bottom) + 14px);
    }

    .sidebar.show {
      transform: translateX(0);
    }

    .sidebar-head {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 12px;
    }

    .sidebar-title {
      font-size: 38px;
      line-height: 1;
    }

    .close-btn {
      border: 3px solid var(--ink);
      border-radius: 999px;
      width: 42px;
      height: 42px;
      background: transparent;
      font-family: inherit;
      font-size: 24px;
      cursor: pointer;
    }

    .entries-list {
      flex: 1;
      overflow: auto;
      display: flex;
      flex-direction: column;
      gap: 10px;
      padding-top: 6px;
    }

    .entry-card {
      width: 100%;
      text-align: left;
      border: 3px solid var(--ink);
      border-radius: 16px;
      background: #fff;
      padding: 12px 14px;
      font-family: inherit;
      cursor: pointer;
    }

    .entry-card.active {
      background: #f5faff;
    }

    .entry-card-title {
      font-size: 29px;
      line-height: 1;
      margin-bottom: 6px;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }

    .entry-card-preview {
      font-size: 20px;
      color: #666;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      margin-bottom: 4px;
    }

    .entry-card-date {
      font-size: 18px;
      color: #777;
    }

    .sidebar-bottom {
      padding-top: 10px;
      border-top: 2px dashed #999;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    .side-btn {
      border: 3px solid var(--ink);
      border-radius: 14px;
      background: white;
      padding: 10px 12px;
      font-family: inherit;
      font-size: 24px;
      cursor: pointer;
    }

    .hidden-file {
      display: none;
    }

    .ghost-status {
      position: fixed;
      top: 10px;
      left: 50%;
      transform: translateX(-50%) translateY(-10px);
      background: white;
      border: 3px solid var(--ink);
      border-radius: 999px;
      padding: 5px 14px;
      font-size: 22px;
      opacity: 0;
      transition: 0.2s ease;
      z-index: 50;
      pointer-events: none;
    }

    .ghost-status.show {
      opacity: 1;
      transform: translateX(-50%) translateY(0);
    }
  </style>
</head>
<body>
  <div class="app">
    <div class="paper-margin"></div>

    <div class="ghost-status" id="toast">saved</div>

    <div class="top-safe topbar">
      <div class="topbar-row">
        <button class="mini-button" id="entriesBtn" aria-label="Entries">
          <div class="icon-stack"></div>
          <div class="sub">entries ↗</div>
        </button>

        <div class="title-wrap">
          <div class="title-dashes">˙ ˙</div>
          <h1 class="app-title">think</h1>
          <div class="title-underline">_____</div>
        </div>

        <button class="mini-button" id="newBtn" aria-label="New Entry">
          <div class="icon-plus">+</div>
          <div class="sub">new<br>entry ↗</div>
        </button>
      </div>
    </div>

    <div class="search-row">
      <div class="search-shell">
        <div class="search-icon">⌕</div>
        <input
          id="searchInput"
          class="search-input"
          type="text"
          placeholder="search my thoughts..."
        />
      </div>
    </div>

    <main class="content">
      <div class="entry-inner">
        <div class="star-right">☆</div>

        <div class="entry-date" id="entryDate"></div>

        <input
          id="titleInput"
          class="entry-title"
          type="text"
          placeholder="Untitled thought"
          autocomplete="off"
        />

        <div class="title-scribble">____________</div>

        <textarea
          id="bodyInput"
          class="entry-body"
          placeholder="Start typing. Anything counts."
        ></textarea>
      </div>
    </main>

    <footer class="bottom-meta">
      <div id="wordCount">0 words</div>

      <div class="saved-wrap">
        <span id="saveText">saved locally</span>
        <span class="check-circle">✓</span>
      </div>
    </footer>

    <div class="bottom-doodles">
      <div class="doodle-left">☆</div>
      <div class="doodle-wave">~ ~ ~ ~ ~ ~ ~ ~</div>
      <div class="doodle-right">☆</div>
    </div>
  </div>

  <div class="sidebar-overlay" id="overlay"></div>

  <aside class="sidebar" id="sidebar">
    <div class="sidebar-head">
      <div class="sidebar-title">entries</div>
      <button class="close-btn" id="closeSidebar">×</button>
    </div>

    <div class="entries-list" id="entriesList"></div>

    <div class="sidebar-bottom">
      <button class="side-btn" id="exportBtn">export journal</button>
      <button class="side-btn" id="importBtn">import journal</button>
      <input
        id="fileInput"
        class="hidden-file"
        type="file"
        accept="application/json"
      />
    </div>
  </aside>

  <script>
    const STORAGE_KEY = "think-doodle-journal-v1";

    const entriesBtn = document.getElementById("entriesBtn");
    const newBtn = document.getElementById("newBtn");
    const titleInput = document.getElementById("titleInput");
    const bodyInput = document.getElementById("bodyInput");
    const wordCount = document.getElementById("wordCount");
    const saveText = document.getElementById("saveText");
    const entryDate = document.getElementById("entryDate");
    const searchInput = document.getElementById("searchInput");

    const sidebar = document.getElementById("sidebar");
    const overlay = document.getElementById("overlay");
    const closeSidebar = document.getElementById("closeSidebar");
    const entriesList = document.getElementById("entriesList");

    const exportBtn = document.getElementById("exportBtn");
    const importBtn = document.getElementById("importBtn");
    const fileInput = document.getElementById("fileInput");
    const toast = document.getElementById("toast");

    let state = {
      entries: [],
      activeId: null
    };

    let saveTimer = null;
    let toastTimer = null;

    function uid() {
      return (
        "e_" +
        Date.now().toString(36) +
        Math.random().toString(36).slice(2, 8)
      );
    }

    function nowISO() {
      return new Date().toISOString();
    }

    function prettyFullDate(iso) {
      const d = new Date(iso);

      return d.toLocaleDateString("en-US", {
        weekday: "long",
        month: "long",
        day: "numeric"
      });
    }

    function prettySmallDate(iso) {
      const d = new Date(iso);

      return d.toLocaleDateString("en-US", {
        month: "short",
        day: "numeric",
        year: "numeric"
      });
    }

    function showToast(message) {
      toast.textContent = message;
      toast.classList.add("show");
      clearTimeout(toastTimer);
      toastTimer = setTimeout(() => {
        toast.classList.remove("show");
      }, 1200);
    }

    function loadState() {
      try {
        const raw = localStorage.getItem(STORAGE_KEY);
        if (raw) {
          state = JSON.parse(raw);
        }
      } catch (error) {}

      if (!state.entries || !Array.isArray(state.entries) || state.entries.length === 0) {
        const first = {
          id: uid(),
          title: "",
          body: "",
          createdAt: nowISO(),
          updatedAt: nowISO()
        };

        state = {
          entries: [first],
          activeId: first.id
        };

        persist(false);
      }

      if (!state.activeId || !state.entries.find(entry => entry.id === state.activeId)) {
        state.activeId = state.entries[0].id;
      }
    }

    function persist(showSavedText = true) {
      localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
      if (showSavedText) {
        saveText.textContent = "saved locally";
      }
    }

    function getActiveEntry() {
      return state.entries.find(entry => entry.id === state.activeId);
    }

    function updateWordCount() {
      const text = bodyInput.value.trim();
      const words = text ? text.split(/\s+/).filter(Boolean).length : 0;
      wordCount.textContent = `${words} ${words === 1 ? "word" : "words"}`;
    }

    function renderActiveEntry() {
      const entry = getActiveEntry();
      if (!entry) return;

      titleInput.value = entry.title || "";
      bodyInput.value = entry.body || "";
      entryDate.textContent = prettyFullDate(entry.createdAt);
      updateWordCount();
      renderEntriesList(searchInput.value);
      saveText.textContent = "saved locally";
    }

    function renderEntriesList(query = "") {
      const search = query.toLowerCase().trim();
      const list = [...state.entries]
        .sort((a, b) => new Date(b.updatedAt) - new Date(a.updatedAt))
        .filter(entry => {
          const combined = `${entry.title} ${entry.body}`.toLowerCase();
          return combined.includes(search);
        });

      entriesList.innerHTML = "";

      if (list.length === 0) {
        const empty = document.createElement("div");
        empty.className = "entry-card";
        empty.innerHTML = `
          <div class="entry-card-title">nothing here yet</div>
          <div class="entry-card-preview">make a new thought</div>
        `;
        entriesList.appendChild(empty);
        return;
      }

      list.forEach(entry => {
        const card = document.createElement("button");
        card.className = "entry-card" + (entry.id === state.activeId ? " active" : "");

        const previewText =
          (entry.body || "").replace(/\n/g, " ").trim() || "empty page";

        card.innerHTML = `
          <div class="entry-card-title">${escapeHTML(entry.title.trim() || "Untitled thought")}</div>
          <div class="entry-card-preview">${escapeHTML(previewText.slice(0, 42))}</div>
          <div class="entry-card-date">${prettySmallDate(entry.updatedAt)}</div>
        `;

        card.addEventListener("click", () => {
          flushSave();
          state.activeId = entry.id;
          persist();
          renderActiveEntry();
          closeEntries();
        });

        entriesList.appendChild(card);
      });
    }

    function escapeHTML(str) {
      return str.replace(/[&<>"']/g, match => {
        const map = {
          "&": "&amp;",
          "<": "&lt;",
          ">": "&gt;",
          "\"": "&quot;",
          "'": "&#39;"
        };
        return map[match];
      });
    }

    function saveCurrent(showToastMessage = false) {
      const entry = getActiveEntry();
      if (!entry) return;

      entry.title = titleInput.value;
      entry.body = bodyInput.value;
      entry.updatedAt = nowISO();

      persist();
      updateWordCount();
      renderEntriesList(searchInput.value);
      saveText.textContent = "saved locally";

      if (showToastMessage) {
        showToast("saved");
      }
    }

    function queueSave() {
      saveText.textContent = "saving...";
      clearTimeout(saveTimer);
      saveTimer = setTimeout(() => {
        saveCurrent(false);
      }, 350);
    }

    function flushSave() {
      clearTimeout(saveTimer);
      saveCurrent(false);
    }

    function createEntry() {
      flushSave();

      const entry = {
        id: uid(),
        title: "",
        body: "",
        createdAt: nowISO(),
        updatedAt: nowISO()
      };

      state.entries.unshift(entry);
      state.activeId = entry.id;
      persist();
      renderActiveEntry();
      titleInput.focus();
      showToast("new thought");
    }

    function openEntries() {
      flushSave();
      sidebar.classList.add("show");
      overlay.classList.add("show");
      renderEntriesList(searchInput.value);
    }

    function closeEntries() {
      sidebar.classList.remove("show");
      overlay.classList.remove("show");
    }

    function exportJournal() {
      flushSave();

      const blob = new Blob([JSON.stringify(state, null, 2)], {
        type: "application/json"
      });

      const url = URL.createObjectURL(blob);
      const a = document.createElement("a");
      a.href = url;
      a.download = `think-journal-${new Date().toISOString().slice(0, 10)}.json`;
      a.click();
      URL.revokeObjectURL(url);
      showToast("exported");
    }

    function importJournal(file) {
      const reader = new FileReader();

      reader.onload = () => {
        try {
          const incoming = JSON.parse(reader.result);

          if (!incoming.entries || !Array.isArray(incoming.entries)) {
            throw new Error("Invalid format");
          }

          state = incoming;

          if (!state.activeId && state.entries[0]) {
            state.activeId = state.entries[0].id;
          }

          persist();
          renderActiveEntry();
          showToast("imported");
        } catch (error) {
          showToast("bad file");
        }
      };

      reader.readAsText(file);
    }

    entriesBtn.addEventListener("click", openEntries);
    closeSidebar.addEventListener("click", closeEntries);
    overlay.addEventListener("click", closeEntries);

    newBtn.addEventListener("click", createEntry);

    titleInput.addEventListener("input", queueSave);
    bodyInput.addEventListener("input", () => {
      updateWordCount();
      queueSave();
    });

    searchInput.addEventListener("input", event => {
      renderEntriesList(event.target.value);
    });

    exportBtn.addEventListener("click", exportJournal);

    importBtn.addEventListener("click", () => {
      fileInput.click();
    });

    fileInput.addEventListener("change", event => {
      const file = event.target.files[0];
      if (file) {
        importJournal(file);
      }
      fileInput.value = "";
    });

    window.addEventListener("beforeunload", flushSave);

    document.addEventListener("visibilitychange", () => {
      if (document.hidden) {
        flushSave();
      }
    });

    loadState();
    renderActiveEntry();
  </script>
</body>
</html>