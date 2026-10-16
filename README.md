<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#020712">
<title>For Shan — 16 October</title>

<style>
*{box-sizing:border-box;margin:0;padding:0}
html,body{width:100%;height:100%;overflow:hidden;background:#020712;color:white;font-family:Arial,Helvetica,sans-serif}
body{position:relative}
button{font:inherit;cursor:pointer;-webkit-tap-highlight-color:transparent}

.bg{position:fixed;inset:0;z-index:-2;overflow:hidden;background:radial-gradient(ellipse at 50% 45%,#102c50,transparent 50%),linear-gradient(145deg,#02040a,#07172d 55%,#02050b)}
.stars{position:absolute;inset:0}
.star{position:absolute;width:2px;height:2px;border-radius:50%;background:white;animation:twinkle 3s infinite ease-in-out}
@keyframes twinkle{0%,100%{opacity:.15;transform:scale(.7)}50%{opacity:.9;transform:scale(1.4)}}
.light{position:absolute;width:350px;height:350px;border-radius:50%;filter:blur(85px);background:rgba(35,125,255,.12);animation:drift 12s infinite alternate ease-in-out}
.light.one{top:5%;left:-180px}.light.two{right:-180px;bottom:-5%;animation-delay:-4s}
@keyframes drift{to{transform:translate(130px,-65px)}}

.screen{position:fixed;inset:0;display:flex;justify-content:center;align-items:center;opacity:0;visibility:hidden;pointer-events:none;transition:opacity 1s ease,visibility 1s;z-index:5}
.screen.active{opacity:1;visibility:visible;pointer-events:auto}

/* Countdown */
#intro,#dateScreen,#movie,#yearScreen,#football,#final{flex-direction:column;text-align:center}
.smallIntro{margin-bottom:30px;color:#a6c8f7;font-size:10px;letter-spacing:5px}
.count{font-size:clamp(120px,30vw,230px);font-weight:900;line-height:.85;letter-spacing:-10px;text-shadow:0 0 70px rgba(66,145,255,.6);animation:countIn .8s ease both}
.countLabel{margin-top:28px;color:#94bfff;font-size:9px;letter-spacing:6px}
@keyframes countIn{from{opacity:0;transform:scale(1.6);filter:blur(14px)}to{opacity:1;transform:scale(1);filter:blur(0)}}

.dateNumber{font-size:clamp(150px,38vw,280px);font-weight:900;line-height:.75;letter-spacing:-12px;text-shadow:0 0 90px rgba(67,151,255,.65);animation:countIn 1.3s ease both}
.dateMonth{margin-top:27px;font-size:clamp(18px,5vw,32px);letter-spacing:12px;color:#c9e0ff;animation:fadeUp 1s .3s both}
.dateLine{width:75px;height:1px;background:#dceaff;margin:28px auto}
.dateText{font-size:9px;letter-spacing:4px;color:#9ab4d7;animation:fadeUp 1s .5s both}
@keyframes fadeUp{from{opacity:0;transform:translateY(18px)}to{opacity:1;transform:translateY(0)}}

#flash{position:fixed;inset:0;background:white;opacity:0;z-index:100;pointer-events:none}
.flashActive{animation:flash .8s ease}
@keyframes flash{0%{opacity:0}15%{opacity:.9}100%{opacity:0}}

.movieTop{position:absolute;top:30px;left:25px;font-size:9px;letter-spacing:4px;color:#7797bf}
.movieCenter{width:90%;max-width:700px}
.movieSmall{font-size:10px;letter-spacing:5px;color:#80b5ff;margin-bottom:25px}
.movieText{font-size:clamp(30px,7vw,68px);font-weight:900;line-height:1.1;letter-spacing:-2px;animation:fadeUp .9s both}
.year{font-size:clamp(100px,28vw,220px);font-weight:900;letter-spacing:-9px;line-height:.85;text-shadow:0 0 80px rgba(40,130,255,.5);animation:countIn .8s ease}
.footballText{position:absolute;top:22%;width:90%;font-size:10px;letter-spacing:4px;color:#9ebde5}
.ball{position:absolute;left:-100px;bottom:35%;font-size:65px;animation:rollBall 3.8s cubic-bezier(.2,.7,.3,1) forwards}
@keyframes rollBall{from{left:-100px;transform:rotate(0)}to{left:calc(100% + 100px);transform:rotate(900deg)}}
.argentinaLine{position:absolute;bottom:23%;width:100%;height:2px;background:linear-gradient(90deg,transparent,#75b9ff,white,#75b9ff,transparent);opacity:.5}

/* Memory cards */
#memory{position:fixed;inset:0;display:flex;justify-content:center;align-items:center;opacity:0;visibility:hidden;pointer-events:none;transition:opacity .8s ease;z-index:30}
#memory.active{opacity:1;visibility:visible;pointer-events:auto}
.memoryGlow{position:absolute;width:450px;height:450px;border-radius:50%;background:rgba(30,120,255,.09);filter:blur(100px);pointer-events:none}

.note{position:absolute;width:min(88%,560px);max-height:calc(100dvh - 125px);overflow-y:auto;padding:32px 27px 35px;border:1px solid rgba(160,210,255,.2);border-radius:22px;background:linear-gradient(135deg,rgba(20,55,100,.42),rgba(4,12,25,.8));box-shadow:0 25px 100px rgba(0,0,0,.5),inset 0 1px rgba(255,255,255,.06);backdrop-filter:blur(16px);-webkit-backdrop-filter:blur(16px);opacity:0;transform:translateX(55px) scale(.96);pointer-events:none;transition:opacity .55s ease,transform .65s cubic-bezier(.2,.8,.2,1)}
.note::-webkit-scrollbar{width:3px}
.note::-webkit-scrollbar-thumb{background:#558dcc;border-radius:5px}
.note.active{opacity:1;transform:translateX(0) scale(1);pointer-events:auto}
.noteNumber{font-size:9px;letter-spacing:3px;color:#79b3ff;margin-bottom:25px}
.noteIcon{font-size:34px;color:#e0eeff;margin-bottom:18px;text-shadow:0 0 25px rgba(80,160,255,.65)}
.noteTitle{font-size:clamp(25px,6vw,40px);font-weight:900;letter-spacing:-1px;line-height:1.05;margin-bottom:22px}
.noteText{white-space:pre-line;font-size:14px;line-height:1.8;color:rgba(235,243,255,.82)}
.noteSignature{margin-top:25px;font-size:9px;letter-spacing:3px;color:#86baff}

.controls{position:absolute;bottom:16px;display:flex;gap:12px;z-index:50}
.controls button{width:45px;height:45px;border-radius:50%;border:1px solid rgba(150,200,255,.3);background:rgba(10,30,55,.85);color:white;font-size:27px;transition:background .25s,transform .25s}
.controls button:active{transform:scale(.92);background:rgba(80,150,255,.3)}
.noteHint{position:absolute;bottom:70px;color:rgba(190,215,250,.5);font-size:8px;letter-spacing:3px;text-align:center;width:100%;pointer-events:none}

.finalNumber{font-size:clamp(145px,40vw,300px);font-weight:900;line-height:.75;letter-spacing:-15px;color:transparent;-webkit-text-stroke:1px rgba(255,255,255,.28);text-shadow:0 0 70px rgba(40,140,255,.35);animation:countIn 1.5s ease}
.finalTitle{margin-top:22px;font-size:clamp(27px,7vw,60px);font-weight:900;letter-spacing:-2px;animation:fadeUp 1s .4s both}
.finalTitle span{color:#8bbcff}
.flag{display:flex;width:85px;height:4px;margin:25px auto;border-radius:5px;overflow:hidden;animation:fadeUp 1s .6s both}
.flag div{flex:1}.blue{background:#76b8ff}.white{background:white}
.finalLine{width:80px;height:1px;background:#a9c9f4;margin:0 auto 23px;animation:fadeUp 1s .7s both}
.finalWish{width:85%;max-width:520px;font-size:13px;line-height:1.8;color:rgba(235,243,255,.75);animation:fadeUp 1s .9s both}
.finalSign{margin-top:25px;font-size:10px;letter-spacing:4px;color:#86baff;animation:fadeUp 1s 1.1s both}
.restart{margin-top:28px;padding:10px 17px;border:1px solid rgba(160,210,255,.25);border-radius:25px;background:rgba(10,30,55,.6);color:#dceaff;font-size:10px;letter-spacing:2px;animation:fadeUp 1s 1.3s both}

@media(max-width:600px){
  .dateMonth{letter-spacing:8px}
  .note{padding:27px 23px 30px;max-height:calc(100dvh - 120px)}
  .noteText{font-size:13px;line-height:1.72}
  .noteTitle{font-size:28px}
  .noteNumber{margin-bottom:20px}
  .noteIcon{margin-bottom:15px}
  .noteSignature{margin-top:20px}
  .controls{bottom:12px}
  .noteHint{bottom:62px}
}
@media(prefers-reduced-motion:reduce){
  *,*::before,*::after{animation-duration:.01ms!important;animation-iteration-count:1!important;scroll-behavior:auto!important}
}
</style>
</head>

<body>
<div class="bg">
  <div class="stars" id="stars"></div>
  <div class="light one"></div>
  <div class="light two"></div>
</div>
<div id="flash"></div>

<!-- COUNTDOWN -->
<div id="intro" class="screen active">
  <div class="smallIntro">A LITTLE SOMETHING FOR SHAN</div>
  <div class="count" id="count">03</div>
  <div class="countLabel">WAIT FOR IT</div>
</div>

<!-- DATE REVEAL -->
<div id="dateScreen" class="screen">
  <div class="dateNumber">16</div>
  <div class="dateMonth">OCTOBER</div>
  <div class="dateLine"></div>
  <div class="dateText">SOME DAYS DESERVE TO BE REMEMBERED</div>
</div>

<!-- CINEMATIC INTRO -->
<div id="movie" class="screen">
  <div class="movieTop">MEMORY ARCHIVE / 001</div>
  <div class="movieCenter">
    <div class="movieSmall">BEFORE WE GET THERE...</div>
    <div class="movieText" id="movieText">SOME MEMORIES<br>NEVER DISAPPEAR.</div>
  </div>
</div>

<!-- TIME REWIND -->
<div id="yearScreen" class="screen">
  <div class="year" id="year">2026</div>
</div>

<!-- FOOTBALL SCENE -->
<div id="football" class="screen">
  <div class="footballText">SOME THINGS ALWAYS BRING US BACK</div>
  <div class="argentinaLine"></div>
  <div class="ball">⚽</div>
</div>

<!-- MEMORY NOTES -->
<div id="memory">
  <div class="memoryGlow"></div>

  <div class="note active">
    <div class="noteNumber">16 OCTOBER — 01</div>
    <div class="noteIcon">✦</div>
    <div class="noteTitle">BHAI.</div>
    <div class="noteText">So...

It's October 16.

Another year just quietly
became part of your story.

No giant speech.
No fake deep words.

Just one thing—

I'm genuinely glad
that somewhere along the way,

life gave me a person
I can call my bhai.

And somehow...

this day became worth
making something for.</div>
    <div class="noteSignature">— SABIT 💙</div>
  </div>

  <div class="note">
    <div class="noteNumber">MEMORY FILE — 02</div>
    <div class="noteIcon">∞</div>
    <div class="noteTitle">REMEMBER?</div>
    <div class="noteText">Maybe you don't remember
every little moment.

Neither do I.

But that's the funny thing
about memories.

They don't ask permission
before becoming important.

A random conversation.

A stupid joke.

A football argument.

One completely normal day
that somehow stayed with us.

We didn't know it then...

but those were the days
we'd eventually miss.</div>
    <div class="noteSignature">SOME MEMORIES JUST STAY.</div>
  </div>

  <div class="note">
    <div class="noteNumber">CHAPTER 03</div>
    <div class="noteIcon">⚡</div>
    <div class="noteTitle">KEEP THAT FIRE.</div>
    <div class="noteText">Bhai...

Don't become someone else
just because life gets harder.

Keep the jokes.

Keep the madness.

Keep chasing the things
that make you excited.

There will be days
when things don't work.

Days when plans fail.

Days when you question
where you're even going.

It's okay.

You don't need to have
the whole story figured out.

Just don't stop writing it.</div>
    <div class="noteSignature">YOUR STORY ISN'T OVER.</div>
  </div>

  <div class="note">
    <div class="noteNumber">LOADING... — 04</div>
    <div class="noteIcon">10</div>
    <div class="noteTitle">NEXT CHAPTER.</div>
    <div class="noteText">Imagine us years from now.

Different place.

Different life.

Different problems.

And somehow...

one random conversation
brings us back here.

October 16.

These days.

These jokes.

These stupid little moments.

We'll probably laugh.

Maybe we'll say,

"Bro, we really thought
those were the good old days."

And maybe...

we'll finally realize
they actually were.</div>
    <div class="noteSignature">FUTURE US WILL REMEMBER THIS.</div>
  </div>

  <div class="note">
    <div class="noteNumber">FINAL MESSAGE — 05</div>
    <div class="noteIcon">💙</div>
    <div class="noteTitle">HAPPY BIRTHDAY, BHAI.</div>
    <div class="noteText">No matter where life takes you...

I hope you never forget
the version of yourself
that started this journey.

Keep moving.

Keep laughing.

Keep dreaming.

Keep making memories
you won't need a camera
to remember.

And when another October 16
comes around...

I hope we can look back
at this moment and laugh.

Because today isn't just
another birthday.

It's another page
in your story.

And bhai...

the best pages
haven't been written yet.</div>
    <div class="noteSignature">— SABIT ❤️</div>
  </div>

  <div class="noteHint">SWIPE OR USE THE ARROWS</div>
  <div class="controls">
    <button type="button" id="prevBtn" aria-label="Previous note">‹</button>
    <button type="button" id="nextBtn" aria-label="Next note">›</button>
  </div>
</div>

<!-- FINAL REVEAL -->
<div id="final" class="screen">
  <div class="finalNumber">10</div>
  <div class="finalTitle">HAPPY BIRTHDAY <span>SHAN</span></div>
  <div class="flag">
    <div class="blue"></div><div class="white"></div><div class="blue"></div>
  </div>
  <div class="finalLine"></div>
  <div class="finalWish">
    Another year added to the story.<br>
    Whatever comes next...<br>
    make it unforgettable.
  </div>
  <div class="finalSign">— SABIT 💙</div>
  <button class="restart" id="restartBtn" type="button">WATCH AGAIN ↻</button>
</div>

<script>
/* Stars */
const stars = document.getElementById("stars");
for (let i = 0; i < 100; i++) {
  const star = document.createElement("div");
  star.className = "star";
  star.style.left = Math.random() * 100 + "%";
  star.style.top = Math.random() * 100 + "%";
  star.style.animationDelay = Math.random() * 4 + "s";
  star.style.animationDuration = 2 + Math.random() * 4 + "s";
  stars.appendChild(star);
}

/* Screens */
const screenIds = ["intro", "dateScreen", "movie", "yearScreen", "football", "final"];
const screens = Object.fromEntries(
  screenIds.map(id => [id, document.getElementById(id)])
);
const memory = document.getElementById("memory");
const flash = document.getElementById("flash");
const notes = [...document.querySelectorAll(".note")];
const countEl = document.getElementById("count");
const yearEl = document.getElementById("year");
const movieText = document.getElementById("movieText");
const ball = document.querySelector(".ball");

let timers = [];
let noteIndex = 0;
let runId = 0;

function later(fn, delay) {
  const id = setTimeout(fn, delay);
  timers.push(id);
  return id;
}

function clearTimers() {
  timers.forEach(clearTimeout);
  timers = [];
}

function isCurrent(id) {
  return id === runId;
}

function hideScreens() {
  Object.values(screens).forEach(s => s.classList.remove("active"));
  memory.classList.remove("active");
}

function showScreen(name) {
  hideScreens();
  screens[name].classList.add("active");
}

function replayAnimation(element, animation) {
  element.style.animation = "none";
  void element.offsetWidth;
  element.style.animation = animation;
}

/* Countdown */
function startExperience() {
  clearTimers();
  runId++;
  const id = runId;
  noteIndex = 0;
  hideScreens();
  showScreen("intro");

  let number = 3;

  function tick() {
    if (!isCurrent(id)) return;

    countEl.textContent = number > 0 ? "0" + number : "00";
    replayAnimation(countEl, "countIn .8s ease both");
    number--;

    if (number >= 0) {
      later(tick, 1000);
    } else {
      later(() => showDate(id), 900);
    }
  }

  countEl.textContent = "03";
  replayAnimation(countEl, "countIn .8s ease both");
  later(tick, 1000);
}

/* Date */
function showDate(id) {
  if (!isCurrent(id)) return;
  showScreen("dateScreen");

  flash.classList.remove("flashActive");
  void flash.offsetWidth;
  flash.classList.add("flashActive");

  later(() => {
    if (!isCurrent(id)) return;
    showScreen("movie");
    later(() => startYears(id), 2600);
  }, 3000);
}

/* Years rewind */
const years = ["2026", "2022", "2019", "2016"];

function startYears(id) {
  if (!isCurrent(id)) return;
  showScreen("yearScreen");
  let index = 0;

  function nextYear() {
    if (!isCurrent(id)) return;

    yearEl.textContent = years[index];
    replayAnimation(yearEl, "countIn .8s ease both");
    index++;

    if (index < years.length) {
      later(nextYear, 900);
    } else {
      later(() => startMessage(id), 1300);
    }
  }

  nextYear();
}

/* Cinematic message */
function startMessage(id) {
  if (!isCurrent(id)) return;
  showScreen("movie");
  movieText.innerHTML = "SOME MEMORIES<br>NEVER DISAPPEAR.";
  replayAnimation(movieText, "fadeUp .9s ease both");
  later(() => startFootball(id), 2600);
}

/* Football */
function startFootball(id) {
  if (!isCurrent(id)) return;
  showScreen("football");
  replayAnimation(ball, "rollBall 3.8s cubic-bezier(.2,.7,.3,1) forwards");
  later(() => startNotes(id), 4000);
}

/* Notes */
function startNotes(id) {
  if (!isCurrent(id)) return;
  hideScreens();
  memory.classList.add("active");
  noteIndex = 0;
  loadNote();
}

function loadNote() {
  notes.forEach((note, index) => {
    note.classList.toggle("active", index === noteIndex);
  });
  document.getElementById("prevBtn").style.opacity =
    noteIndex === 0 ? ".45" : "1";
  document.getElementById("prevBtn").disabled = noteIndex === 0;
}

function nextNote() {
  if (!memory.classList.contains("active")) return;
  if (noteIndex < notes.length - 1) {
    noteIndex++;
    loadNote();
  } else {
    showFinal();
  }
}

function previousNote() {
  if (!memory.classList.contains("active") || noteIndex === 0) return;
  noteIndex--;
  loadNote();
}

/* Final screen */
function showFinal() {
  memory.classList.remove("active");
  later(() => {
    if (memory.classList.contains("active")) return;
    showScreen("final");
  }, 550);
}

/* Buttons and touch */
document.getElementById("nextBtn").addEventListener("click", nextNote);
document.getElementById("prevBtn").addEventListener("click", previousNote);
document.getElementById("restartBtn").addEventListener("click", startExperience);

let touchStartX = 0;
let touchStartY = 0;

memory.addEventListener("touchstart", e => {
  touchStartX = e.changedTouches[0].clientX;
  touchStartY = e.changedTouches[0].clientY;
}, {passive: true});

memory.addEventListener("touchend", e => {
  const dx = touchStartX - e.changedTouches[0].clientX;
  const dy = touchStartY - e.changedTouches[0].clientY;

  if (Math.abs(dx) > 55 && Math.abs(dx) > Math.abs(dy)) {
    if (dx > 0) nextNote();
    else previousNote();
  }
}, {passive: true});

/* Start */
startExperience();
</script>
</body>
</html>
