# hng-stage1-uiux-design

<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>FunBot — 7 Screen Mockups</title>

  <!-- Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700&family=Poppins:wght@600;700&display=swap" rel="stylesheet">

  <style>
    /* ==========================
       Design tokens (exact)
       ========================== */
    :root{
      --primary: #4AB7FF;
      --primary-2: #2CA6F0;
      --secondary: #FFD93D;
      --success: #4CD964;
      --error: #FF6F61;
      --background: #F5F5F5;
      --text-dark: #2D3142;
      --text-light: #555B6E;
      --card-bg: #FFFFFF;

      --radius-lg: 16px;
      --radius-md: 12px;
      --shadow: 0 10px 30px rgba(45,49,66,0.08);
      --max-width: 980px;
    }

    /* ==========================
       Base
       ========================== */
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;background:linear-gradient(180deg,#FFFFFF 0%, #FBFDFF 40%, var(--background) 100%);font-family: "Nunito", system-ui, -apple-system, "Segoe UI", Roboto, Arial;color:var(--text-dark);-webkit-font-smoothing:antialiased}
    .wrap{max-width:var(--max-width);margin:24px auto;padding:20px;}

    /* top nav for quick screen switching (only for prototype) */
    .topbar{display:flex;gap:10px;align-items:center;margin-bottom:16px}
    .logo{display:flex;gap:12px;align-items:center}
    .logo .mark{width:44px;height:44px;border-radius:10px;background:linear-gradient(180deg,#68CBFF,var(--primary));display:flex;align-items:center;justify-content:center;color:white;font-weight:800;font-family:"Poppins";box-shadow:0 8px 18px rgba(74,183,255,0.16)}
    .screens-menu{margin-left:auto;display:flex;gap:8px;flex-wrap:wrap}
    .screen-btn{background:transparent;border:1px solid rgba(45,49,66,0.06);padding:8px 10px;border-radius:10px;cursor:pointer;font-size:13px}
    .screen-btn.active{background:var(--primary);color:white;border-color:transparent;box-shadow:var(--shadow)}

    /* common card */
    .card{background:var(--card-bg);border-radius:var(--radius-lg);padding:18px;box-shadow:var(--shadow);border:1px solid rgba(13,18,28,0.03)}

    /* layout helper for mobile mock size */
    .phone{
      width:375px;
      height:812px;
      margin:0 auto;
      background:linear-gradient(180deg,#FFFFFF,#F8FAFF);
      border-radius:22px;
      padding:14px;
      box-shadow: 0 18px 60px rgba(13,18,28,0.12);
      position:relative;
      overflow:hidden;
      border: 10px solid rgba(0,0,0,0.02);
    }

    /* screen container */
    .screen{width:100%;height:100%;display:none;position:absolute;left:14px;top:14px;padding:14px;box-sizing:border-box}
    .screen.active{display:block}

    /* header inside phone */
    .phone-header{display:flex;align-items:center;gap:8px;margin-bottom:10px}
    .avatar{width:44px;height:44px;border-radius:10px;background:linear-gradient(180deg,#68CBFF,var(--primary));display:flex;align-items:center;justify-content:center;color:white;font-weight:800}
    .xp-bar{flex:1;height:12px;background:#F1F7FF;border-radius:99px;padding:2px}
    .xp-fill{height:8px;border-radius:99px;background:linear-gradient(90deg,var(--primary),var(--primary-2));width:48%}
    .small{font-size:12px;color:var(--text-light)}

    /* ==========================
       01 Onboarding (3 slides)
       ========================== */
    .onboarding{display:flex;flex-direction:column;align-items:center;justify-content:space-between;height:100%}
    .ob-hero{width:100%;height:300px;background:linear-gradient(135deg,var(--primary),var(--secondary));border-radius:16px;color:white;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:18px;text-align:center}
    .ob-hero h2{font-family:"Poppins";font-size:24px;margin:0}
    .ob-desc{margin-top:8px;font-size:14px;opacity:0.95}
    .ob-controls{display:flex;align-items:center;gap:10px}
    .dot{width:8px;height:8px;border-radius:99px;background:rgba(255,255,255,0.5)}
    .dot.active{width:18px;background:white;transition:all .18s ease}
    .start-btn{background:linear-gradient(90deg,var(--primary),var(--primary-2));color:white;border:none;padding:12px 18px;border-radius:12px;font-weight:700;cursor:pointer;box-shadow:0 14px 36px rgba(74,183,255,0.14)}

    /* ==========================
       02 Home
       ========================== */
    .home-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-top:8px}
    .home-card{display:flex;flex-direction:column;gap:8px;padding:12px;border-radius:12px}
    .home-card h4{margin:0;font-family:"Poppins";font-size:15px}
    .home-row{display:flex;align-items:center;justify-content:space-between;margin-top:8px}
    .big-cta{background:linear-gradient(90deg,var(--primary),var(--primary-2));color:white;padding:12px;border-radius:12px;font-weight:700;border:none;cursor:pointer}

    /* ==========================
       03 Lesson (drag & drop)
       ========================== */
    .lesson-wrap{display:flex;flex-direction:column;height:100%}
    .lesson-stage{flex:1;background:linear-gradient(180deg,#EEF9FF,#FFFFFF);border-radius:12px;padding:12px;display:flex;flex-direction:column;gap:10px;align-items:center;justify-content:center}
    .blocks-palette{display:flex;flex-direction:column;gap:8px;padding:8px;border-radius:12px;background:white;border:1px solid rgba(13,18,28,0.03)}
    .block{padding:10px 12px;border-radius:10px;background:linear-gradient(90deg,#fff,#F4FBFF);border:1px solid rgba(74,183,255,0.08);cursor:grab;font-weight:700}
    .workspace{width:100%;min-height:120px;background:linear-gradient(180deg,#FFFFFF,#F6FBFF);border-radius:10px;border:2px dashed rgba(74,183,255,0.12);padding:12px;display:flex;flex-direction:column;gap:8px}
    .run-btn{background:var(--secondary);color:var(--text-dark);border:none;padding:10px;border-radius:10px;font-weight:800;cursor:pointer}

    /* small code preview badges */
    .chip{display:inline-flex;padding:6px 10px;border-radius:999px;background:#F3FBFF;border:1px solid rgba(74,183,255,0.06);font-weight:700;color:var(--primary);font-size:13px}

    /* ==========================
       04 Challenge / Progress
       ========================== */
    .progress-top{display:flex;align-items:center;gap:10px}
    .badges{display:flex;gap:8px;flex-wrap:wrap;margin-top:10px}
    .badge{width:72px;height:72px;border-radius:12px;background:linear-gradient(180deg,#fff,#FFF9E6);display:flex;align-items:center;justify-content:center;flex-direction:column;border:1px solid rgba(45,49,66,0.04)}
    .badge .ttl{font-weight:700;font-size:12px}

    /* ==========================
       05 Profile
       ========================== */
    .profile-top{display:flex;gap:12px;align-items:center}
    .large-avatar{width:80px;height:80px;border-radius:16px;background:linear-gradient(180deg,#68CBFF,var(--primary));display:flex;align-items:center;justify-content:center;color:white;font-weight:800;font-size:22px}
    .stat-grid{display:flex;gap:8px;margin-top:10px}
    .stat{flex:1;background:#F9FBFF;padding:10px;border-radius:10px;text-align:center}

    /* ==========================
       06 Parent Control
       ========================== */
    .pc-row{display:flex;align-items:center;justify-content:space-between;padding:12px;border-radius:10px;background:#FFFFFF;border:1px solid rgba(13,18,28,0.03)}
    .toggle{width:48px;height:28px;border-radius:99px;background:#E7EEF9;position:relative;cursor:pointer}
    .toggle .knob{width:22px;height:22px;border-radius:50%;background:white;position:absolute;top:3px;left:3px;box-shadow:0 4px 10px rgba(13,18,28,0.08);transition:left .18s ease}
    .toggle.on{background:linear-gradient(90deg,var(--primary),var(--primary-2))}
    .toggle.on .knob{left:23px}

    /* ==========================
       07 Reward screen
       ========================== */
    .reward-center{display:flex;flex-direction:column;align-items:center;justify-content:center;height:100%}
    .trophy{width:140px;height:140px;border-radius:20px;background:linear-gradient(180deg,var(--secondary),#FFEC8A);display:flex;align-items:center;justify-content:center;font-weight:900;font-size:48px;color:var(--text-dark);box-shadow:0 14px 40px rgba(255,217,61,0.14)}
    .confetti{position:absolute;pointer-events:none;inset:0}
    .reward-cta{display:flex;gap:10px;margin-top:18px}

    /* tiny helpers */
    .muted{color:var(--text-light);font-size:13px}
    .center{text-align:center}
    .spacer{height:12px}
    .small-cta{font-size:13px;padding:8px 10px;border-radius:10px;border:1px solid rgba(13,18,28,0.06);background:white;cursor:pointer}

    /* accessibility focus */
    button:focus{outline:3px solid rgba(74,183,255,0.18);outline-offset:2px}
  </style>
</head>
<body>
  <div class="wrap">

    <div class="topbar">
      <div class="logo">
        <div class="mark">FB</div>
        <div>
          <div style="font-weight:800">FunBot</div>
          <div style="font-size:12px;color:var(--text-light)">Kids Coding App — Prototype</div>
        </div>
      </div>

      <div class="screens-menu" role="tablist" aria-label="Screens">
        <button class="screen-btn active" data-screen="onboarding">Onboarding</button>
        <button class="screen-btn" data-screen="home">Home</button>
        <button class="screen-btn" data-screen="lesson">Lesson</button>
        <button class="screen-btn" data-screen="challenge">Challenge</button>
        <button class="screen-btn" data-screen="profile">Profile</button>
        <button class="screen-btn" data-screen="parent">Parent</button>
        <button class="screen-btn" data-screen="reward">Reward</button>
      </div>
    </div>

    <!-- phone mock -->
    <div class="phone" role="application" aria-label="Phone mockup containing screens">

      <!-- 01 Onboarding -->
      <section id="onboarding" class="screen active card">
        <div class="onboarding">
          <div style="width:100%">
            <div style="display:flex;justify-content:space-between;align-items:center">
              <div style="display:flex;gap:10px;align-items:center">
                <div class="avatar">😺</div>
                <div>
                  <div style="font-weight:700">Welcome to FunBot</div>
                  <div class="small">Learn coding — playfully</div>
                </div>
              </div>
              <div class="small">Skip</div>
            </div>
          </div>

          <div class="ob-hero">
            <h2 id="ob-title">Welcome, Little Coder!</h2>
            <div class="ob-desc" id="ob-desc">Meet FunBot — your friendly coding buddy. Learn through play, stories and puzzles.</div>

            <div style="margin-top:16px;display:flex;gap:8px;align-items:center" id="ob-dots">
              <div class="dot active"></div>
              <div class="dot"></div>
              <div class="dot"></div>
            </div>
          </div>

          <div style="width:100%;display:flex;align-items:center;justify-content:space-between">
            <div class="small">Tap to hear</div>
            <div class="ob-controls">
              <button class="screen-btn" id="ob-prev" style="visibility:hidden">Back</button>
              <button class="start-btn" id="ob-next">Next</button>
            </div>
          </div>
        </div>
      </section>

      <!-- 02 Home -->
      <section id="home" class="screen card">
        <div>
          <div class="phone-header">
            <div class="avatar">LK</div>
            <div style="flex:1">
              <div style="display:flex;justify-content:space-between;align-items:center">
                <div style="font-weight:700">Lawrence</div>
                <div class="small">Lvl 4 • 420 XP</div>
              </div>
              <div style="margin-top:8px">
                <div class="xp-bar" aria-hidden="true"><div class="xp-fill"></div></div>
              </div>
            </div>
          </div>

          <div style="margin-top:12px">
            <div class="home-grid">
              <div class="card home-card">
                <h4>Lessons</h4>
                <div class="muted">Step-by-step learning</div>
                <div class="home-row">
                  <button class="big-cta" onclick="goScreen('lesson')">Start Lesson</button>
                  <div class="chip">3 modules</div>
                </div>
              </div>

              <div class="card home-card">
                <h4>Games</h4>
                <div class="muted">Play and practice</div>
                <div class="home-row">
                  <button class="big-cta">Play</button>
                  <div class="chip">2 games</div>
                </div>
              </div>

              <div class="card home-card" style="grid-column:'span 2'">
                <h4>Challenges & Progress</h4>
                <div class="muted">Earn stars and badges</div>
                <div class="home-row">
                  <button class="big-cta" onclick="goScreen('challenge')">View Progress</button>
                  <div class="chip">12★</div>
                </div>
              </div>

              <div class="card home-card">
                <h4>Profile</h4>
                <div class="muted">Manage avatar & stats</div>
                <div class="home-row">
                  <button class="big-cta" onclick="goScreen('profile')">Open</button>
                  <div class="chip">Lvl 4</div>
                </div>
              </div>
            </div>
          </div>

        </div>
      </section>

      <!-- 03 Lesson -->
      <section id="lesson" class="screen card">
        <div class="lesson-wrap">
          <div style="display:flex;justify-content:space-between;align-items:center">
            <div style="display:flex;gap:12px;align-items:center">
              <div class="avatar">FB</div>
              <div>
                <div style="font-weight:700">Lesson 1: Make FunBot Jump</div>
                <div class="small">Drag blocks to the workspace and run</div>
              </div>
            </div>
            <div class="small">Step 1 / 4</div>
          </div>

          <div class="lesson-stage">
            <div style="width:100%;display:flex;gap:12px;align-items:flex-start">
              <div style="width:40%;display:flex;flex-direction:column;gap:8px">
                <div class="card blocks-palette">
                  <div class="chip">Blocks</div>
                  <div draggable="true" class="block" data-type="move">Move Forward</div>
                  <div draggable="true" class="block" data-type="jump">Jump</div>
                  <div draggable="true" class="block" data-type="loop">Repeat x3</div>
                </div>

                <div style="margin-top:8px" class="card">
                  <div style="font-weight:700">Hints</div>
                  <div class="muted">Try playing a jump after moving forward</div>
                </div>
              </div>

              <div style="flex:1;display:flex;flex-direction:column;gap:8px">
                <div class="workspace" id="workspace" aria-label="Drag blocks here">
                  <div class="muted">Drop blocks here</div>
                </div>

                <div style="display:flex;gap:8px;align-items:center;justify-content:space-between">
                  <button class="run-btn" id="runBtn">Run Code ▶</button>
                  <div class="muted">Output: <span id="runOutput">—</span></div>
                </div>
              </div>
            </div>
          </div>

          <div style="display:flex;justify-content:space-between;align-items:center;margin-top:8px">
            <button class="screen-btn" onclick="goScreen('home')">Back to Home</button>
            <button class="start-btn" onclick="goScreen('challenge')">Submit & View Progress</button>
          </div>
        </div>
      </section>

      <!-- 04 Challenge / Progress -->
      <section id="challenge" class="screen card">
        <div>
          <div style="display:flex;justify-content:space-between;align-items:center">
            <div style="display:flex;gap:12px;align-items:center">
              <div class="avatar">🏆</div>
              <div>
                <div style="font-weight:800">My Progress</div>
                <div class="small">Keep your streak — earn more stars!</div>
              </div>
            </div>
            <div style="text-align:right">
              <div style="font-weight:800">420 XP</div>
              <div class="muted">Level 4</div>
            </div>
          </div>

          <div style="margin-top:12px" class="card">
            <div class="progress-top">
              <div style="flex:1">
                <div style="font-weight:700">XP Progress</div>
                <div style="margin-top:8px" class="xp-bar"><div class="xp-fill" style="width:62%"></div></div>
                <div class="muted" style="margin-top:8px">Next level at 700 XP</div>
              </div>
              <div style="width:110px;text-align:center">
                <div style="font-weight:900;font-size:20px">12★</div>
                <div class="muted">Total Stars</div>
              </div>
            </div>

            <div style="margin-top:12px">
              <div style="font-weight:800">Badges</div>
              <div class="badges">
                <div class="badge"><div style="font-size:20px">🔁</div><div class="ttl">Loop Pro</div></div>
                <div class="badge"><div style="font-size:20px">🧠</div><div class="ttl">Logic Pro</div></div>
                <div class="badge"><div style="font-size:20px">⭐</div><div class="ttl">Star Learner</div></div>
                <div class="badge"><div style="font-size:20px">🏅</div><div class="ttl">Streak 7</div></div>
              </div>
            </div>

            <div style="margin-top:12px;display:flex;justify-content:space-between;align-items:center">
              <button class="big-cta" onclick="goScreen('reward')">Claim Reward</button>
              <div style="display:flex;gap:8px">
                <button class="small-cta" onclick="goScreen('lesson')">Retry Lesson</button>
                <button class="small-cta" onclick="goScreen('home')">Home</button>
              </div>
            </div>
          </div>

        </div>
      </section>

      <!-- 05 Profile -->
      <section id="profile" class="screen card">
        <div>
          <div class="profile-top">
            <div class="large-avatar">LK</div>
            <div>
              <div style="font-weight:900;font-size:18px">Lawrence M.</div>
              <div class="small">Age 10 • 4th grade</div>
              <div style="margin-top:8px" class="muted">Bio: Loves robots & puzzles.</div>
            </div>
          </div>

          <div class="stat-grid" style="margin-top:12px">
            <div class="stat card">
              <div style="font-weight:800;font-size:18px">14</div>
              <div class="muted">Lessons</div>
            </div>
            <div class="stat card">
              <div style="font-weight:800;font-size:18px">12★</div>
              <div class="muted">Stars</div>
            </div>
            <div class="stat card">
              <div style="font-weight:800;font-size:18px">4</div>
              <div class="muted">Level</div>
            </div>
          </div>

          <div style="margin-top:12px;display:flex;gap:8px;flex-direction:column">
            <button class="big-cta" onclick="goScreen('parent')">Parent Settings</button>
            <div style="display:flex;gap:8px">
              <button class="start-btn" onclick="alert('Edit Profile - placeholder')">Edit Profile</button>
              <button class="screen-btn" onclick="alert('Support - placeholder')">Support</button>
            </div>
          </div>

        </div>
      </section>

      <!-- 06 Parent Control -->
      <section id="parent" class="screen card">
        <div>
          <div style="display:flex;justify-content:space-between;align-items:center">
            <div style="font-weight:900">Parent Controls</div>
            <div class="small">Secure PIN required</div>
          </div>

          <div style="margin-top:12px;display:flex;flex-direction:column;gap:10px">
            <div class="pc-row">
              <div>
                <div style="font-weight:800">Screen Time Limit</div>
                <div class="muted">Set daily minutes</div>
              </div>
              <div style="display:flex;gap:8px;align-items:center">
                <input type="number" id="timeLimit" value="45" style="width:80px;padding:6px;border-radius:8px;border:1px solid rgba(13,18,28,0.06)"/> mins
              </div>
            </div>

            <div class="pc-row">
              <div>
                <div style="font-weight:800">Game Access</div>
                <div class="muted">Allow or pause games</div>
              </div>
              <div>
                <div class="toggle on" id="toggleGames"><div class="knob"></div></div>
              </div>
            </div>

            <div class="pc-row">
              <div>
                <div style="font-weight:800">Notifications</div>
                <div class="muted">Email updates for progress</div>
              </div>
              <div>
                <div class="toggle" id="toggleNotif"><div class="knob"></div></div>
              </div>
            </div>

            <div style="margin-top:8px;display:flex;gap:8px">
              <button class="start-btn" onclick="saveParent()">Save Settings</button>
              <button class="screen-btn" onclick="goScreen('profile')">Back</button>
            </div>
          </div>
        </div>
      </section>

      <!-- 07 Reward -->
      <section id="reward" class="screen card">
        <div class="reward-center">
          <div style="text-align:center">
            <div class="trophy">★</div>
            <div style="font-weight:900;font-size:18px;margin-top:12px">You earned a Star!</div>
            <div class="muted" style="margin-top:6px">Great job completing the challenge</div>

            <div class="reward-cta">
              <button class="start-btn" onclick="goScreen('home')">Continue</button>
              <button class="small-cta" onclick="alert('Shared with parent')">Share with Parent</button>
            </div>
          </div>
        </div>
        <div class="confetti" id="confettiArea" aria-hidden="true"></div>
      </section>

    </div> <!-- phone end -->

  </div>

  <script>
    // Screen switching
    const screenBtns = document.querySelectorAll('.screen-btn[data-screen]');
    const screens = {
      onboarding: document.getElementById('onboarding'),
      home: document.getElementById('home'),
      lesson: document.getElementById('lesson'),
      challenge: document.getElementById('challenge'),
      profile: document.getElementById('profile'),
      parent: document.getElementById('parent'),
      reward: document.getElementById('reward')
    };

    function setActiveBtn(targetBtn){
      document.querySelectorAll('.screen-btn[data-screen]').forEach(b=>{
        b.classList.toggle('active', b===targetBtn);
      });
    }

    function goScreen(name){
      Object.values(screens).forEach(s=>s.classList.remove('active'));
      screens[name].classList.add('active');
      // set top bar highlighting
      const btn = Array.from(screenBtns).find(b => b.dataset.screen===name);
      if(btn) setActiveBtn(btn);

      // trigger confetti when reaching reward screen
      if(name==='reward') startConfetti();
      else stopConfetti();
    }

    screenBtns.forEach(btn=>{
      btn.addEventListener('click', ()=>goScreen(btn.dataset.screen));
    });

    // -------------------------
    // Onboarding logic (3 slides)
    // -------------------------
    const obSlides = [
      {title: 'Welcome, Little Coder!', desc: 'Meet FunBot — your friendly coding buddy. Learn through play, stories and puzzles.'},
      {title: 'Learn to Code with Play', desc: 'Use blocks to create sequences, loops and logic. Solve fun puzzles.'},
      {title: 'Let’s Get Started', desc: 'Create your avatar, try your first lesson and earn stars!'}
    ];
    let obIndex = 0;
    const obTitle = document.getElementById('ob-title');
    const obDesc = document.getElementById('ob-desc');
    const obDots = document.getElementById('ob-dots');
    const obPrev = document.getElementById('ob-prev');
    const obNext = document.getElementById('ob-next');

    function renderOnboarding(){
      const s = obSlides[obIndex];
      obTitle.textContent = s.title;
      obDesc.textContent = s.desc;
      Array.from(obDots.children).forEach((d,i)=>d.classList.toggle('active', i===obIndex));
      obPrev.style.visibility = obIndex===0 ? 'hidden' : 'visible';
      obNext.textContent = obIndex===obSlides.length-1 ? 'Start Learning' : 'Next';
    }

    obPrev.addEventListener('click', ()=>{ obIndex = Math.max(0, obIndex-1); renderOnboarding(); });
    obNext.addEventListener('click', ()=>{
      if(obIndex < obSlides.length-1){ obIndex++; renderOnboarding(); }
      else { goScreen('home'); }
    });

    renderOnboarding();

    // -------------------------
    // Drag and drop lesson
    // -------------------------
    const blocks = document.querySelectorAll('.block');
    const workspace = document.getElementById('workspace');
    const runBtn = document.getElementById('runBtn');
    const runOutput = document.getElementById('runOutput');

    blocks.forEach(b=>{
      b.addEventListener('dragstart', (e)=> {
        e.dataTransfer.setData('text/plain', b.dataset.type);
        setTimeout(()=> b.classList.add('dragging'), 0);
      });
      b.addEventListener('dragend', ()=> b.classList.remove('dragging'));
    });

    workspace.addEventListener('dragover', (e)=>{ e.preventDefault(); workspace.style.background='#F6FFFF' });
    workspace.addEventListener('dragleave', ()=> workspace.style.background='linear-gradient(180deg,#FFFFFF,#F6FBFF)');
    workspace.addEventListener('drop', (e)=>{
      e.preventDefault();
      workspace.style.background='linear-gradient(180deg,#FFFFFF,#F6FBFF)';
      const type = e.dataTransfer.getData('text/plain');
      const el = document.createElement('div');
      el.className = 'block';
      el.textContent = type==='move' ? 'Move Forward' : type==='jump' ? 'Jump' : 'Repeat x3';
      el.dataset.type = type;
      // allow removal on click
      el.addEventListener('click', ()=> el.remove());
      workspace.appendChild(el);
    });

    runBtn.addEventListener('click', ()=>{
      const seq = Array.from(workspace.querySelectorAll('.block')).map(b=>b.dataset.type);
      if(seq.length===0){
        runOutput.textContent = 'No blocks!';
        return;
      }
      // simple simulation
      let out = [];
      seq.forEach(t=>{
        if(t==='move') out.push('→');
        if(t==='jump') out.push('↑');
        if(t==='loop') out.push('↺↺↺');
      });
      runOutput.textContent = out.join(' ');
    });

    // -------------------------
    // Parent toggles
    // -------------------------
    document.getElementById('toggleGames').addEventListener('click', function(){ this.classList.toggle('on') });
    document.getElementById('toggleNotif').addEventListener('click', function(){ this.classList.toggle('on') });

    function saveParent(){
      const minutes = document.getElementById('timeLimit').value;
      alert('Parent settings saved. Daily limit: ' + minutes + ' mins');
      goScreen('profile');
    }

    // -------------------------
    // Confetti for reward
    // -------------------------
    let confettiInterval=null;
    function makeConfettiParticle(x, y){
      const el = document.createElement('div');
      el.style.position='absolute';
      el.style.left = x + 'px';
      el.style.top = y + 'px';
      el.style.width = (6 + Math.random()*8) + 'px';
      el.style.height = (8 + Math.random()*10) + 'px';
      el.style.background = ['#FFD93D','#FF6F61','#4AB7FF','#4CD964'][Math.floor(Math.random()*4)];
      el.style.transform = 'rotate('+(Math.random()*360)+'deg)';
      el.style.borderRadius = '2px';
      el.style.opacity = 0.95;
      el.style.zIndex = 9999;
      document.getElementById('confettiArea').appendChild(el);

      // animate downwards
      const dur = 1800 + Math.random()*1200;
      el.animate([
        { transform: 'translateY(0px) rotate(0deg)', opacity:1 },
        { transform: 'translateY('+ (220 + Math.random()*220) +'px) rotate(480deg)', opacity:0.9 }
      ], { duration: dur, easing: 'cubic-bezier(.2,.8,.2,1)' });
      setTimeout(()=> el.remove(), dur+100);
    }

    function startConfetti(){
      stopConfetti();
      const area = document.getElementById('confettiArea');
      confettiInterval = setInterval(()=>{
        const rect = area.getBoundingClientRect();
        const x = Math.random()*(rect.width-40) + 20;
        const y = -10;
        makeConfettiParticle(x, y);
      }, 120);
      // short burst
      setTimeout(()=> stopConfetti(), 3800);
    }

    function stopConfetti(){
      if(confettiInterval) clearInterval(confettiInterval);
      confettiInterval = null;
    }

    // keyboard shortcuts for quick navigation in prototype
    window.addEventListener('keydown', (e)=>{
      if(e.key==='1') goScreen('onboarding');
      if(e.key==='2') goScreen('home');
      if(e.key==='3') goScreen('lesson');
      if(e.key==='4') goScreen('challenge');
      if(e.key==='5') goScreen('profile');
      if(e.key==='6') goScreen('parent');
      if(e.key==='7') goScreen('reward');
    });

    // Helpful: initial focus on active screen button
    document.querySelector('.screen-btn.active')?.focus();
  </script>
</body>
</html>
