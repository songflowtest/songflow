<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SongFlow</title>

<style>
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, sans-serif;
  background: #05070c;
  color: #f8fafc;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 14px;
  background: #0b1220;
}

header button {
  background: none;
  border: none;
  color: #3b82f6;
  font-size: 16px;
  cursor: pointer;
}

.view {
  display: none;
  padding: 16px;
}

.view.active {
  display: block;
}

.card {
  background: rgba(20,27,45,0.9);
  border-radius: 14px;
  padding: 16px;
  margin-bottom: 12px;
  cursor: pointer;
}

.card small {
  color: #9ca3af;
}

input {
  width: 100%;
  padding: 12px;
  margin-bottom: 12px;
  border-radius: 8px;
  border: none;
  font-size: 16px;
}

button.primary {
  width: 100%;
  padding: 14px;
  border-radius: 10px;
  border: none;
  background: #2563eb;
  color: white;
  font-size: 16px;
}

.performance {
  position: fixed;
  inset: 0;
  background: #05070c;
  display: none;
  padding: 20px;
  overflow-y: auto;
}

.performance pre {
  font-size: 22px;
  line-height: 1.6;
  white-space: pre-wrap;
}

.shareBox {
  background: #0b1220;
  padding: 12px;
  border-radius: 10px;
  margin-top: 12px;
}
</style>
</head>

<body>

<header>
  <div>🎸 SongFlow</div>
  <div>
    <button onclick="showLibrary()">Library</button>
    <button onclick="showSetlists()">Setlists</button>
  </div>
</header>

<!-- LIBRARY -->
<div id="library" class="view active">
  <h3>Library</h3>
  <div class="card" onclick="openSong(0)">Moon Banana</div>
  <div class="card" onclick="openSong(1)">Electric Puddle</div>
  <div class="card" onclick="openSong(2)">Waffle Tornado</div>
</div>

<!-- SETLISTS -->
<div id="setlists" class="view">
  <h3>Setlists</h3>
  <div id="setlistContainer"></div>
  <button class="primary" onclick="createSetlist()">＋ Create Setlist</button>
</div>

<!-- CREATE SETLIST -->
<div id="createSetlistView" class="view">
  <h3>New Setlist</h3>
  <input id="setlistTitle" placeholder="Setlist title">
  <button class="primary" onclick="saveSetlist()">Save Setlist</button>
</div>

<!-- PERFORMANCE -->
<div id="performance" class="performance">
  <button onclick="closePerformance()">← Back</button>
  <button onclick="shareSong()">Share Song</button>
  <pre id="lyrics"></pre>
  <div id="shareBox" class="shareBox" style="display:none;"></div>
</div>

<script>
const songs = [
{
  title: "Moon Banana",
  text: `G   D   Em
Moon banana on a sidewalk train
La-la fridge hums hurricane`
},
{
  title: "Electric Puddle",
  text: `Am   F   C
Electric puddle shaking hands
Neon rain on marching plans`
},
{
  title: "Waffle Tornado",
  text: `C   G   Am
Waffle tornado spinning slow
Maple syrup undertow`
}
];

let currentSong = 0;
let setlists = [];

function showLibrary() {
  setView("library");
}

function showSetlists() {
  renderSetlists();
  setView("setlists");
}

function setView(id) {
  document.querySelectorAll(".view").forEach(v => v.classList.remove("active"));
  document.getElementById(id).classList.add("active");
}

function openSong(i) {
  currentSong = i;
  document.getElementById("lyrics").innerText = songs[i].text;
  document.getElementById("performance").style.display = "block";
}

function closePerformance() {
  document.getElementById("performance").style.display = "none";
  document.getElementById("shareBox").style.display = "none";
}

function createSetlist() {
  document.getElementById("setlistTitle").value = "";
  setView("createSetlistView");
}

function saveSetlist() {
  const title = document.getElementById("setlistTitle").value || "Untitled Setlist";
  setlists.push(title);
  showSetlists();
}

function renderSetlists() {
  const container = document.getElementById("setlistContainer");
  container.innerHTML = "";
  setlists.forEach(title => {
    const div = document.createElement("div");
    div.className = "card";
    div.innerHTML = title + "<br><small>Tap to open</small>";
    div.onclick = () => openSong(0);
    container.appendChild(div);
  });
}

function shareSong() {
  const data = {
    title: songs[currentSong].title,
    text: songs[currentSong].text
  };

  if (navigator.share) {
    navigator.share(data);
  } else {
    const box = document.getElementById("shareBox");
    box.style.display = "block";
    box.innerText = "Copy & share this song:\n\n" + data.text;
  }
}
</script>

</body>
</html>
