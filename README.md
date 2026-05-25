<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ALWIZZZ DEVV</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@400;600;700&display=swap" rel="stylesheet">
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  :root {
    --bg-deep: #0a0515;
    --bg-card: #110a2a;
    --bg-input: #1a0f35;
    --purple-main: #a855f7;
    --purple-light: #c084fc;
    --purple-glow: #7c3aed;
    --purple-btn: linear-gradient(135deg, #a855f7, #7c3aed);
    --purple-border: #6d28d9;
    --text-main: #f0e6ff;
    --text-muted: #9d7fc4;
    --error: #f87171;
    --success: #4ade80;
  }
  body {
    font-family: 'Rajdhani', sans-serif;
    background: var(--bg-deep);
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }
  body::before {
    content: '';
    position: fixed;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(ellipse at 60% 30%, rgba(124,58,237,0.15) 0%, transparent 60%),
                radial-gradient(ellipse at 20% 80%, rgba(168,85,247,0.1) 0%, transparent 50%);
    pointer-events: none;
    z-index: 0;
    animation: bgpulse 6s ease-in-out infinite alternate;
  }
  @keyframes bgpulse {
    from { opacity: 0.7; }
    to { opacity: 1; }
  }

  .page { display: none; position: relative; z-index: 1; width: 100%; max-width: 400px; padding: 0 20px; }
  .page.active { display: flex; flex-direction: column; align-items: center; }

  /* Floating particles */
  .particles { position: fixed; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; z-index: 0; overflow: hidden; }
  .particle {
    position: absolute;
    width: 3px;
    height: 3px;
    border-radius: 50%;
    background: var(--purple-light);
    opacity: 0;
    animation: float linear infinite;
  }
  @keyframes float {
    0% { transform: translateY(100vh) scale(0); opacity: 0; }
    10% { opacity: 0.6; }
    90% { opacity: 0.3; }
    100% { transform: translateY(-10vh) scale(1.5); opacity: 0; }
  }

  /* === LOGIN PAGE === */
  .login-avatar {
    width: 110px;
    height: 110px;
    border-radius: 26px;
    border: 2.5px solid var(--purple-main);
    box-shadow: 0 0 30px rgba(168,85,247,0.5), 0 0 60px rgba(124,58,237,0.2);
    margin-bottom: 28px;
    animation: avatarpulse 3s ease-in-out infinite;
    background: var(--bg-card);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 60px;
    overflow: hidden;
  }
  @keyframes avatarpulse {
    0%, 100% { box-shadow: 0 0 30px rgba(168,85,247,0.5), 0 0 60px rgba(124,58,237,0.2); }
    50% { box-shadow: 0 0 50px rgba(168,85,247,0.8), 0 0 90px rgba(124,58,237,0.4); }
  }
  .avatar-emoji { font-size: 60px; line-height: 1; }

  .login-title {
    font-family: 'Orbitron', monospace;
    font-size: 28px;
    font-weight: 900;
    color: var(--text-main);
    text-shadow: 0 0 20px rgba(168,85,247,0.6);
    margin-bottom: 6px;
    letter-spacing: 1px;
  }
  .login-sub {
    font-size: 15px;
    color: var(--text-muted);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 40px;
  }

  .input-group {
    width: 100%;
    position: relative;
    margin-bottom: 16px;
  }
  .input-icon {
    position: absolute;
    left: 16px;
    top: 50%;
    transform: translateY(-50%);
    font-size: 20px;
    color: var(--text-muted);
    pointer-events: none;
  }
  .input-group input {
    width: 100%;
    background: var(--bg-input);
    border: 1.5px solid rgba(109,40,217,0.4);
    border-radius: 14px;
    padding: 16px 50px 16px 48px;
    color: var(--text-main);
    font-family: 'Rajdhani', sans-serif;
    font-size: 16px;
    font-weight: 600;
    letter-spacing: 1px;
    outline: none;
    transition: all 0.3s;
  }
  .input-group input::placeholder { color: var(--text-muted); font-weight: 400; }
  .input-group input:focus {
    border-color: var(--purple-main);
    box-shadow: 0 0 20px rgba(168,85,247,0.25);
    background: #1f1240;
  }
  .eye-btn {
    position: absolute;
    right: 16px;
    top: 50%;
    transform: translateY(-50%);
    background: none;
    border: none;
    color: var(--text-muted);
    cursor: pointer;
    font-size: 20px;
    padding: 4px;
    transition: color 0.2s;
  }
  .eye-btn:hover { color: var(--purple-light); }

  .error-msg {
    color: var(--error);
    font-size: 13px;
    letter-spacing: 1px;
    text-align: center;
    margin-bottom: 12px;
    min-height: 20px;
    font-weight: 600;
    opacity: 0;
    transition: opacity 0.3s;
  }
  .error-msg.visible { opacity: 1; }

  .btn-signin {
    width: 100%;
    padding: 17px;
    border-radius: 14px;
    border: none;
    background: linear-gradient(135deg, #c084fc, #a855f7, #7c3aed);
    color: #fff;
    font-family: 'Orbitron', monospace;
    font-size: 16px;
    font-weight: 700;
    letter-spacing: 3px;
    cursor: pointer;
    margin-top: 8px;
    position: relative;
    overflow: hidden;
    transition: all 0.3s;
    box-shadow: 0 4px 25px rgba(124,58,237,0.5);
  }
  .btn-signin::before {
    content: '';
    position: absolute;
    top: 0; left: -100%;
    width: 100%; height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.15), transparent);
    transition: left 0.5s;
  }
  .btn-signin:hover::before { left: 100%; }
  .btn-signin:hover { transform: translateY(-2px); box-shadow: 0 8px 35px rgba(124,58,237,0.7); }
  .btn-signin:active { transform: scale(0.98); }

  /* Shake animation */
  @keyframes shake {
    0%, 100% { transform: translateX(0); }
    20% { transform: translateX(-8px); }
    40% { transform: translateX(8px); }
    60% { transform: translateX(-6px); }
    80% { transform: translateX(6px); }
  }
  .shake { animation: shake 0.4s ease; }

  /* === MAIN PAGE === */
  .main-header {
    text-align: center;
    margin-bottom: 40px;
    width: 100%;
  }
  .main-logo {
    width: 90px;
    height: 90px;
    border-radius: 22px;
    background: linear-gradient(135deg, #1a0f35, #2d1060);
    border: 2px solid var(--purple-main);
    box-shadow: 0 0 30px rgba(168,85,247,0.4);
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto 20px;
    font-size: 48px;
    animation: avatarpulse 3s ease-in-out infinite;
  }
  .main-title {
    font-family: 'Orbitron', monospace;
    font-size: 22px;
    font-weight: 900;
    color: var(--text-main);
    letter-spacing: 3px;
    text-shadow: 0 0 20px rgba(168,85,247,0.7);
    margin-bottom: 6px;
  }
  .title-line {
    width: 80px;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--purple-main), transparent);
    margin: 10px auto 0;
  }

  .card-form {
    width: 100%;
    background: var(--bg-card);
    border-radius: 20px;
    border: 1px solid rgba(109,40,217,0.35);
    padding: 28px 24px;
    box-shadow: 0 0 40px rgba(124,58,237,0.15);
  }
  .form-label {
    font-size: 12px;
    letter-spacing: 2px;
    color: var(--text-muted);
    text-transform: uppercase;
    margin-bottom: 8px;
    display: block;
    font-weight: 600;
  }
  .form-textarea {
    width: 100%;
    background: var(--bg-input);
    border: 1.5px solid rgba(109,40,217,0.4);
    border-radius: 14px;
    padding: 16px 18px;
    color: var(--text-main);
    font-family: 'Rajdhani', sans-serif;
    font-size: 15px;
    font-weight: 500;
    outline: none;
    resize: none;
    min-height: 100px;
    letter-spacing: 0.5px;
    transition: all 0.3s;
  }
  .form-textarea::placeholder { color: var(--text-muted); }
  .form-textarea:focus {
    border-color: var(--purple-main);
    box-shadow: 0 0 20px rgba(168,85,247,0.2);
  }

  .btn-confirm {
    width: 100%;
    padding: 16px;
    border-radius: 14px;
    border: none;
    background: linear-gradient(135deg, #c084fc, #a855f7, #7c3aed);
    color: #fff;
    font-family: 'Orbitron', monospace;
    font-size: 14px;
    font-weight: 700;
    letter-spacing: 2px;
    cursor: pointer;
    margin-top: 20px;
    position: relative;
    overflow: hidden;
    transition: all 0.3s;
    box-shadow: 0 4px 25px rgba(124,58,237,0.4);
  }
  .btn-confirm::before {
    content: '';
    position: absolute;
    top: 0; left: -100%;
    width: 100%; height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.15), transparent);
    transition: left 0.5s;
  }
  .btn-confirm:hover::before { left: 100%; }
  .btn-confirm:hover { transform: translateY(-2px); box-shadow: 0 8px 35px rgba(124,58,237,0.6); }
  .btn-confirm:active { transform: scale(0.98); }
  .btn-confirm:disabled { opacity: 0.6; cursor: not-allowed; transform: none; }

  /* === LOADING OVERLAY === */
  .loading-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(5, 2, 15, 0.92);
    z-index: 100;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    backdrop-filter: blur(8px);
  }
  .loading-overlay.active { display: flex; }

  .loading-spinner {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    border: 3px solid rgba(168,85,247,0.15);
    border-top: 3px solid var(--purple-main);
    border-right: 3px solid var(--purple-light);
    animation: spin 0.9s linear infinite;
    margin-bottom: 28px;
    box-shadow: 0 0 30px rgba(168,85,247,0.3);
  }
  @keyframes spin { to { transform: rotate(360deg); } }

  .loading-icon {
    font-size: 36px;
    position: absolute;
    animation: iconpulse 1.5s ease-in-out infinite;
  }
  @keyframes iconpulse {
    0%, 100% { transform: scale(0.9); opacity: 0.7; }
    50% { transform: scale(1.1); opacity: 1; }
  }
  .loading-wrapper { position: relative; display: flex; align-items: center; justify-content: center; }

  .loading-text {
    font-family: 'Orbitron', monospace;
    font-size: 13px;
    color: var(--purple-light);
    letter-spacing: 2px;
    text-align: center;
    animation: textpulse 1.5s ease-in-out infinite;
  }
  @keyframes textpulse {
    0%, 100% { opacity: 0.6; }
    50% { opacity: 1; }
  }
  .loading-dest {
    font-family: 'Rajdhani', sans-serif;
    font-size: 16px;
    color: var(--text-muted);
    letter-spacing: 1px;
    text-align: center;
    margin-top: 8px;
    max-width: 280px;
  }
  .loading-dest span {
    color: var(--purple-light);
    font-weight: 700;
  }

  /* Progress dots */
  .loading-dots { display: flex; gap: 8px; margin-top: 20px; }
  .dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: var(--purple-border);
    animation: dotpulse 1.2s ease-in-out infinite;
  }
  .dot:nth-child(2) { animation-delay: 0.2s; }
  .dot:nth-child(3) { animation-delay: 0.4s; }
  @keyframes dotpulse {
    0%, 100% { background: var(--purple-border); transform: scale(1); }
    50% { background: var(--purple-light); transform: scale(1.4); }
  }

  /* === SUCCESS === */
  .success-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(5, 2, 15, 0.92);
    z-index: 100;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    backdrop-filter: blur(8px);
  }
  .success-overlay.active { display: flex; }

  .success-circle {
    width: 110px;
    height: 110px;
    border-radius: 50%;
    background: rgba(74,222,128,0.1);
    border: 2px solid var(--success);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 50px;
    margin-bottom: 28px;
    animation: successpop 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    box-shadow: 0 0 40px rgba(74,222,128,0.3);
  }
  @keyframes successpop {
    from { transform: scale(0); opacity: 0; }
    to { transform: scale(1); opacity: 1; }
  }
  .success-title {
    font-family: 'Orbitron', monospace;
    font-size: 20px;
    font-weight: 900;
    color: var(--success);
    letter-spacing: 3px;
    text-shadow: 0 0 20px rgba(74,222,128,0.5);
    margin-bottom: 10px;
    text-align: center;
  }
  .success-sub {
    font-size: 15px;
    color: var(--text-muted);
    letter-spacing: 1px;
    text-align: center;
    margin-bottom: 30px;
    max-width: 260px;
    line-height: 1.5;
  }
  .success-sub strong { color: var(--purple-light); }
  .btn-back {
    padding: 14px 36px;
    border-radius: 14px;
    border: 1.5px solid var(--purple-main);
    background: transparent;
    color: var(--purple-light);
    font-family: 'Orbitron', monospace;
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 2px;
    cursor: pointer;
    transition: all 0.3s;
  }
  .btn-back:hover { background: rgba(168,85,247,0.15); transform: translateY(-1px); }

  /* Confetti */
  .confetti-piece {
    position: fixed;
    width: 10px;
    height: 10px;
    top: -10px;
    pointer-events: none;
    z-index: 200;
    animation: confetti-fall linear forwards;
  }
  @keyframes confetti-fall {
    to { transform: translateY(110vh) rotate(720deg); opacity: 0; }
  }

  /* Page transition */
  @keyframes pagein {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .page.active { animation: pagein 0.5s ease; }
</style>
</head>
<body>

<!-- Particles -->
<div class="particles" id="particles"></div>

<!-- Loading Overlay -->
<div class="loading-overlay" id="loadingOverlay">
  <div class="loading-wrapper">
    <div class="loading-spinner"></div>
    <div class="loading-icon">📤</div>
  </div>
  <div class="loading-text">MENGIRIM bug...</div>
  <div class="loading-dest" id="loadingDest">Mengirim ke <span id="destTarget">—</span></div>
  <div class="loading-dots">
    <div class="dot"></div>
    <div class="dot"></div>
    <div class="dot"></div>
  </div>
</div>

<!-- Success Overlay -->
<div class="success-overlay" id="successOverlay">
  <div class="success-circle">✅</div>
  <div class="success-title">udh terkirim nunggu 5 mnit anj!</div>
  <div class="success-sub" id="successMsg">bug berhasil dikirim ke <strong id="successDest">—</strong></div>
  <button class="btn-back" onclick="closeSuccess()">KIRIM LAGI</button>
</div>

<!-- ===== PAGE 1: LOGIN ===== -->
<div class="page active" id="loginPage">
  <div class="login-avatar">
    <span class="avatar-emoji">👾</span>
  </div>
  <div class="login-title">Welcome Back</div>
  <div class="login-sub">Sign in to continue</div>

  <div class="input-group">
    <span class="input-icon">👤</span>
    <input type="text" id="username" placeholder="Username" autocomplete="off" spellcheck="false">
  </div>

  <div class="input-group">
    <span class="input-icon">🔒</span>
    <input type="password" id="password" placeholder="Password" id="password" autocomplete="off">
    <button class="eye-btn" onclick="togglePw(this)" tabindex="-1">🙈</button>
  </div>

  <div class="error-msg" id="errorMsg">⚠ Username atau Password salah!</div>

  <button class="btn-signin" onclick="doLogin()">SIGN IN</button>
</div>

<!-- ===== PAGE 2: MAIN ===== -->
<div class="page" id="mainPage">
  <div class="main-header">
    <div class="main-logo">⚡</div>
    <div class="main-title">APK BUG ALWIZZ</div>
    <div class="title-line"></div>
  </div>

  <div class="card-form">
    <label class="form-label">Nomor target😈</label>
    <div class="input-group" style="margin-bottom: 0;">
      <span class="input-icon">👾</span>
      <input type="text" id="targetInput" placeholder="Masukkan tujuan..." style="padding-left: 48px; border-radius: 14px;">
    </div>

    <div style="margin-top: 20px;">
      <label class="form-label">Kronologi</label>
      <textarea class="form-textarea" id="msgInput" placeholder="kronologinya apa......."></textarea>
    </div>

    <button class="btn-confirm" id="confirmBtn" onclick="doConfirm()">KONFIRMASI ✦</button>
  </div>
</div>

<script>
  // Particles
  const p = document.getElementById('particles');
  for (let i = 0; i < 25; i++) {
    const d = document.createElement('div');
    d.className = 'particle';
    d.style.left = Math.random() * 100 + '%';
    d.style.animationDuration = (8 + Math.random() * 14) + 's';
    d.style.animationDelay = (Math.random() * 10) + 's';
    d.style.width = d.style.height = (2 + Math.random() * 4) + 'px';
    d.style.opacity = 0.3 + Math.random() * 0.5;
    p.appendChild(d);
  }

  function togglePw(btn) {
    const pw = document.getElementById('password');
    if (pw.type === 'password') { pw.type = 'text'; btn.textContent = '👁'; }
    else { pw.type = 'password'; btn.textContent = '🙈'; }
  }

  function doLogin() {
    const u = document.getElementById('username').value.trim();
    const pw = document.getElementById('password').value;
    const err = document.getElementById('errorMsg');
    const fields = document.querySelectorAll('#loginPage input');

    if (u === 'alwizz26' && pw === 'alwizz655321') {
      err.classList.remove('visible');
      document.getElementById('loginPage').classList.remove('active');
      document.getElementById('mainPage').classList.add('active');
    } else {
      err.classList.add('visible');
      fields.forEach(f => { f.classList.add('shake'); setTimeout(() => f.classList.remove('shake'), 500); });
      document.getElementById('password').value = '';
    }
  }

  document.addEventListener('keydown', e => {
    if (e.key === 'Enter') {
      if (document.getElementById('loginPage').classList.contains('active')) doLogin();
    }
  });

  function doConfirm() {
    const target = document.getElementById('targetInput').value.trim();
    if (!target) {
      document.getElementById('targetInput').style.borderColor = '#f87171';
      document.getElementById('targetInput').style.boxShadow = '0 0 15px rgba(248,113,113,0.3)';
      setTimeout(() => {
        document.getElementById('targetInput').style.borderColor = '';
        document.getElementById('targetInput').style.boxShadow = '';
      }, 1500);
      return;
    }

    document.getElementById('destTarget').textContent = target;
    document.getElementById('loadingOverlay').classList.add('active');
    document.getElementById('confirmBtn').disabled = true;

    setTimeout(() => {
      document.getElementById('loadingOverlay').classList.remove('active');
      document.getElementById('successDest').textContent = target;
      document.getElementById('successOverlay').classList.add('active');
      spawnConfetti();
    }, 3000);
  }

  function closeSuccess() {
    document.getElementById('successOverlay').classList.remove('active');
    document.getElementById('confirmBtn').disabled = false;
    document.getElementById('targetInput').value = '';
    document.getElementById('msgInput').value = '';
  }

  function spawnConfetti() {
    const colors = ['#a855f7','#c084fc','#7c3aed','#4ade80','#f0abfc','#818cf8'];
    for (let i = 0; i < 40; i++) {
      const c = document.createElement('div');
      c.className = 'confetti-piece';
      c.style.left = Math.random() * 100 + 'vw';
      c.style.background = colors[Math.floor(Math.random() * colors.length)];
      c.style.borderRadius = Math.random() > 0.5 ? '50%' : '2px';
      c.style.width = c.style.height = (6 + Math.random() * 10) + 'px';
      c.style.animationDuration = (1.5 + Math.random() * 2) + 's';
      c.style.animationDelay = (Math.random() * 0.8) + 's';
      document.body.appendChild(c);
      setTimeout(() => c.remove(), 4000);
    }
  }
</script>
</body>
