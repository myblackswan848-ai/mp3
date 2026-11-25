
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>For Saawera — My Sunshine ☀️</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,500;0,600;0,700;1,400;1,600&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&family=Caveat:wght@500;600;700&display=swap" rel="stylesheet">
  <style>
    * { box-sizing: border-box; }
    body {
      font-family: 'Plus Jakarta Sans', sans-serif;
      background: radial-gradient(circle at 50% 0%, #451a2b 0%, #240b1c 45%, #0f0614 100%);
      color: #fff1f2;
      min-height: 100vh;
      overflow-x: hidden;
    }
    .font-serif-luxury { font-family: 'Cormorant Garamond', serif; }
    .font-handwritten { font-family: 'Caveat', cursive; }

    #starlightCanvas {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 1;
    }

    .luxury-glass {
      background: rgba(25, 12, 30, 0.74);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border: 1px solid rgba(251, 191, 36, 0.18);
      box-shadow: 0 24px 60px -15px rgba(0, 0, 0, 0.7), inset 0 1px 0 0 rgba(255, 255, 255, 0.08);
    }
    .luxury-glass-warm {
      background: linear-gradient(145deg, rgba(48, 17, 34, 0.85) 0%, rgba(24, 10, 26, 0.9) 100%);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border: 1px solid rgba(251, 191, 36, 0.28);
      box-shadow: 0 25px 65px -12px rgba(244, 63, 94, 0.18);
    }
    .parchment-letter {
      background: linear-gradient(165deg, #fffdf9 0%, #fff4e6 55%, #ffe8d6 100%);
      color: #2b0918;
      box-shadow: 0 30px 70px rgba(0, 0, 0, 0.65), inset 0 0 40px rgba(245, 158, 11, 0.12);
    }

    /* 3D Flip Cards */
    .flip-scene { perspective: 1100px; }
    .flip-card-inner {
      position: relative;
      width: 100%;
      min-height: 230px;
      transition: transform 0.75s cubic-bezier(0.22, 1, 0.36, 1);
      transform-style: preserve-3d;
    }
    .flip-scene.is-flipped .flip-card-inner { transform: rotateY(180deg); }
    .flip-face {
      position: absolute;
      inset: 0;
      backface-visibility: hidden;
      -webkit-backface-visibility: hidden;
      border-radius: 1.5rem;
      padding: 1.5rem;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }
    .flip-face-back { transform: rotateY(180deg); }

    /* Animations */
    @keyframes sunOrbPulse {
      0%, 100% {
        box-shadow: 0 0 35px 8px rgba(251, 191, 36, 0.45), 0 0 90px 25px rgba(244, 63, 94, 0.25);
        transform: scale(1);
      }
      50% {
        box-shadow: 0 0 55px 18px rgba(251, 191, 36, 0.7), 0 0 120px 40px rgba(244, 63, 94, 0.38);
        transform: scale(1.04);
      }
    }
    @keyframes vinylSpin {
      from { transform: rotate(0deg); }
      to { transform: rotate(360deg); }
    }
    @keyframes candleFlicker {
      0%, 100% { transform: scale(1) rotate(-1.5deg); opacity: 0.95; }
      33% { transform: scale(1.08, 0.94) rotate(2deg); opacity: 1; }
      66% { transform: scale(0.94, 1.1) rotate(-1deg); opacity: 0.9; }
    }
    @keyframes pageReveal {
      from { opacity: 0; transform: translateY(20px) scale(0.99); }
      to { opacity: 1; transform: translateY(0) scale(1); }
    }
    @keyframes floatSoft {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-10px); }
    }
    @keyframes pulseRipple {
      0% { transform: scale(0.9); opacity: 0.8; }
      100% { transform: scale(2.1); opacity: 0; }
    }

    .sun-orb { animation: sunOrbPulse 3s ease-in-out infinite; }
    .vinyl-spinning { animation: vinylSpin 5s linear infinite; }
    .flame-anim { animation: candleFlicker 0.85s ease-in-out infinite; transform-origin: bottom center; }
    .page-transition { animation: pageReveal 0.55s cubic-bezier(0.16, 1, 0.3, 1) forwards; }
    .float-soft { animation: floatSoft 4s ease-in-out infinite; }
    .ripple-ring { animation: pulseRipple 1.6s cubic-bezier(0, 0.2, 0.8, 1) infinite; }

    /* Scratch Card Canvas */
    #scratchCanvas {
      touch-action: none;
      cursor: crosshair;
    }

    ::-webkit-scrollbar { width: 6px; }
    ::-webkit-scrollbar-track { background: #0d0612; }
    ::-webkit-scrollbar-thumb { background: #881337; border-radius: 9999px; }
  </style>
</head>
<body class="selection:bg-amber-400 selection:text-rose-950">

  <canvas id="starlightCanvas"></canvas>
  <audio id="sunshineAudio" preload="auto"></audio>

  <!-- ========================================================= -->
  <!-- ENTRY GATE OVERLAY: MUSIC GATE + PERSONAL RIDDLE LOCK     -->
  <!-- ========================================================= -->
  <div id="entryGateOverlay" class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-[#0b0410]/95 backdrop-blur-xl">
    <div class="max-w-md w-full luxury-glass-warm rounded-[2.25rem] p-7 sm:p-9 text-center space-y-6 border-2 border-amber-400/35 shadow-2xl">

      <!-- Step 1: Musical Surprise Gate -->
      <div id="gateStepMusic" class="space-y-5">
        <div class="w-20 h-20 mx-auto rounded-full bg-gradient-to-tr from-amber-400 via-rose-500 to-pink-500 flex items-center justify-center text-4xl shadow-xl sun-orb">
          🎵
        </div>
        <div>
          <p class="text-[11px] uppercase tracking-[0.3em] text-amber-300 font-bold">A Musical Apology Awaits</p>
          <h1 class="font-serif-luxury text-3xl sm:text-4xl font-bold text-white mt-1.5">
            Celebrate <span class="italic text-amber-300">Saawera</span> with Music?
          </h1>
          <p class="text-xs sm:text-sm text-rose-100/80 mt-2 leading-relaxed">
            Turn on the music before you step inside—I picked three songs just for my Sunshine.
          </p>
        </div>
        <div class="flex flex-col gap-2.5 pt-1">
          <button id="gateStartMusicBtn" type="button" class="w-full py-3.5 rounded-full bg-gradient-to-r from-amber-400 via-amber-500 to-rose-500 hover:from-amber-300 hover:to-rose-400 text-rose-950 font-extrabold text-sm shadow-xl transition transform active:scale-95">
            🔊 Start with Music ☀️
          </button>
          <button id="gateQuietBtn" type="button" class="w-full py-2.5 rounded-full bg-white/10 hover:bg-white/15 text-rose-200 text-xs font-semibold transition">
            Continue Without Sound
          </button>
        </div>
      </div>

      <!-- Step 2: Personal Riddle Lock -->
      <div id="gateStepRiddle" class="hidden space-y-5 page-transition">
        <div class="w-16 h-16 mx-auto rounded-full bg-gradient-to-br from-rose-600 to-amber-500 flex items-center justify-center text-3xl shadow-lg border-2 border-amber-200">
          🔐
        </div>
        <div>
          <p class="text-[11px] uppercase tracking-[0.3em] text-amber-300 font-bold">Golden Diary Lock</p>
          <h2 class="font-serif-luxury text-2xl sm:text-3xl font-bold text-white mt-1">
            Only One Girl Can Open This
          </h2>
          <p class="text-xs sm:text-sm text-rose-100/85 mt-2">
            Answer this riddle to break the seal:<br/>
            <strong class="text-amber-300">"What's the nickname your idiot best friend always calls you?"</strong>
          </p>
        </div>

        <div class="space-y-2.5">
          <input id="riddleAnswerInput" type="text" placeholder="Type the secret nickname..." class="w-full px-4 py-3 rounded-full bg-white/10 border border-amber-300/40 text-center text-white placeholder-rose-200/50 text-sm focus:outline-none focus:ring-2 focus:ring-amber-400" />
          <p id="riddleFeedback" class="hidden text-xs font-medium text-amber-200 bg-rose-950/70 px-3 py-2 rounded-xl border border-amber-400/25"></p>
          <button id="unlockRiddleBtn" type="button" class="w-full py-3.5 rounded-full bg-gradient-to-r from-amber-400 to-rose-500 hover:from-amber-300 hover:to-rose-400 text-rose-950 font-extrabold text-sm shadow-xl transition">
            🗝️ Unlock My Sunshine's Site
          </button>
          <button id="riddleHintBtn" type="button" class="text-xs text-rose-300 hover:text-amber-200 underline pt-1">
            Need a hint? (Starts with S... ☀️)
          </button>
        </div>
      </div>

    </div>
  </div>

  <!-- Toast Banner -->
  <div id="toastBanner" class="fixed top-20 left-1/2 -translate-x-1/2 z-50 hidden max-w-md w-[90%] luxury-glass-warm text-amber-100 px-5 py-3 rounded-full shadow-2xl border border-amber-400/50 flex items-center justify-between gap-3">
    <span id="toastMessage" class="text-xs sm:text-sm font-medium">✨</span>
    <button id="dismissToastBtn" type="button" class="text-amber-300 hover:text-white text-xs font-bold uppercase tracking-wider">OK</button>
  </div>

  <!-- ========================================================= -->
  <!-- TOP NAVIGATION BAR                                        -->
  <!-- ========================================================= -->
  <header class="sticky top-0 z-40 backdrop-blur-xl bg-[#110718]/80 border-b border-amber-400/15">
    <div class="max-w-5xl mx-auto px-4 sm:px-6 py-3 flex flex-col md:flex-row md:items-center md:justify-between gap-3">
      <div class="flex items-center justify-between">
        <button type="button" data-nav="home" class="site-nav-trigger flex items-center gap-3 text-left focus:outline-none">
          <div class="w-10 h-10 rounded-full bg-gradient-to-tr from-amber-500 via-rose-500 to-pink-500 flex items-center justify-center shadow-lg">
            <span class="text-lg">☀️</span>
          </div>
          <div>
            <span class="font-serif-luxury italic text-xl sm:text-2xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-amber-200 via-amber-400 to-rose-300">
              Saawera
            </span>
            <span class="block text-[10px] uppercase tracking-[0.25em] text-rose-300/70">My Sunshine • 3 Years</span>
          </div>
        </button>

        <button id="mobileMusicBtn" type="button" class="md:hidden px-3 py-1.5 rounded-full text-xs font-semibold bg-amber-500/15 border border-amber-400/30 text-amber-200 flex items-center gap-1.5">
          <span class="music-state-icon">🎶</span>
          <span class="music-state-label">Play</span>
        </button>
      </div>

      <nav aria-label="Chapters" class="flex items-center gap-1 sm:gap-2 overflow-x-auto pb-1 md:pb-0">
        <button type="button" data-nav="home" class="site-nav-trigger nav-link px-3.5 py-1.5 rounded-full text-xs font-semibold transition whitespace-nowrap bg-gradient-to-r from-amber-500 to-rose-500 text-rose-950 shadow-md">
          I. Sunbeam Letter
        </button>
        <button type="button" data-nav="constellation" class="site-nav-trigger nav-link px-3.5 py-1.5 rounded-full text-xs font-semibold transition whitespace-nowrap text-rose-200/80 hover:text-amber-200 hover:bg-white/5">
          II. Stars &amp; Quiz
        </button>
        <button type="button" data-nav="truth" class="site-nav-trigger nav-link px-3.5 py-1.5 rounded-full text-xs font-semibold transition whitespace-nowrap text-rose-200/80 hover:text-amber-200 hover:bg-white/5">
          III. My Stupid Brain
        </button>
        <button type="button" data-nav="wishes" class="site-nav-trigger nav-link px-3.5 py-1.5 rounded-full text-xs font-semibold transition whitespace-nowrap text-rose-200/80 hover:text-amber-200 hover:bg-white/5">
          IV. 3 Birthday Wishes
        </button>
        <button type="button" data-nav="promise" class="site-nav-trigger nav-link px-3.5 py-1.5 rounded-full text-xs font-semibold transition whitespace-nowrap text-rose-200/80 hover:text-amber-200 hover:bg-white/5">
          V. Maan Jao Na
        </button>
      </nav>
    </div>
  </header>

  <!-- ========================================================= -->
  <!-- MAIN 5-PAGE INTERACTIVE EXPERIENCE                        -->
  <!-- ========================================================= -->
  <main class="relative z-10 max-w-5xl mx-auto px-4 sm:px-6 pt-8 pb-32">

    <!-- ======================================================= -->
    <!-- PAGE I: SUNBEAM CATCHER & SCRATCH-OFF CONFESSION LETTER -->
    <!-- ======================================================= -->
    <section id="page-home" class="story-page page-transition space-y-10">

      <!-- Hero Card -->
      <div class="relative rounded-[2.25rem] luxury-glass-warm p-8 sm:p-12 text-center overflow-hidden border border-amber-400/25">
        <p class="text-xs uppercase tracking-[0.35em] text-amber-300/90 font-semibold mb-4">
          Three Years of Best Friendship • One Unhidden Crush
        </p>

        <div class="my-5 flex justify-center">
          <button id="awakenSunshineBtn" type="button" class="sun-orb w-24 h-24 sm:w-28 sm:h-28 rounded-full bg-gradient-to-tr from-rose-500 via-amber-400 to-yellow-200 flex flex-col items-center justify-center text-rose-950 shadow-2xl transition transform hover:scale-105 active:scale-95 focus:outline-none">
            <span class="text-3xl">☀️</span>
            <span class="text-[10px] font-extrabold uppercase tracking-wider mt-1">Sunshine</span>
          </button>
        </div>

        <h1 class="font-serif-luxury text-4xl sm:text-6xl font-bold text-white leading-[1.1]">
          I Forgot the Date,<br/>
          <span class="italic font-normal text-transparent bg-clip-text bg-gradient-to-r from-amber-200 via-amber-400 to-rose-300">
            Never the Girl Who Is My Sunshine.
          </span>
        </h1>

        <p class="mt-4 text-sm sm:text-base text-rose-100/85 max-w-2xl mx-auto leading-relaxed">
          Saawera, you think I don't care enough because I missed your birthday for three years straight. Every paragraph of my confession below is hidden behind glowing sunbeams—catch all three sunbeams to unlock my letter.
        </p>
      </div>

      <!-- Interactive Sunbeam Catcher + Unlockable Parchment Paragraphs -->
      <div class="parchment-letter rounded-[2rem] p-6 sm:p-11 space-y-6 border-2 border-amber-300/80">
        <div class="flex flex-wrap items-center justify-between gap-2 border-b border-rose-900/15 pb-4">
          <div>
            <span class="text-[11px] font-bold uppercase tracking-[0.25em] text-rose-800/70">Sunbeam Treasure Hunt</span>
            <h2 class="font-serif-luxury text-2xl sm:text-4xl font-bold text-rose-950 mt-0.5">Catch the 3 Sunbeams to Reveal My Letter ☀️</h2>
          </div>
          <span id="sunbeamsCaughtBadge" class="px-3.5 py-1 rounded-full bg-rose-900 text-amber-200 text-xs font-bold">
            0 / 3 Caught
          </span>
        </div>

        <!-- 3 Interactive Sunbeam Buttons -->
        <div class="grid grid-cols-1 sm:grid-cols-3 gap-3">
          <button type="button" data-beam="0" class="sunbeam-catch-btn p-4 rounded-2xl bg-gradient-to-r from-amber-200 via-amber-100 to-rose-100 border-2 border-amber-400 text-rose-950 font-bold text-xs sm:text-sm shadow-md hover:scale-[1.02] transition flex items-center justify-center gap-2">
            <span class="text-xl float-soft">☀️</span>
            <span>Catch Sunbeam #1</span>
          </button>
          <button type="button" data-beam="1" class="sunbeam-catch-btn p-4 rounded-2xl bg-gradient-to-r from-amber-200 via-amber-100 to-rose-100 border-2 border-amber-400 text-rose-950 font-bold text-xs sm:text-sm shadow-md hover:scale-[1.02] transition flex items-center justify-center gap-2">
            <span class="text-xl float-soft">✨</span>
            <span>Catch Sunbeam #2</span>
          </button>
          <button type="button" data-beam="2" class="sunbeam-catch-btn p-4 rounded-2xl bg-gradient-to-r from-amber-200 via-amber-100 to-rose-100 border-2 border-amber-400 text-rose-950 font-bold text-xs sm:text-sm shadow-md hover:scale-[1.02] transition flex items-center justify-center gap-2">
            <span class="text-xl float-soft">💛</span>
            <span>Catch Sunbeam #3</span>
          </button>
        </div>

        <!-- Paragraphs Revealed by Catching Sunbeams -->
        <div class="space-y-4 font-serif-luxury text-base sm:text-lg text-rose-950/90 leading-relaxed">
          <div id="beamPara-0" class="hidden p-4 rounded-2xl bg-white/75 border-l-4 border-amber-500 page-transition">
            <p class="italic text-xl text-rose-900 mb-1">"Galti se mistake nahi... yeh toh teen saal ka blunder ho gaya mujhse."</p>
            <p>
              If I were in your place—after <strong>three whole years</strong> of being best friends—and the guy who literally calls me <em>Sunshine</em>, the guy who doesn't even hide how massive of a crush he has on me, forgot my birthday for the third time in a row... I would think he didn't care enough either.
            </p>
          </div>

          <div id="beamPara-1" class="hidden p-4 rounded-2xl bg-white/75 border-l-4 border-rose-500 page-transition">
            <p>
              I won't make fake excuses or pretend I wasn't an idiot. I messed up the one day of the year that celebrates the girl I adore most. And knowing that my stupidity made you feel like you don't matter to me hurts more than anything else.
            </p>
          </div>

          <div id="beamPara-2" class="hidden p-4 rounded-2xl bg-white/75 border-l-4 border-pink-500 page-transition">
            <p>
              Because here is the truth, Saawera: my brain is terrible at holding onto calendar dates simply because I don't think of you once a year. <strong>I think of you every single day.</strong> I remember the sound of your laugh, the way your mood shifts in two seconds, the stories you tell me, and how my whole day gets brighter the moment you talk to me.
            </p>
          </div>
        </div>

        <!-- Interactive Scratch-Off Secret Note -->
        <div class="pt-3 border-t border-rose-900/15 space-y-2.5">
          <div class="flex items-center justify-between">
            <p class="text-xs font-extrabold uppercase tracking-wider text-rose-800">🪙 Scratch the Gold Foil Below for My Secret Postscript:</p>
            <button id="revealScratchInstantBtn" type="button" class="text-[11px] font-bold text-rose-700 underline">Tap to reveal</button>
          </div>
          <div class="relative h-28 rounded-2xl overflow-hidden border-2 border-amber-400 bg-rose-950 flex items-center justify-center p-4 text-center">
            <p class="font-serif-luxury italic text-lg sm:text-xl text-amber-200 select-none">
              "You aren't a date on a calendar to me, Saawera. You're my favorite part of every ordinary day. ☀️💖"
            </p>
            <canvas id="scratchCanvas" class="absolute inset-0 w-full h-full"></canvas>
          </div>
        </div>

        <div class="pt-3 flex items-center justify-between">
          <p class="font-handwritten text-2xl sm:text-3xl text-rose-900">Your Idiot Best Friend ☀️</p>
          <button type="button" data-nav="constellation" class="site-nav-trigger px-6 py-3 rounded-full bg-rose-900 hover:bg-rose-950 text-amber-100 text-xs sm:text-sm font-bold shadow-lg transition">
            II. Light Up S·A·A·W·E·R·A →
          </button>
        </div>
      </div>
    </section>

    <!-- ======================================================= -->
    <!-- PAGE II: S·A·A·W·E·R·A CONSTELLATION & MINI MEMORY QUIZ -->
    <!-- ======================================================= -->
    <section id="page-constellation" class="story-page hidden page-transition space-y-10">

      <!-- S-A-A-W-E-R-A Constellation -->
      <div class="luxury-glass-warm rounded-[2.25rem] p-7 sm:p-10 space-y-6">
        <div class="flex flex-col sm:flex-row sm:items-end justify-between gap-3 border-b border-amber-400/20 pb-4">
          <div>
            <span class="text-xs uppercase tracking-[0.3em] text-amber-300 font-semibold">Chapter II • Written in the Sky</span>
            <h2 class="font-serif-luxury text-3xl sm:text-5xl font-bold text-white mt-1">
              The Constellation of <span class="text-amber-300 italic">S·A·A·W·E·R·A</span>
            </h2>
          </div>
          <span id="starsLitBadge" class="px-4 py-1.5 rounded-full bg-amber-400/15 border border-amber-400/30 text-amber-200 text-xs font-bold self-start sm:self-auto">
            1 / 7 Stars Illuminated
          </span>
        </div>

        <p class="text-sm text-rose-100/80">
          Tap every star in your name to connect the constellation and read the seven things about you that live permanently in my heart:
        </p>

        <div id="saaweraStarsBar" class="grid grid-cols-7 gap-2 sm:gap-3"></div>

        <div class="relative h-52 sm:h-60 w-full rounded-3xl bg-[#09040e] border border-amber-400/25 overflow-hidden">
          <canvas id="constellationCanvas" class="w-full h-full block cursor-pointer"></canvas>
        </div>

        <div class="rounded-3xl bg-gradient-to-r from-amber-500/15 via-rose-500/15 to-pink-500/15 border border-amber-300/40 p-6 space-y-2">
          <span id="starLetterTag" class="text-xs font-extrabold uppercase tracking-[0.25em] text-amber-300"></span>
          <h3 id="starTitle" class="font-serif-luxury text-2xl sm:text-3xl font-bold text-white"></h3>
          <p id="starDescription" class="text-sm sm:text-base text-rose-100/90 leading-relaxed"></p>
        </div>
      </div>

      <!-- Interactive Mini "Do I Actually Know You?" Quiz -->
      <div class="luxury-glass rounded-[2.25rem] p-7 sm:p-10 space-y-5 border border-amber-400/25">
        <div class="flex flex-wrap items-center justify-between gap-2 border-b border-white/10 pb-4">
          <div>
            <span class="text-xs uppercase tracking-[0.3em] text-rose-300 font-semibold">Interactive Mini-Challenge</span>
            <h3 class="font-serif-luxury text-2xl sm:text-3xl font-bold text-white mt-0.5">
              Quick Check: Why Do I Still Deserve Your Smile? 💭
            </h3>
          </div>
          <span id="quizProgressBadge" class="px-3.5 py-1 rounded-full bg-rose-500/20 border border-rose-400/30 text-rose-200 text-xs font-bold">
            Question 1 of 3
          </span>
        </div>

        <div id="quizContainer" class="space-y-4">
          <p id="quizQuestionText" class="font-serif-luxury text-xl sm:text-2xl font-bold text-amber-200"></p>
          <div id="quizOptionsGrid" class="grid grid-cols-1 sm:grid-cols-2 gap-3"></div>
          <div id="quizUnlockBox" class="hidden rounded-2xl bg-amber-500/15 border border-amber-300/40 p-4 space-y-2 page-transition">
            <p id="quizReactionText" class="text-xs font-bold uppercase tracking-wider text-amber-300"></p>
            <p id="quizUnlockedParagraph" class="text-sm text-rose-100 leading-relaxed"></p>
            <button id="nextQuizBtn" type="button" class="mt-2 px-5 py-2 rounded-full bg-amber-400 text-rose-950 text-xs font-extrabold">
              Next Question →
            </button>
          </div>
        </div>

        <div class="flex items-center justify-between pt-3">
          <button type="button" data-nav="home" class="site-nav-trigger px-5 py-2.5 rounded-full bg-white/10 hover:bg-white/15 text-rose-200 text-xs font-semibold transition">
            ← I. Sunbeam Letter
          </button>
          <button type="button" data-nav="truth" class="site-nav-trigger px-6 py-3 rounded-full bg-gradient-to-r from-amber-400 to-rose-500 text-rose-950 text-xs sm:text-sm font-bold shadow-lg transition">
            III. My Stupid Brain →
          </button>
        </div>
      </div>
    </section>

    <!-- ======================================================= -->
    <!-- PAGE III: 3D FLIP CARDS & HEARTBEAT MEMORY SCANNER      -->
    <!-- ======================================================= -->
    <section id="page-truth" class="story-page hidden page-transition space-y-10">

      <div class="luxury-glass-warm rounded-[2.25rem] p-7 sm:p-10 space-y-6">
        <div class="flex flex-col sm:flex-row sm:items-end justify-between gap-3 border-b border-amber-400/20 pb-4">
          <div>
            <span class="text-xs uppercase tracking-[0.3em] text-rose-300 font-semibold">Chapter III • The Honest Contrast</span>
            <h2 class="font-serif-luxury text-3xl sm:text-5xl font-bold text-white mt-1">
              What It Looks Like <span class="italic text-amber-300">vs.</span> What's Actually True
            </h2>
          </div>
          <span id="flippedTruthCounter" class="px-4 py-1.5 rounded-full bg-rose-500/20 border border-rose-400/30 text-rose-200 text-xs font-bold self-start sm:self-auto">
            0 / 6 Cards Revealed
          </span>
        </div>

        <p class="text-sm text-rose-100/80">
          Tap each card to flip it over and see what's actually inside my head whenever it comes to you:
        </p>

        <div id="flipCardsGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5"></div>
      </div>

      <!-- Heartbeat Pulse Memory Scanner -->
      <div class="luxury-glass rounded-[2.25rem] p-7 sm:p-10 text-center space-y-5 border border-rose-400/30">
        <span class="text-xs uppercase tracking-[0.3em] text-amber-300 font-semibold">Heartbeat Memory Scanner</span>
        <h3 class="font-serif-luxury text-2xl sm:text-4xl font-bold text-white">
          Tap the Heart to See What I Never Forget About Saawera
        </h3>
        <div class="py-3 flex flex-col items-center justify-center">
          <button id="pulseScanBtn" type="button" class="relative w-24 h-24 rounded-full bg-gradient-to-tr from-rose-600 via-pink-500 to-amber-400 text-white text-3xl flex items-center justify-center shadow-2xl transform active:scale-90 transition focus:outline-none">
            <span class="absolute inset-0 rounded-full bg-rose-500/40 ripple-ring pointer-events-none"></span>
            <span>💓</span>
          </button>
          <p id="pulseMemoryReadout" class="mt-5 font-serif-luxury italic text-xl sm:text-2xl text-amber-200 max-w-xl mx-auto min-h-[3.5rem] px-4">
            "Tap the heartbeat above..."
          </p>
        </div>

        <div class="flex items-center justify-between pt-2">
          <button type="button" data-nav="constellation" class="site-nav-trigger px-5 py-2.5 rounded-full bg-white/10 hover:bg-white/15 text-rose-200 text-xs font-semibold transition">
            ← II. Stars &amp; Quiz
          </button>
          <button type="button" data-nav="wishes" class="site-nav-trigger px-6 py-3 rounded-full bg-gradient-to-r from-amber-400 to-rose-500 text-rose-950 text-xs sm:text-sm font-bold shadow-lg transition">
            IV. Blow Your 3 Birthday Candles →
          </button>
        </div>
      </div>
    </section>

    <!-- ======================================================= -->
    <!-- PAGE IV: 3 CANDLES -> SEALED ENVELOPES -> GOLDEN KEY    -->
    <!-- ======================================================= -->
    <section id="page-wishes" class="story-page hidden page-transition space-y-10">

      <div class="luxury-glass-warm rounded-[2.25rem] p-7 sm:p-10 text-center space-y-6">
        <div class="flex flex-col sm:flex-row sm:items-end justify-between gap-3 border-b border-amber-400/20 pb-4 text-left">
          <div>
            <span class="text-xs uppercase tracking-[0.3em] text-amber-300 font-semibold">Chapter IV • Three Missed Birthdays</span>
            <h2 class="font-serif-luxury text-3xl sm:text-5xl font-bold text-white mt-1">
              Blow Out Each Candle to Unseal Its Letter 🎂
            </h2>
          </div>
          <span id="wishesBlownBadge" class="px-4 py-1.5 rounded-full bg-amber-400/15 border border-amber-400/30 text-amber-200 text-xs font-bold self-start sm:self-auto">
            0 / 3 Seals Broken
          </span>
        </div>

        <p class="text-sm text-rose-100/80 max-w-xl mx-auto">
          Each candle is tied to a wax-sealed envelope for <strong>Year 1</strong>, <strong>Year 2</strong>, and <strong>Year 3</strong>. Tap each candle to blow it out and unseal my promise for that year.
        </p>

        <!-- 3-Candle Cake -->
        <div class="py-4">
          <div class="flex items-end justify-center gap-8 sm:gap-14 mb-1">
            <button type="button" data-candle-idx="0" class="cake-candle-btn group flex flex-col items-center focus:outline-none">
              <div id="flameOrb-0" class="w-6 h-9 rounded-full bg-gradient-to-t from-orange-500 via-amber-300 to-yellow-100 shadow-[0_0_25px_rgba(251,191,36,0.9)] flame-anim mb-1"></div>
              <div class="w-8 h-20 rounded-t-xl bg-gradient-to-b from-amber-200 via-rose-400 to-rose-600 border-2 border-amber-100 flex items-center justify-center text-xs font-extrabold text-white">Yr 1</div>
              <span class="mt-2 text-xs font-semibold text-amber-200">Blow Yr 1</span>
            </button>
            <button type="button" data-candle-idx="1" class="cake-candle-btn group flex flex-col items-center focus:outline-none">
              <div id="flameOrb-1" class="w-6 h-9 rounded-full bg-gradient-to-t from-orange-500 via-amber-300 to-yellow-100 shadow-[0_0_25px_rgba(251,191,36,0.9)] flame-anim mb-1"></div>
              <div class="w-8 h-24 rounded-t-xl bg-gradient-to-b from-amber-200 via-amber-500 to-rose-600 border-2 border-amber-100 flex items-center justify-center text-xs font-extrabold text-white">Yr 2</div>
              <span class="mt-2 text-xs font-semibold text-amber-200">Blow Yr 2</span>
            </button>
            <button type="button" data-candle-idx="2" class="cake-candle-btn group flex flex-col items-center focus:outline-none">
              <div id="flameOrb-2" class="w-6 h-9 rounded-full bg-gradient-to-t from-orange-500 via-amber-300 to-yellow-100 shadow-[0_0_25px_rgba(251,191,36,0.9)] flame-anim mb-1"></div>
              <div class="w-8 h-28 rounded-t-xl bg-gradient-to-b from-amber-200 via-pink-500 to-rose-700 border-2 border-amber-100 flex items-center justify-center text-xs font-extrabold text-white">Yr 3</div>
              <span class="mt-2 text-xs font-semibold text-amber-200">Blow Yr 3</span>
            </button>
          </div>
          <div class="max-w-sm mx-auto">
            <div class="h-10 bg-gradient-to-r from-amber-200 via-rose-200 to-amber-200 rounded-t-3xl border-2 border-amber-300 flex items-center justify-around px-4">
              <span>🍓</span><span>✨</span><span>☀️</span><span>✨</span><span>🍓</span>
            </div>
            <div class="h-14 bg-gradient-to-r from-rose-700 via-rose-600 to-amber-600 rounded-b-3xl border-x-2 border-b-2 border-amber-300/80 flex items-center justify-center text-amber-100 font-serif-luxury italic text-lg font-bold shadow-2xl">
              Happy Birthday, Saawera — My Sunshine ☀️
            </div>
          </div>
        </div>

        <div class="flex flex-wrap items-center justify-center gap-3">
          <button id="blowAllCandlesBtn" type="button" class="px-6 py-2.5 rounded-full bg-gradient-to-r from-amber-400 to-rose-500 text-rose-950 font-bold text-xs sm:text-sm shadow-lg">
            🌬️ Blow Out All 3 Candles
          </button>
          <button id="relightCandlesBtn" type="button" class="px-4 py-2.5 rounded-full bg-white/10 hover:bg-white/15 text-amber-200 text-xs font-semibold">
            🔥 Relight
          </button>
        </div>

        <!-- 3 Sealed Envelopes -->
        <div id="sealedEnvelopesGrid" class="grid grid-cols-1 md:grid-cols-3 gap-4 text-left pt-2"></div>
      </div>

      <div class="flex items-center justify-between pt-2">
        <button type="button" data-nav="truth" class="site-nav-trigger px-5 py-2.5 rounded-full bg-white/10 hover:bg-white/15 text-rose-200 text-xs font-semibold transition">
          ← III. My Stupid Brain
        </button>
        <button type="button" data-nav="promise" class="site-nav-trigger px-6 py-3 rounded-full bg-gradient-to-r from-amber-400 to-rose-500 text-rose-950 text-xs sm:text-sm font-bold shadow-lg transition">
          V. Maan Jao Na, Sunshine →
        </button>
      </div>
    </section>

    <!-- ======================================================= -->
    <!-- PAGE V: MOOD SLIDER, PROMISES & HOLD-FOR-HUG FINALE     -->
    <!-- ======================================================= -->
    <section id="page-promise" class="story-page hidden page-transition space-y-10">

      <!-- Claimable Promises -->
      <div class="luxury-glass-warm rounded-[2.25rem] p-7 sm:p-10 space-y-6">
        <div class="flex flex-col sm:flex-row sm:items-end justify-between gap-3 border-b border-amber-400/20 pb-4">
          <div>
            <span class="text-xs uppercase tracking-[0.3em] text-amber-300 font-semibold">Chapter V • Three Years of Compensation</span>
            <h2 class="font-serif-luxury text-3xl sm:text-5xl font-bold text-white mt-1">
              Manaanے Ka Waada — <span class="italic text-amber-300">Everything I Owe You</span>
            </h2>
          </div>
          <span id="promisesClaimedBadge" class="px-4 py-1.5 rounded-full bg-amber-400/15 border border-amber-400/30 text-amber-200 text-xs font-bold self-start sm:self-auto">
            3 / 6 Claimed
          </span>
        </div>

        <div id="promisesGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4"></div>
      </div>

      <!-- Gussa-to-Smile Mood Slider + Hold-for-3-Seconds Heart -->
      <div class="luxury-glass rounded-[2.25rem] p-7 sm:p-11 text-center space-y-6 border-2 border-amber-400/35">
        <span class="text-xs uppercase tracking-[0.3em] text-rose-300 font-semibold">The Final Unlock</span>
        <h3 class="font-serif-luxury text-3xl sm:text-5xl font-bold text-white">
          Ab Maan Bhi Jao Na, <span class="italic text-amber-300">Saawera?</span> 🥺☀️
        </h3>

        <!-- Mood Slider -->
        <div class="max-w-lg mx-auto bg-white/5 border border-amber-400/25 rounded-3xl p-5 space-y-3">
          <div class="flex items-center justify-between text-xs font-bold">
            <span class="text-rose-300">😤 100% Gussa</span>
            <span id="moodPercentLabel" class="text-amber-300">50% Thoda Thoda Maan Rahi Hoon</span>
            <span class="text-amber-300">💖 0% Maaf Kiya</span>
          </div>
          <input id="moodSlider" type="range" min="0" max="100" value="50" class="w-full accent-amber-400 cursor-pointer h-2.5 rounded-lg" />
          <p id="moodHindiQuote" class="font-serif-luxury italic text-base sm:text-lg text-amber-200 pt-1">
            "Thoda sa gussa kam hua? Bas ek smile de do, saari duniya jeet lunga main..."
          </p>
        </div>

        <!-- Press & Hold Heart OR Dodging Still Mad Button -->
        <div class="space-y-4 pt-2">
          <p class="text-xs text-rose-200/80">
            Press &amp; hold the glowing heart for <strong>2 seconds</strong> (or tap <strong>Maaf Kiya</strong>) to unlock my final promise:
          </p>

          <div class="flex flex-col sm:flex-row items-center justify-center gap-4">
            <button id="holdHugBtn" type="button" class="relative overflow-hidden px-8 py-4 rounded-full bg-gradient-to-r from-amber-400 via-amber-500 to-rose-500 text-rose-950 font-extrabold text-sm sm:text-base shadow-2xl transition select-none">
              <span id="holdProgressFill" class="absolute inset-y-0 left-0 bg-white/40 w-0 pointer-events-none transition-none"></span>
              <span id="holdHugLabel" class="relative z-10">💖 Hold / Tap: Maaf Kiya, Idiot!</span>
            </button>

            <button id="stillAngryBtn" type="button" class="px-6 py-3.5 rounded-full bg-white/10 hover:bg-white/15 border border-rose-300/30 text-rose-200 font-semibold text-xs sm:text-sm transition">
              😤 Abhi Bhi Gussa Hoon!
            </button>
          </div>
        </div>

        <!-- Final Unlocked Paragraph -->
        <div id="forgivenCelebrationCard" class="hidden mt-4 rounded-3xl bg-gradient-to-br from-amber-500/20 via-rose-500/20 to-pink-500/20 border-2 border-amber-300 p-7 sm:p-9 space-y-4 text-center shadow-2xl page-transition">
          <div class="text-4xl sm:text-5xl">☀️👑💖</div>
          <h4 class="font-serif-luxury text-3xl sm:text-4xl font-bold text-white">
            Thank You, My Sunshine!
          </h4>
          <p class="text-sm sm:text-base text-rose-100/90 max-w-lg mx-auto leading-relaxed">
            Happy Birthday, Saawera—for Year 1, Year 2, Year 3, and every single year ahead of us. Three years of being your best friend is just the beginning, and I promise I will never let you feel forgotten ever again. Get ready to be spoiled properly!
          </p>
          <p class="font-handwritten text-2xl sm:text-3xl text-amber-300">
            Always yours, always in your corner ☀️
          </p>
        </div>

        <div class="flex items-center justify-between pt-3">
          <button type="button" data-nav="wishes" class="site-nav-trigger px-5 py-2.5 rounded-full bg-white/10 hover:bg-white/15 text-rose-200 text-xs font-semibold transition">
            ← IV. 3 Birthday Wishes
          </button>
          <button type="button" data-nav="home" class="site-nav-trigger px-5 py-2.5 rounded-full bg-amber-400/20 hover:bg-amber-400/30 text-amber-200 text-xs font-semibold transition">
            ☀️ Back to The Sunrise
          </button>
        </div>
      </div>
    </section>

  </main>



  <!-- ========================================================= -->
  <!-- PERSISTENT SUNSHINE MP3 VINYL PLAYER                      -->
  <!-- ========================================================= -->
  <footer class="fixed bottom-0 inset-x-0 z-40 backdrop-blur-xl bg-[#0c0513]/92 border-t border-amber-400/20">
    <div class="max-w-5xl mx-auto px-3 sm:px-6 py-2.5 flex items-center justify-between gap-3">
      <div class="flex items-center gap-3 min-w-0">
        <button id="vinylPlayBtn" type="button" class="w-10 h-10 rounded-full bg-gradient-to-tr from-stone-900 via-rose-950 to-stone-800 border-2 border-amber-400 flex items-center justify-center shadow-lg shrink-0" title="Play / Pause">
          <div id="vinylDisc" class="w-full h-full rounded-full flex items-center justify-center">
            <div class="w-3.5 h-3.5 rounded-full bg-gradient-to-r from-amber-400 to-rose-500 flex items-center justify-center text-[8px]">☀️</div>
          </div>
        </button>
        <div class="min-w-0">
          <span id="nowPlayingBadge" class="text-[10px] font-bold uppercase tracking-widest text-amber-400 block">Sunshine's Soundtrack</span>
          <p id="currentSongTitle" class="text-xs sm:text-sm font-serif-luxury italic text-rose-100 truncate">
            Elliot James Reay — I Think They Call This Love
          </p>
        </div>
      </div>

      <div class="flex items-center gap-2 shrink-0">
        <select id="songSelector" aria-label="Select Song" class="bg-white/10 border border-amber-400/30 text-amber-100 text-xs rounded-full px-3 py-1.5 focus:outline-none max-w-[165px] sm:max-w-none">
          <option value="0" class="bg-rose-950">1. I Think They Call This Love</option>
          <option value="1" class="bg-rose-950">2. Ed Sheeran — Perfect</option>
          <option value="2" class="bg-rose-950">3. I Wanna Be Yours</option>
        </select>
        <button id="mainPlayToggleBtn" type="button" class="px-4 py-1.5 rounded-full bg-gradient-to-r from-amber-400 to-rose-500 text-rose-950 font-bold text-xs shadow">
          <span class="music-state-label">▶ Play</span>
        </button>
      </div>
    </div>
  </footer>

  <script>
    (function () {
      const state = {
        musicPlaying: false,
        usingLocalMp3: false,
        selectedSongIndex: 0,
        caughtBeams: [false, false, false],
        scratchRevealed: false,
        activeStarIndex: 0,
        starsVisited: [true, false, false, false, false, false, false],
        quizStep: 0,
        pulseTapIndex: 0,
        candlesBlown: [false, false, false],
        pleaStep: 0,
        saaweraStars: [
          { letter: "S", tag: "Star 1 of 7 • S is for Sunshine", title: "Sunshine — Because You Brighten My World", desc: "No matter how heavy a day feels, the moment your name pops up, everything feels lighter. That's why I call you Sunshine.", xRatio: 0.12, yRatio: 0.62 },
          { letter: "A", tag: "Star 2 of 7 • A is for Always On My Mind", title: "Always in My Thoughts (Even When My Calendar Fails)", desc: "You're on my mind every single morning and night—not just once a year.", xRatio: 0.25, yRatio: 0.32 },
          { letter: "A", tag: "Star 3 of 7 • A is for All Your Little Details", title: "All the Small Habits & Expressions You Have", desc: "I remember the sound of your laugh, your mood shifts, and every story you've trusted me with over 3 years.", xRatio: 0.38, yRatio: 0.56 },
          { letter: "W", tag: "Star 4 of 7 • W is for Worth Every Effort", title: "Worth Every Second of Our Three Years", desc: "Three years of being your best friend is the best thing that ever happened to me.", xRatio: 0.50, yRatio: 0.25 },
          { letter: "E", tag: "Star 5 of 7 • E is for Everything I Feel", title: "Every Feeling I Have for You Is an Open Book", desc: "You already know I have a massive crush on you. Liking you is the easiest, most genuine feeling in my life.", xRatio: 0.63, yRatio: 0.58 },
          { letter: "R", tag: "Star 6 of 7 • R is for Regretting My Mistake", title: "Regretting That I Ever Made You Doubt My Care", desc: "Making my favorite person feel unimportant on her birthday breaks my heart.", xRatio: 0.76, yRatio: 0.30 },
          { letter: "A", tag: "Star 7 of 7 • A is for Always Celebrating You", title: "A Promise That You'll Never Feel Forgotten Again", desc: "From today onward, every birthday of yours is going to be celebrated like a festival.", xRatio: 0.88, yRatio: 0.52 }
        ],
        quizQuestions: [
          {
            q: "1. What's the REAL reason I forgot your birthday for 3 years?",
            options: [
              { text: "A. You don't care about me enough 😤", reaction: "Ouch, fair shot—but look deeper:", unlock: "If I didn't care, I wouldn't be losing sleep over seeing you upset. My brain fails dates because you're in my heart every single day, not just one date a year." },
              { text: "B. Your calendar brain is broken, but your heart isn't ☀️", reaction: "Ding ding! 100% accurate:", unlock: "My calendar IQ is literally zero, Saawera—but when it comes to remembering your smile, your rants, and how much you mean to me, I never miss." }
            ]
          },
          {
            q: "2. Why do I keep calling you 'Sunshine'?",
            options: [
              { text: "A. Just a random nickname 🙄", reaction: "Not even close!", unlock: "Nothing about 'Sunshine' is random. For three years, even my worst days turn golden the second I start talking to you." },
              { text: "B. Because you literally brighten my whole day 💛", reaction: "You know it, Sunshine:", unlock: "You're my favorite notification in the morning and my favorite person to talk to at night—three years straight and counting." }
            ]
          },
          {
            q: "3. Since everyone knows I have a crush on my best friend, what am I doing next?",
            options: [
              { text: "A. Making up for all 3 birthdays at once 🎂", reaction: "Non-negotiable plan:", unlock: "Year 1, Year 2, and Year 3—you're getting spoiled for all three, starting the moment you forgive this idiot." },
              { text: "B. Hoping you smile right now 🥺", reaction: "Both A and B! 💖", unlock: "Seeing Saawera smile is literally all I ever want. Now check out Page 3 to see what's actually inside my head." }
            ]
          }
        ],
        flipCards: [
          { flipped: false, frontLabel: "What It Looks Like", frontTitle: "\"He forgot my birthday 3 years in a row.\"", frontSub: "Tap to flip →", backLabel: "What's Actually True", backTitle: "I think about you all 365 days—not once a year.", backSub: "My calendar is broken, never my feelings." },
          { flipped: false, frontLabel: "What You Might Think", frontTitle: "\"He says he likes me, yet forgets my day.\"", frontSub: "Tap to flip →", backLabel: "The Honest Truth", backTitle: "My crush on you is the realest thing about me.", backSub: "Seeing you upset hurts more than anything." },
          { flipped: false, frontLabel: "Calendar Brain", frontTitle: "0 / 10 — Loses track of dates & months.", frontSub: "Tap to flip →", backLabel: "Saawera Brain", backTitle: "1000 / 10 — Remembers your laugh, rants & moods.", backSub: "Completely devoted to Sunshine." },
          { flipped: false, frontLabel: "Why You're Mad", frontTitle: "\"It makes me feel like I'm not a priority.\"", frontSub: "Tap to flip →", backLabel: "Your Real Rank", backTitle: "You're my favorite human being on this planet.", backSub: "And I'll prove it with actions." },
          { flipped: false, frontLabel: "Why 'Sunshine'?", frontTitle: "\"Is it just a cute word?\"", frontSub: "Tap to flip →", backLabel: "Why It's Yours", backTitle: "You turn my darkest days golden in seconds.", backSub: "Meri dhoop, meri Sunshine." },
          { flipped: false, frontLabel: "Next Birthday?", frontTitle: "\"He'll forget Year 4 too.\"", frontSub: "Tap to flip →", backLabel: "Permanent Oath", backTitle: "Never again. Celebrating all 3 years starting now.", backSub: "Locked in forever." }
        ],
        sealedEnvelopes: [
          { year: "Year 1 Envelope", title: "When We Became Best Friends", text: "Year 1 was when you quietly became my favorite person to talk to. For missing that first birthday, I owe you an entire day out doing everything you love." },
          { year: "Year 2 Envelope", title: "When My Crush Became Open", text: "By Year 2, you knew how crazy I was about you—and you still stayed my closest friend. For missing Year 2, I owe you a handwritten letter & thoughtful gift." },
          { year: "Year 3 Envelope", title: "Right Here, Right Now", text: "Three years in, you mean the world to me, Saawera. For missing Year 3, I promise you will never doubt how much I care about you ever again." }
        ],
        promises: [
          { icon: "🍽️", title: "The 'Saawera Picks Everything' Dinner", desc: "Your favorite spot, mains, and dessert—100% my treat.", claimed: true },
          { icon: "🎁", title: "3-Years-In-1 Gift Spree", desc: "Three separate gifts for Year 1, Year 2, and Year 3.", claimed: true },
          { icon: "☀️", title: "'Sunshine Is Always Right' Pass", desc: "Win any future argument automatically with zero debate.", claimed: true },
          { icon: "☕", title: "Late-Night Chai / Coffee Runs", desc: "Whenever you're craving something, one text and I'm there.", claimed: false },
          { icon: "💌", title: "Handwritten Letter + Treats", desc: "Something physical you can keep whenever you want a reminder.", claimed: false },
          { icon: "👑", title: "Full 'Never Say No' Day", desc: "24 hours where Saawera calls every single shot.", claimed: false }
        ]
      };

      // --- REAL MP3 PLAYLIST ENGINE (GitHub Raw Direct Streams) ---
      const mp3Tracks = [
        {
          title: "Elliot James Reay — I Think They Call This Love",
          url: "https://raw.githubusercontent.com/myblackswan848-ai/mp3/main/Elliot%20James%20Reay%20-%20I%20Think%20They%20Call%20This%20Love%20(Official%20Music%20Video)%20-%20Elliot%20James%20Reay.mp3"
        },
        {
          title: "Ed Sheeran — Perfect",
          url: "https://raw.githubusercontent.com/myblackswan848-ai/mp3/main/Ed%20Sheeran%20-%20Perfect%20(Official%20Music%20Video)%20-%20Ed%20Sheeran.mp3"
        },
        {
          title: "Arctic Monkeys — I Wanna Be Yours",
          url: "https://raw.githubusercontent.com/myblackswan848-ai/mp3/main/I%20Wanna%20Be%20Yours%20-%20Arctic%20Monkeys.mp3"
        }
      ];

      const audioEl = document.getElementById("sunshineAudio");
      audioEl.src = mp3Tracks[0].url;

      function playSparkleChord() {
        // Silent so background MP3 song plays smoothly uninterrupted
      }

      function updateMusicUI() {
        const vinyl = document.getElementById("vinylDisc");
        if (state.musicPlaying) vinyl.classList.add("vinyl-spinning");
        else vinyl.classList.remove("vinyl-spinning");
        document.querySelectorAll(".music-state-label").forEach(function (el) {
          el.textContent = state.musicPlaying ? "⏸ Pause" : "▶ Play";
        });
        document.querySelectorAll(".music-state-icon").forEach(function (el) {
          el.textContent = state.musicPlaying ? "🔊" : "🎶";
        });
      }

      function startHindiSongLoop() {
        const track = mp3Tracks[state.selectedSongIndex] || mp3Tracks[0];
        if (audioEl.src !== track.url) {
          audioEl.src = track.url;
        }
        document.getElementById("currentSongTitle").textContent = track.title;
        audioEl.play().then(function () {
          state.musicPlaying = true;
          updateMusicUI();
        }).catch(function () {
          state.musicPlaying = false;
          updateMusicUI();
          showNotice("Tap ▶ Play in the bottom bar to start the music!");
        });
      }

      function pauseSunshineAudio() {
        audioEl.pause();
        state.musicPlaying = false;
        updateMusicUI();
      }

      function toggleMusic() {
        if (state.musicPlaying) pauseSunshineAudio();
        else startHindiSongLoop();
      }

      audioEl.addEventListener("ended", function () {
        state.selectedSongIndex = (state.selectedSongIndex + 1) % mp3Tracks.length;
        document.getElementById("songSelector").value = String(state.selectedSongIndex);
        startHindiSongLoop();
      });

      document.getElementById("vinylPlayBtn").addEventListener("click", toggleMusic);
      document.getElementById("mainPlayToggleBtn").addEventListener("click", toggleMusic);
      document.getElementById("mobileMusicBtn").addEventListener("click", toggleMusic);
      document.getElementById("songSelector").addEventListener("change", function (e) {
        state.selectedSongIndex = parseInt(e.target.value, 10) || 0;
        startHindiSongLoop();
      });

      // --- TOAST ---
      let toastTimer = null;
      function showNotice(msg) {
        const b = document.getElementById("toastBanner");
        document.getElementById("toastMessage").textContent = msg;
        b.classList.remove("hidden");
        if (toastTimer) clearTimeout(toastTimer);
        toastTimer = setTimeout(function () { b.classList.add("hidden"); }, 3500);
      }
      document.getElementById("dismissToastBtn").addEventListener("click", function () {
        document.getElementById("toastBanner").classList.add("hidden");
      });

      // --- ENTRY GATE (MUSIC + RIDDLE LOCK) ---
      document.getElementById("gateStartMusicBtn").addEventListener("click", function () {
        startHindiSongLoop();
        document.getElementById("gateStepMusic").classList.add("hidden");
        document.getElementById("gateStepRiddle").classList.remove("hidden");
      });
      document.getElementById("gateQuietBtn").addEventListener("click", function () {
        document.getElementById("gateStepMusic").classList.add("hidden");
        document.getElementById("gateStepRiddle").classList.remove("hidden");
      });

      const wrongRiddleHints = [
        "Arre nahi! Think about what brightens up the whole sky every morning... ☀️",
        "Hint: It's 'Sunshine' (or 'Saawera')! Type it below to unlock 😉"
      ];
      let wrongRiddleCount = 0;

      function tryUnlockRiddle() {
        const val = (document.getElementById("riddleAnswerInput").value || "").trim().toLowerCase();
        const fb = document.getElementById("riddleFeedback");
        if (val.includes("sunshine") || val.includes("saawera") || val.includes("sun")) {
          document.getElementById("entryGateOverlay").classList.add("hidden");
          launchFireworks(60);
          initScratchCard();
          showNotice("☀️ Welcome inside, My Sunshine!");
        } else {
          fb.textContent = wrongRiddleHints[wrongRiddleCount % wrongRiddleHints.length];
          fb.classList.remove("hidden");
          wrongRiddleCount++;
        }
      }

      document.getElementById("unlockRiddleBtn").addEventListener("click", tryUnlockRiddle);
      document.getElementById("riddleAnswerInput").addEventListener("keydown", function (e) {
        if (e.key === "Enter") tryUnlockRiddle();
      });
      document.getElementById("riddleHintBtn").addEventListener("click", function () {
        const fb = document.getElementById("riddleFeedback");
        fb.textContent = "Hint: Type 'Sunshine' (because that's what you are to me ☀️)";
        fb.classList.remove("hidden");
      });

      // --- PAGE ROUTER ---
      function navigateToPage(pageKey) {
        ["home", "constellation", "truth", "wishes", "promise"].forEach(function (k) {
          const el = document.getElementById("page-" + k);
          if (el) el.classList.toggle("hidden", k !== pageKey);
        });
        document.querySelectorAll(".nav-link").forEach(function (btn) {
          const t = btn.getAttribute("data-nav");
          btn.className = "site-nav-trigger nav-link px-3.5 py-1.5 rounded-full text-xs font-semibold transition whitespace-nowrap " +
            (t === pageKey
              ? "bg-gradient-to-r from-amber-500 to-rose-500 text-rose-950 shadow-md"
              : "text-rose-200/80 hover:text-amber-200 hover:bg-white/5");
        });
        if (pageKey === "home") setTimeout(initScratchCard, 50);
        if (pageKey === "constellation") setTimeout(drawConstellationCanvas, 60);
        window.scrollTo({ top: 0, behavior: "smooth" });
      }
      document.querySelectorAll(".site-nav-trigger").forEach(function (btn) {
        btn.addEventListener("click", function () {
          const t = btn.getAttribute("data-nav");
          if (t) navigateToPage(t);
        });
      });

      // --- PAGE 1: SUNBEAM CATCHER & SCRATCH-OFF CARD ---
      document.getElementById("awakenSunshineBtn").addEventListener("click", function () {
        if (!state.musicPlaying) startHindiSongLoop();
        launchFireworks(45);
        showNotice("☀️ I Think They Call This Love — For Saawera!");
      });

      document.querySelectorAll(".sunbeam-catch-btn").forEach(function (btn) {
        btn.addEventListener("click", function () {
          const idx = parseInt(btn.getAttribute("data-beam"), 10);
          if (!state.caughtBeams[idx]) {
            state.caughtBeams[idx] = true;
            btn.className = "sunbeam-catch-btn p-4 rounded-2xl bg-rose-900 text-amber-200 border-2 border-amber-400 font-bold text-xs sm:text-sm shadow-md flex items-center justify-center gap-2";
            btn.innerHTML = "<span>☀️</span><span>Sunbeam #" + (idx + 1) + " Caught!</span>";
            document.getElementById("beamPara-" + idx).classList.remove("hidden");
            const count = state.caughtBeams.filter(Boolean).length;
            document.getElementById("sunbeamsCaughtBadge").textContent = count + " / 3 Caught";
            playSparkleChord([523.25, 659.25, 783.99]);
            launchFireworks(25);
          }
        });
      });

      // Scratch-off Gold Foil Canvas
      function initScratchCard() {
        if (state.scratchRevealed) return;
        const sc = document.getElementById("scratchCanvas");
        if (!sc || !sc.parentElement) return;
        const rect = sc.parentElement.getBoundingClientRect();
        if (rect.width === 0) return;
        sc.width = rect.width;
        sc.height = rect.height;
        const sctx = sc.getContext("2d");
        const grad = sctx.createLinearGradient(0, 0, sc.width, sc.height);
        grad.addColorStop(0, "#fbbf24");
        grad.addColorStop(0.5, "#f59e0b");
        grad.addColorStop(1, "#ec4899");
        sctx.fillStyle = grad;
        sctx.fillRect(0, 0, sc.width, sc.height);
        sctx.fillStyle = "#450a0a";
        sctx.font = "bold 14px 'Plus Jakarta Sans', sans-serif";
        sctx.textAlign = "center";
        sctx.fillText("✨ Rub / Scratch Here With Finger or Mouse ✨", sc.width / 2, sc.height / 2 + 5);

        let scratching = false;
        function scratchAt(clientX, clientY) {
          const r = sc.getBoundingClientRect();
          const x = clientX - r.left;
          const y = clientY - r.top;
          sctx.globalCompositeOperation = "destination-out";
          sctx.beginPath();
          sctx.arc(x, y, 22, 0, Math.PI * 2);
          sctx.fill();
        }
        sc.onmousedown = function (e) { scratching = true; scratchAt(e.clientX, e.clientY); };
        sc.onmousemove = function (e) { if (scratching) scratchAt(e.clientX, e.clientY); };
        window.addEventListener("mouseup", function () { scratching = false; });
        sc.ontouchstart = function (e) { scratching = true; if (e.touches[0]) scratchAt(e.touches[0].clientX, e.touches[0].clientY); };
        sc.ontouchmove = function (e) { if (scratching && e.touches[0]) scratchAt(e.touches[0].clientX, e.touches[0].clientY); };
        sc.ontouchend = function () { scratching = false; };
      }

      document.getElementById("revealScratchInstantBtn").addEventListener("click", function () {
        state.scratchRevealed = true;
        document.getElementById("scratchCanvas").classList.add("hidden");
        launchFireworks(20);
      });

      // --- PAGE 2: S·A·A·W·E·R·A CONSTELLATION & MINI QUIZ ---
      const constCanvas = document.getElementById("constellationCanvas");
      const constCtx = constCanvas.getContext("2d");

      function renderSaaweraStarButtons() {
        const bar = document.getElementById("saaweraStarsBar");
        bar.innerHTML = "";
        let lit = 0;
        state.saaweraStars.forEach(function (s, idx) {
          if (state.starsVisited[idx]) lit++;
          const cur = idx === state.activeStarIndex;
          const btn = document.createElement("button");
          btn.type = "button";
          btn.className = "py-3 rounded-2xl font-serif-luxury text-lg sm:text-2xl font-bold border transition flex flex-col items-center justify-center " +
            (cur ? "bg-gradient-to-b from-amber-400 to-rose-500 text-rose-950 border-amber-200 shadow-lg scale-105"
              : state.starsVisited[idx] ? "bg-amber-500/20 text-amber-200 border-amber-400/40"
              : "bg-white/5 hover:bg-white/10 text-rose-200/70 border-white/10");
          btn.innerHTML = '<span>' + s.letter + '</span><span class="text-[9px] font-sans uppercase mt-0.5">' + (state.starsVisited[idx] ? "★ Lit" : "Tap") + '</span>';
          btn.addEventListener("click", function () { selectStar(idx); });
          bar.appendChild(btn);
        });
        document.getElementById("starsLitBadge").textContent = lit + " / 7 Stars Illuminated";
        const act = state.saaweraStars[state.activeStarIndex];
        document.getElementById("starLetterTag").textContent = act.tag;
        document.getElementById("starTitle").textContent = act.title;
        document.getElementById("starDescription").textContent = act.desc;
      }

      function selectStar(idx) {
        state.activeStarIndex = idx;
        state.starsVisited[idx] = true;
        playSparkleChord([523.25, 659.25, 783.99]);
        renderSaaweraStarButtons();
        drawConstellationCanvas();
      }

      function drawConstellationCanvas() {
        const box = constCanvas.parentElement;
        if (!box) return;
        constCanvas.width = box.clientWidth || 600;
        constCanvas.height = box.clientHeight || 220;
        const w = constCanvas.width, h = constCanvas.height;
        constCtx.clearRect(0, 0, w, h);
        constCtx.strokeStyle = "rgba(251, 191, 36, 0.55)";
        constCtx.lineWidth = 2;
        constCtx.setLineDash([4, 4]);
        constCtx.beginPath();
        state.saaweraStars.forEach(function (s, i) {
          if (i === 0) constCtx.moveTo(s.xRatio * w, s.yRatio * h);
          else constCtx.lineTo(s.xRatio * w, s.yRatio * h);
        });
        constCtx.stroke();
        constCtx.setLineDash([]);
        state.saaweraStars.forEach(function (s, idx) {
          const x = s.xRatio * w, y = s.yRatio * h;
          const isCur = idx === state.activeStarIndex;
          const grad = constCtx.createRadialGradient(x, y, 2, x, y, isCur ? 26 : 16);
          grad.addColorStop(0, state.starsVisited[idx] ? "rgba(251,191,36,0.9)" : "rgba(244,63,94,0.45)");
          grad.addColorStop(1, "rgba(251,191,36,0)");
          constCtx.fillStyle = grad;
          constCtx.beginPath(); constCtx.arc(x, y, isCur ? 26 : 16, 0, Math.PI * 2); constCtx.fill();
          constCtx.fillStyle = isCur ? "#fef08a" : state.starsVisited[idx] ? "#fbbf24" : "#fda4af";
          constCtx.beginPath(); constCtx.arc(x, y, isCur ? 7 : 5, 0, Math.PI * 2); constCtx.fill();
          constCtx.fillStyle = "#fff1f2";
          constCtx.font = "bold 13px 'Cormorant Garamond', serif";
          constCtx.textAlign = "center";
          constCtx.fillText(s.letter, x, y - 12);
        });
      }

      constCanvas.addEventListener("click", function (e) {
        const rect = constCanvas.getBoundingClientRect();
        const cx = e.clientX - rect.left, cy = e.clientY - rect.top;
        let best = 0, bestD = 999999;
        state.saaweraStars.forEach(function (s, idx) {
          const d = Math.hypot(s.xRatio * constCanvas.width - cx, s.yRatio * constCanvas.height - cy);
          if (d < bestD) { bestD = d; best = idx; }
        });
        selectStar(best);
      });

      // Mini Quiz Renderer
      function renderQuiz() {
        const q = state.quizQuestions[state.quizStep];
        document.getElementById("quizProgressBadge").textContent = "Question " + (state.quizStep + 1) + " of " + state.quizQuestions.length;
        document.getElementById("quizQuestionText").textContent = q.q;
        document.getElementById("quizUnlockBox").classList.add("hidden");
        const grid = document.getElementById("quizOptionsGrid");
        grid.innerHTML = "";
        q.options.forEach(function (opt) {
          const btn = document.createElement("button");
          btn.type = "button";
          btn.className = "p-4 rounded-2xl bg-white/5 hover:bg-amber-500/20 border border-amber-300/30 text-left text-xs sm:text-sm font-semibold text-rose-100 transition";
          btn.textContent = opt.text;
          btn.addEventListener("click", function () {
            document.getElementById("quizReactionText").textContent = opt.reaction;
            document.getElementById("quizUnlockedParagraph").textContent = opt.unlock;
            document.getElementById("quizUnlockBox").classList.remove("hidden");
            document.getElementById("nextQuizBtn").textContent = state.quizStep < state.quizQuestions.length - 1 ? "Next Question →" : "Restart Quiz ↺";
            playSparkleChord([523.25, 659.25]);
          });
          grid.appendChild(btn);
        });
      }
      document.getElementById("nextQuizBtn").addEventListener("click", function () {
        state.quizStep = (state.quizStep + 1) % state.quizQuestions.length;
        renderQuiz();
      });

      // --- PAGE 3: FLIP CARDS & HEARTBEAT ---
      function renderFlipCards() {
        const grid = document.getElementById("flipCardsGrid");
        grid.innerHTML = "";
        let count = 0;
        state.flipCards.forEach(function (card) {
          if (card.flipped) count++;
          const w = document.createElement("div");
          w.className = "flip-scene cursor-pointer " + (card.flipped ? "is-flipped" : "");
          w.innerHTML =
            '<div class="flip-card-inner">' +
              '<div class="flip-face luxury-glass border border-rose-400/25">' +
                '<div><span class="text-[10px] font-bold uppercase tracking-widest text-rose-400">' + card.frontLabel + '</span><p class="font-serif-luxury text-xl font-bold text-white mt-2">' + card.frontTitle + '</p></div>' +
                '<div class="flex justify-between text-xs text-amber-300 font-semibold pt-3 border-t border-white/10"><span>' + card.frontSub + '</span><span>🔄</span></div>' +
              '</div>' +
              '<div class="flip-face flip-face-back bg-gradient-to-br from-amber-500/25 via-rose-600/30 to-pink-600/25 border-2 border-amber-300/70 backdrop-blur-xl">' +
                '<div><span class="text-[10px] font-extrabold uppercase tracking-widest text-amber-300">☀️ ' + card.backLabel + '</span><p class="font-serif-luxury text-xl font-bold text-white mt-2">' + card.backTitle + '</p></div>' +
                '<div class="flex justify-between text-xs text-amber-200 italic pt-3 border-t border-amber-300/25"><span>' + card.backSub + '</span><span>💖</span></div>' +
              '</div>' +
            '</div>';
          w.addEventListener("click", function () {
            card.flipped = !card.flipped;
            playSparkleChord([440, 554.37, 659.25]);
            renderFlipCards();
          });
          grid.appendChild(w);
        });
        document.getElementById("flippedTruthCounter").textContent = count + " / " + state.flipCards.length + " Cards Revealed";
      }

      const pulseMemories = [
        "\"I remember the exact way you laugh when you're trying to stay serious...\"",
        "\"I remember how my entire day gets 10x better the second a message from Saawera appears...\"",
        "\"I remember every late-night conversation we've had over the last three years...\"",
        "\"I might be the worst with calendar dates, par mera dil sirf tumhara naam yaad rakhta hai, Saawera ☀️\""
      ];
      document.getElementById("pulseScanBtn").addEventListener("click", function () {
        document.getElementById("pulseMemoryReadout").textContent = pulseMemories[state.pulseTapIndex % pulseMemories.length];
        state.pulseTapIndex++;
        playSparkleChord([523.25, 659.25, 880]);
        launchFireworks(16);
      });

      // --- PAGE 4: CANDLES -> ENVELOPES -> GOLDEN KEY -> LANTERNS ---
      function renderCandlesAndEnvelopes() {
        let blown = 0;
        state.candlesBlown.forEach(function (b, idx) {
          if (b) blown++;
          const orb = document.getElementById("flameOrb-" + idx);
          if (orb) {
            orb.className = b ? "w-6 h-9 rounded-full bg-white/10 mb-1 flex items-center justify-center text-xs" : "w-6 h-9 rounded-full bg-gradient-to-t from-orange-500 via-amber-300 to-yellow-100 shadow-[0_0_25px_rgba(251,191,36,0.9)] flame-anim mb-1";
            orb.textContent = b ? "💨" : "";
          }
        });
        document.getElementById("wishesBlownBadge").textContent = blown + " / 3 Seals Broken";

        const grid = document.getElementById("sealedEnvelopesGrid");
        grid.innerHTML = "";
        state.sealedEnvelopes.forEach(function (env, idx) {
          const open = state.candlesBlown[idx];
          const card = document.createElement("div");
          card.className = "rounded-3xl p-5 border transition " + (open ? "bg-gradient-to-br from-amber-500/20 to-rose-500/20 border-amber-300/70 shadow-lg" : "luxury-glass border-white/10 opacity-75");
          card.innerHTML =
            '<div class="flex justify-between mb-1.5">' +
              '<span class="text-[10px] font-bold uppercase tracking-widest text-amber-300">' + env.year + '</span>' +
              '<span class="text-xs font-bold">' + (open ? "💌 Unsealed" : "🔒 Blow Yr " + (idx + 1)) + '</span>' +
            '</div>' +
            '<h4 class="font-serif-luxury text-xl font-bold text-white">' + env.title + '</h4>' +
            '<p class="text-xs text-rose-100/85 mt-1.5 leading-relaxed">' + (open ? env.text : "Blow out Candle Yr " + (idx + 1) + " above to break the wax seal on this letter.") + '</p>';
          grid.appendChild(card);
        });

        if (blown === 3) {
          showNotice("🎂 All 3 Birthday Seals Unsealed for Saawera!");
        }
      }

      document.querySelectorAll(".cake-candle-btn").forEach(function (btn) {
        btn.addEventListener("click", function () {
          const idx = parseInt(btn.getAttribute("data-candle-idx"), 10);
          if (!state.candlesBlown[idx]) {
            state.candlesBlown[idx] = true;
            playSparkleChord([523.25, 659.25, 783.99]);
            launchFireworks(35);
            renderCandlesAndEnvelopes();
          }
        });
      });

      document.getElementById("blowAllCandlesBtn").addEventListener("click", function () {
        state.candlesBlown = [true, true, true];
        playSparkleChord([523.25, 659.25, 783.99, 1046.5]);
        launchFireworks(65);
        renderCandlesAndEnvelopes();
      });

      document.getElementById("relightCandlesBtn").addEventListener("click", function () {
        state.candlesBlown = [false, false, false];
        renderCandlesAndEnvelopes();
      });


      // --- PAGE 5: PROMISES, MOOD SLIDER & HOLD-FOR-HUG FINALE ---
      function renderPromises() {
        const grid = document.getElementById("promisesGrid");
        grid.innerHTML = "";
        let count = 0;
        state.promises.forEach(function (p) {
          if (p.claimed) count++;
          const btn = document.createElement("button");
          btn.type = "button";
          btn.className = "text-left p-5 rounded-3xl border transition flex flex-col justify-between " +
            (p.claimed ? "bg-gradient-to-br from-amber-500/25 via-rose-500/25 to-pink-500/25 border-amber-300 shadow-lg" : "luxury-glass hover:bg-white/10 border-white/10");
          btn.innerHTML =
            '<div><div class="flex justify-between mb-2"><span class="text-2xl">' + p.icon + '</span><span class="text-[10px] font-extrabold uppercase px-3 py-1 rounded-full ' + (p.claimed ? 'bg-amber-400 text-rose-950' : 'bg-white/10 text-rose-200') + '">' + (p.claimed ? "✓ Promised" : "Claim") + '</span></div>' +
            '<h4 class="font-serif-luxury text-xl font-bold text-white">' + p.title + '</h4>' +
            '<p class="text-xs text-rose-100/80 mt-1.5">' + p.desc + '</p></div>';
          btn.addEventListener("click", function () {
            p.claimed = !p.claimed;
            if (p.claimed) { playSparkleChord([523.25, 659.25]); launchFireworks(14); }
            renderPromises();
          });
          grid.appendChild(btn);
        });
        document.getElementById("promisesClaimedBadge").textContent = count + " / " + state.promises.length + " Claimed";
      }

      // Mood Slider
      document.getElementById("moodSlider").addEventListener("input", function (e) {
        const v = parseInt(e.target.value, 10);
        const label = document.getElementById("moodPercentLabel");
        const quote = document.getElementById("moodHindiQuote");
        if (v < 30) {
          label.textContent = "😤 Full Gussa Mode (" + (100 - v) + "% Mad)";
          quote.textContent = "\"Kaano ko haath laga ke sorry bol raha hoon, Saawera... itna gussa mat karo yaar!\"";
        } else if (v < 75) {
          label.textContent = "🥺 Thoda Pighal Rahi Hoon";
          quote.textContent = "\"Thoda sa gussa kam hua? Bas ek smile de do, saari duniya jeet lunga main...\"";
        } else {
          label.textContent = "💖 Maaf Kiya Mode Activated!";
          quote.textContent = "\"Ab bas hold or tap the button below, Sunshine! ☀️\"";
        }
      });

      // Press & Hold (or Tap) Forgiveness Button
      let holdInterval = null, holdProgress = 0;
      const holdBtn = document.getElementById("holdHugBtn");
      const holdFill = document.getElementById("holdProgressFill");

      function triggerForgivenessCelebration() {
        document.getElementById("forgivenCelebrationCard").classList.remove("hidden");
        document.getElementById("stillAngryBtn").style.transform = "translate(0, 0)";
        if (!state.musicPlaying) startHindiSongLoop();
        playSparkleChord([523.25, 659.25, 783.99, 1046.5]);
        launchFireworks(95);
        showNotice("💖 Happy Birthday, Saawera — My Sunshine Forever!");
      }

      holdBtn.addEventListener("mousedown", function () {
        holdProgress = 0;
        clearInterval(holdInterval);
        holdInterval = setInterval(function () {
          holdProgress += 5;
          holdFill.style.width = Math.min(100, holdProgress) + "%";
          if (holdProgress >= 100) {
            clearInterval(holdInterval);
            triggerForgivenessCelebration();
          }
        }, 40);
      });
      holdBtn.addEventListener("mouseup", function () { clearInterval(holdInterval); holdFill.style.width = "0%"; });
      holdBtn.addEventListener("click", triggerForgivenessCelebration);

      const hindiPleas = [
        "\"Yaar Saawera, maan bhi jao na... kaano ko haath laga ke sorry bol raha hoon! 🥺\"",
        "\"Teen saal se tumpe hi crush hai, bas calendar dekhna bhool jaata hoon kyunki tumhe dekhta rehta hoon! ☀️\"",
        "\"Jitni chahe saza de do, par naraz mat raho meri Sunshine! 💖\""
      ];
      document.getElementById("stillAngryBtn").addEventListener("click", function (e) {
        document.getElementById("moodHindiQuote").textContent = hindiPleas[state.pleaStep % hindiPleas.length];
        state.pleaStep++;
        playSparkleChord([392, 349.23]);
        const ox = Math.round((Math.random() - 0.5) * 80);
        const oy = Math.round((Math.random() - 0.5) * 24);
        e.currentTarget.style.transform = "translate(" + ox + "px, " + oy + "px)";
      });

      // --- ULTRA-LIGHTWEIGHT AMBIENT STARLIGHT ---
      const starCanvas = document.getElementById("starlightCanvas");
      const starCtx = starCanvas.getContext("2d");
      let ambientStars = [];
      function initStarlight() {
        starCanvas.width = window.innerWidth; starCanvas.height = window.innerHeight;
        ambientStars = [];
        for (let i = 0; i < 16; i++) {
          ambientStars.push({ x: Math.random() * starCanvas.width, y: Math.random() * starCanvas.height, r: 1.2 + Math.random() * 1.5, vy: -0.12 - Math.random() * 0.15, alpha: 0.2 + Math.random() * 0.35, gold: Math.random() > 0.35 });
        }
      }
      function animateStarlight() {
        starCtx.clearRect(0, 0, starCanvas.width, starCanvas.height);
        ambientStars.forEach(function (s) {
          s.y += s.vy; if (s.y < -10) s.y = starCanvas.height + 10;
          starCtx.globalAlpha = s.alpha;
          starCtx.fillStyle = s.gold ? "#fbbf24" : "#fda4af";
          starCtx.beginPath(); starCtx.arc(s.x, s.y, s.r, 0, Math.PI * 2); starCtx.fill();
        });
        starCtx.globalAlpha = 1;
        requestAnimationFrame(animateStarlight);
      }
      window.addEventListener("resize", function () { initStarlight(); drawConstellationCanvas(); });
      initStarlight(); requestAnimationFrame(animateStarlight);

      function launchFireworks() {
        // Lightweight no-op to keep UI buttery smooth without emoji canvas lag
      }

      // --- INIT ---
      renderSaaweraStarButtons();
      drawConstellationCanvas();
      renderQuiz();
      renderFlipCards();
      renderCandlesAndEnvelopes();
      renderPromises();
    })();
  </script>
</body>
</html>
