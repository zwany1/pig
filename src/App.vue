<template>
  <div class="cia-app">
    <!-- 顶部条 -->
    <div class="top-bar">
      <a href="#">Contact</a>
      <a href="#">Report Information</a>
    </div>

    <!-- 导航 -->
    <nav class="nav">
      <a class="nav-logo" href="#">
        <span class="nav-logo-eagle">
          <img src="/image.png" alt="CIA Seal" style="height:48px;width:48px;">
        </span>
        <span class="nav-logo-text">
          CENTRAL INTELLIGENCE AGENCY
          <small>INTELLIGENCE COMMUNITY MEMBER</small>
        </span>
      </a>
      <ul class="nav-links">
        <li><a href="#">Today's CIA</a></li>
        <li><a href="#">Careers</a></li>
        <li><a href="#">Legacy</a></li>
        <li><a href="#">Newsroom</a></li>
        <li><a href="#">Library</a></li>
      </ul>
      <span class="nav-search">Search CIA.gov</span>
    </nav>

    <main>
      <!-- About 头部 -->
      <div class="about-lead">
        <h1>About CIA</h1>
        <p>Our mission is straightforward but critical: leverage the power of information to keep our Nation safe.</p>
        <div class="seal-row">
          <span class="eagle">
            <img src="/image.png" alt="CIA Seal" style="height:48px;width:48px;">
          </span>
          <span class="divider"></span>
          <span class="signature">
            The CIA seal features several symbols:<br>
            an eagle for alertness, a shield for defense,<br>
            and a compass rose for global intelligence collection.
          </span>
        </div>
      </div>

      <!-- 引用块 -->
      <div class="hero-quote">
        <p>"We are the Nation's first line of defense.<br>We accomplish what others cannot accomplish and go where others cannot go."</p>
        <span class="established">Established in 1947</span>
      </div>

      <!-- What is CIA + What We Do -->
      <div class="grid-2col">
        <div>
          <h2>What is CIA?</h2>
          <p>The CIA is a U.S. government agency that provides objective intelligence on foreign countries and global issues to the president, the National Security Council, and other policymakers to help them make national security decisions.</p>
        </div>
        <div>
          <h2>What We Do</h2>
          <p>To stop threats before they happen and further U.S. national security objectives, we:</p>
          <ul>
            <li>Collect foreign intelligence;</li>
            <li>Produce objective analysis; and</li>
            <li>Conduct covert action, as directed by the president.</li>
          </ul>
          <p class="note">We do not make policy or policy recommendations. Instead, our Agency serves as an independent source of information for people who do.</p>
          <p class="note">We are not a law enforcement organization.</p>
        </div>
      </div>

      <!-- 密码验证卡片 -->
      <div ref="accessCard" class="access-card" :class="{ glitch: isGlitch, shake: isShake }">
        <div class="watermark">TOP SECRET // CLASSIFIED</div>
        <div class="scan-line"></div>
        <div class="scan-texture"></div>
        <h2>🛡 CIA人口搜索系统</h2>
        <div class="card-sub">// CLASSIFIED ACCESS PORTAL //</div>
        <div class="card-warning">
          本系统仅限授权人员访问。<br>
          未经授权的访问企图将被记录并追踪。<br>
          AUTHORIZED PERSONNEL ONLY.
        </div>
        <div class="legal-warning">
          ⚠ 法律警告：登录该网站你将违背<br>
          《日内瓦公约》《主动防御战略守则》《青少年网络健康管理条例》
        </div>
        <div class="input-row">
          <div class="input-wrapper">
            <input
              ref="pwdInput"
              v-model="password"
              :type="showPwd ? 'text' : 'password'"
              placeholder="输入访问密钥"
              maxlength="20"
              autocomplete="off"
              @keypress.enter="checkPwd"
            />
            <span class="toggle-pwd" @click="showPwd = !showPwd" title="显示/隐藏密码">{{ showPwd ? '🙈' : '👁️' }}</span>
          </div>
          <button @click="checkPwd">验证</button>
        </div>
        <div class="hint">提示：密码为 zwycool</div>
        <div class="error-msg" :style="{ color: errColor }">{{ errMsg }}</div>
        <div style="margin-top:16px;font-family:'Arial',sans-serif;font-size:10px;color:#bbb;letter-spacing:1px;">SESSION-ID: X7-CIA-88291-DECRYPT</div>
      </div>

      <!-- 解密后视频 -->
      <div v-if="decrypted" class="video-container">
        <div class="video-inner">
          <h3 class="video-title">🔓 机密内容已解密</h3>
          <video controls autoplay class="cia-video" @ended="closeVideo">
            <source src="/2.mp4" type="video/mp4">
            您的浏览器不支持视频播放。
          </video>
        </div>
      </div>

      <!-- 探索更多 -->
      <div class="explore-section">
        <h2>Explore More</h2>
        <div class="explore-grid">
          <div class="explore-card">
            <div class="icon">📜</div>
            <h3>Legacy</h3>
            <p>Explore our history</p>
          </div>
          <div class="explore-card">
            <div class="icon">📰</div>
            <h3>News and Stories</h3>
            <p>Latest from CIA</p>
          </div>
          <div class="explore-card">
            <div class="icon">📄</div>
            <h3>Publications</h3>
            <p>Official documents</p>
          </div>
          <div class="explore-card">
            <div class="icon">⚙</div>
            <h3>Technology</h3>
            <p>Innovation at CIA</p>
          </div>
        </div>
      </div>

      <!-- CTA -->
      <div class="cta-banner">
        <h2>Your Talent. Your Diverse Skills. Our Mission.</h2>
        <p>Make a difference in your career. We're looking for students, recent graduates, and professionals to join our team.</p>
        <a class="cta-btn" href="#" @click.prevent="$refs.pwdInput?.focus()">Browse Jobs →</a>
      </div>
    </main>

    <!-- 页脚 -->
    <footer>
      <div class="footer-inner">
        <div class="footer-col">
          <h4>Agency</h4>
          <a href="#">About CIA</a>
          <a href="#">Leadership</a>
          <a href="#">Organization</a>
          <a href="#">Mission and Vision</a>
          <a href="#">CIA Museum</a>
        </div>
        <div class="footer-col">
          <h4>Careers</h4>
          <a href="#">Career Opportunities</a>
          <a href="#">Hiring Process</a>
          <a href="#">Student Programs</a>
          <a href="#">Accommodations</a>
          <a href="#">MyLINK</a>
        </div>
        <div class="footer-col">
          <h4>Resources</h4>
          <a href="#">News and Stories</a>
          <a href="#">Center for the Study of Intelligence</a>
          <a href="#">World Leaders</a>
          <a href="#">The Langley Files</a>
          <a href="#">Spy Kids</a>
        </div>
        <div class="footer-col">
          <h4>Helpful Links</h4>
          <a href="#">Partner with CIA</a>
          <a href="#">Prepublication Review</a>
          <a href="#">Freedom of Information Act</a>
          <a href="#">Frequently Asked Questions</a>
          <a href="#">Privacy Policy</a>
        </div>
      </div>

      <div class="footer-social">
        <span>Central Intelligence Agency</span>
        <div class="social-icons">
          <a href="#">Instagram</a>
          <a href="#">Facebook</a>
          <a href="#">X</a>
          <a href="#">LinkedIn</a>
          <a href="#">YouTube</a>
          <a href="#">Flickr</a>
          <a href="#">Telegram</a>
        </div>
      </div>

      <div class="footer-bottom">
        <span>Search CIA.gov</span>
        <div class="links">
          <a href="#">Site Policies</a>
          <a href="#">Privacy</a>
          <a href="#">No FEAR Act</a>
          <a href="#">EEO</a>
          <a href="#">Inspector General</a>
          <a href="#">USA.gov</a>
          <a href="#">Sitemap</a>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted, nextTick } from 'vue'

const CORRECT_PWD = 'zwycool'

const password = ref('')
const showPwd = ref(false)
const errMsg = ref('')
const errColor = ref('#ef5350')
const isGlitch = ref(false)
const isShake = ref(false)
const decrypted = ref(false)
const accessCard = ref(null)
const pwdInput = ref(null)

function closeVideo() {
  decrypted.value = false
  errMsg.value = '✓ 文件已销毁，会话已清除'
  errColor.value = '#4fc3f7'
  password.value = ''
  pwdInput.value?.focus()
}

function checkPwd() {
  if (password.value === CORRECT_PWD) {
    isShake.value = false
    isGlitch.value = false
    errColor.value = '#4fc3f7'
    errMsg.value = '✓ 密码正确正在解密文件,10s后自动销毁...'
    setTimeout(() => {
      decrypted.value = true
    }, 800)
  } else {
    isGlitch.value = false
    isShake.value = false
    nextTick(() => {
      isGlitch.value = true
      isShake.value = true
      setTimeout(() => { isGlitch.value = false }, 1000)
    })
    errColor.value = '#ef5350'
    errMsg.value = '× 访问被拒绝，密钥错误'
    password.value = ''
    pwdInput.value?.focus()
  }
}

onMounted(() => {
  pwdInput.value?.focus()
})
</script>

<style>
/* ===== 全局重置 ===== */
*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

.cia-app {
  background: #f5f5f0;
  color: #1a1a1a;
  font-family: 'Georgia', 'Times New Roman', 'Noto Serif SC', serif;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
}

/* ===== 顶部通栏 ===== */
.top-bar {
  width: 100%;
  background: #002b7f;
  color: #fff;
  font-size: 12px;
  padding: 6px 40px;
  display: flex;
  justify-content: flex-end;
  gap: 24px;
  font-family: 'Arial', 'Helvetica Neue', sans-serif;
  letter-spacing: 0.3px;
}
.top-bar a {
  color: #fff;
  text-decoration: none;
}
.top-bar a:hover { text-decoration: underline; }

/* ===== 导航 ===== */
.nav {
  width: 100%;
  max-width: 1200px;
  padding: 16px 40px 12px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid #d4d4d4;
  background: #fff;
}
.nav-logo {
  display: flex;
  align-items: center;
  gap: 10px;
  text-decoration: none;
}
.nav-logo-eagle {
  font-size: 32px;
  line-height: 1;
  display: flex;
  align-items: center;
}
.nav-logo-text {
  font-family: 'Arial', 'Helvetica Neue', sans-serif;
  font-weight: 700;
  font-size: 14px;
  color: #002b7f;
  letter-spacing: 1.5px;
  line-height: 1.2;
}
.nav-logo-text small {
  display: block;
  font-weight: 300;
  font-size: 9px;
  color: #666;
  letter-spacing: 1px;
}
.nav-links {
  display: flex;
  list-style: none;
  gap: 28px;
  font-family: 'Arial', 'Helvetica Neue', sans-serif;
  font-size: 13px;
  font-weight: 600;
  letter-spacing: 0.5px;
}
.nav-links a {
  color: #1a1a1a;
  text-decoration: none;
}
.nav-links a:hover { color: #002b7f; }
.nav-search {
  font-family: 'Arial', sans-serif;
  font-size: 13px;
  color: #002b7f;
  font-weight: 600;
  cursor: default;
}

/* ===== 主体 ===== */
main {
  width: 100%;
  max-width: 1200px;
  padding: 60px 40px 40px;
  flex: 1;
}

/* ===== 关于段落 ===== */
.about-lead {
  text-align: center;
  max-width: 800px;
  margin: 0 auto 48px;
}
.about-lead h1 {
  font-family: 'Georgia', 'Times New Roman', 'Noto Serif SC', serif;
  font-size: 44px;
  font-weight: 700;
  color: #002b7f;
  margin-bottom: 24px;
  letter-spacing: 1px;
}
.about-lead p {
  font-size: 18px;
  line-height: 1.7;
  color: #333;
  margin-bottom: 28px;
}
.about-lead .seal-row {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
  margin: 20px 0 10px;
}
.about-lead .eagle {
  display: flex;
  align-items: center;
}
.about-lead .divider {
  width: 1px;
  height: 40px;
  background: #ccc;
}
.about-lead .signature {
  font-family: 'Arial', sans-serif;
  font-size: 11px;
  color: #666;
  text-align: left;
  line-height: 1.4;
  letter-spacing: 0.5px;
}

/* ===== 引用块 ===== */
.hero-quote {
  background: #eef3fa;
  border-left: 4px solid #002b7f;
  padding: 32px 40px;
  margin: 0 auto 48px;
  max-width: 800px;
  text-align: center;
}
.hero-quote p {
  font-family: 'Georgia', 'Times New Roman', 'Noto Serif SC', serif;
  font-size: 22px;
  font-weight: 700;
  color: #002b7f;
  line-height: 1.5;
  font-style: italic;
}
.hero-quote .established {
  display: inline-block;
  margin-top: 12px;
  font-family: 'Arial', sans-serif;
  font-size: 13px;
  font-weight: 600;
  color: #666;
  letter-spacing: 2px;
  font-style: normal;
}

/* ===== 内容网格 ===== */
.grid-2col {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  margin-bottom: 48px;
}
.grid-2col h2 {
  font-family: 'Georgia', 'Times New Roman', 'Noto Serif SC', serif;
  font-size: 24px;
  font-weight: 700;
  color: #002b7f;
  margin-bottom: 16px;
}
.grid-2col p {
  font-size: 15px;
  line-height: 1.7;
  color: #333;
  margin-bottom: 12px;
}
.grid-2col ul {
  list-style: none;
  padding: 0;
}
.grid-2col ul li {
  font-size: 14px;
  line-height: 1.7;
  color: #333;
  padding-left: 18px;
  position: relative;
  margin-bottom: 4px;
}
.grid-2col ul li::before {
  content: '*';
  position: absolute;
  left: 0;
  color: #002b7f;
  font-weight: bold;
}
.grid-2col .note {
  font-size: 13px;
  color: #666;
  font-style: italic;
  margin-top: 8px;
}

/* ===== 密码验证卡片 ===== */
.access-card {
  background: #f5f5f0;
  border: 1px solid #d4d4d4;
  padding: 40px 48px;
  max-width: 560px;
  margin: 0 auto 48px;
  text-align: center;
  box-shadow: 0 4px 24px rgba(0,0,0,0.12), inset 0 0 0 1px #cc0000;
  position: relative;
  overflow: hidden;
  color: #1a1a1a;
}
.watermark {
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%) rotate(-25deg);
  font-family: 'Arial', sans-serif;
  font-size: 36px;
  font-weight: 900;
  color: rgba(204,0,0,0.06);
  letter-spacing: 6px;
  white-space: nowrap;
  pointer-events: none;
  user-select: none;
  z-index: 0;
}
.scan-line {
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, #4fc3f7, transparent);
  opacity: 0;
  animation: cia-scan 3s ease-in-out infinite;
  pointer-events: none;
  z-index: 10;
}
@keyframes cia-scan {
  0%   { top: 0; opacity: 0; }
  10%  { opacity: 0.7; }
  90%  { opacity: 0.7; }
  100% { top: 100%; opacity: 0; }
}
.scan-texture {
  position: absolute;
  top: 0; left: 0; right: 0; bottom: 0;
  background: repeating-linear-gradient(
    0deg,
    transparent 0px,
    transparent 2px,
    rgba(0, 80, 200, 0.04) 2px,
    rgba(0, 80, 200, 0.04) 4px
  );
  pointer-events: none;
  z-index: 1;
}
@keyframes cia-glitch {
  0%   { opacity: 1; transform: translate(0); }
  20%  { opacity: 0.8; transform: translate(-3px, 1px); }
  40%  { opacity: 0.85; transform: translate(3px, -1px); }
  60%  { opacity: 0.75; transform: translate(-2px, 2px); border-color: #ff0000; }
  80%  { opacity: 0.9; transform: translate(1px, -1px); }
  100% { opacity: 1; transform: translate(0); }
}
.access-card.glitch {
  animation: cia-glitch 0.3s ease-in-out 3;
  border-color: #ef5350;
  box-shadow: 0 0 40px rgba(239,83,80,0.3);
}
@keyframes cia-shake {
  0%, 100% { transform: translateX(0); }
  10% { transform: translateX(-8px); }
  20% { transform: translateX(8px); }
  30% { transform: translateX(-6px); }
  40% { transform: translateX(6px); }
  50% { transform: translateX(-4px); }
  60% { transform: translateX(4px); }
  70% { transform: translateX(-2px); }
  80% { transform: translateX(2px); }
}
.access-card.shake { animation: cia-shake 0.5s ease-in-out; }
.access-card h2 {
  font-family: 'Courier New', monospace;
  font-size: 18px;
  color: #4fc3f7;
  margin-bottom: 6px;
  letter-spacing: 2px;
  text-shadow: 0 0 10px rgba(79,195,247,0.3);
  position: relative;
  z-index: 2;
}
.access-card .card-sub {
  font-family: 'Courier New', monospace;
  font-size: 10px;
  color: #ef5350;
  letter-spacing: 3px;
  margin-bottom: 20px;
  text-transform: uppercase;
  animation: ciasub-blink 1.2s step-end infinite;
  position: relative;
  z-index: 2;
}
@keyframes ciasub-blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}
.access-card .card-warning {
  font-family: 'Courier New', monospace;
  font-size: 11px;
  color: #ff8a80;
  line-height: 1.7;
  margin-bottom: 18px;
  padding: 14px 0;
  border-top: 1px solid #ef5350;
  border-bottom: 1px solid #ef5350;
  text-shadow: 0 0 4px rgba(239,83,80,0.2);
  position: relative;
  z-index: 2;
}
.access-card .legal-warning {
  background: rgba(239,83,80,0.06);
  border: 1px solid #ef5350;
  color: #ff8a80;
  font-size: 10px;
  font-family: 'Courier New', monospace;
  padding: 10px 12px;
  margin-bottom: 18px;
  line-height: 1.8;
  text-align: center;
  letter-spacing: 0.5px;
  position: relative;
  z-index: 2;
  box-shadow: 0 0 8px rgba(239,83,80,0.12);
}
.access-card .input-row {
  display: flex;
  gap: 10px;
  margin-bottom: 12px;
  position: relative;
  z-index: 2;
}
.access-card .input-wrapper {
  flex: 1;
  position: relative;
}
.access-card .input-wrapper input {
  width: 100%;
  background: #f9f9f9;
  border: 1px solid #ccc;
  color: #1a1a1a;
  font-family: 'Courier New', monospace;
  font-size: 16px;
  padding: 10px 40px 10px 14px;
  letter-spacing: 4px;
  outline: none;
  transition: border 0.2s;
}
.access-card .input-wrapper input:focus {
  border-color: #002b7f;
  box-shadow: 0 0 0 2px rgba(0,43,127,0.15);
}
.access-card .input-wrapper input::placeholder {
  letter-spacing: 1px;
  font-size: 12px;
  color: #aaa;
}
.access-card .toggle-pwd {
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
  cursor: pointer;
  font-size: 18px;
  user-select: none;
  z-index: 3;
  color: #888;
  transition: color 0.2s;
  line-height: 1;
}
.access-card .toggle-pwd:hover {
  color: #002b7f;
}
.access-card button {
  background: transparent;
  color: #4fc3f7;
  border: 1px solid #4fc3f7;
  padding: 12px 28px;
  font-family: 'Courier New', monospace;
  font-weight: 600;
  font-size: 13px;
  letter-spacing: 2px;
  cursor: pointer;
  transition: all 0.2s;
  text-transform: uppercase;
  position: relative;
  z-index: 2;
}
.access-card button:hover {
  background: rgba(79,195,247,0.1);
  box-shadow: 0 0 16px rgba(79,195,247,0.25);
}
.access-card button:active {
  background: rgba(239,83,80,0.2);
  border-color: #ef5350;
}
.access-card .hint {
  font-family: 'Courier New', monospace;
  font-size: 11px;
  color: #555;
  position: relative;
  z-index: 2;
}
.error-msg {
  color: #ef5350;
  font-size: 12px;
  margin-top: 12px;
  min-height: 16px;
  letter-spacing: 0.5px;
  font-family: 'Courier New', monospace;
}

/* ===== 解密视频容器 ===== */
.video-container {
  max-width: 800px;
  margin: 0 auto 48px;
}
.video-inner {
  background: #0a0a0f;
  border: 1px solid #4fc3f7;
  padding: 20px;
  text-align: center;
  box-shadow: 0 0 30px rgba(79,195,247,0.2);
}
.video-title {
  font-family: 'Courier New', monospace;
  color: #4fc3f7;
  margin-bottom: 16px;
  text-shadow: 0 0 10px rgba(79,195,247,0.3);
}
.cia-video {
  width: 100%;
  max-height: 70vh;
  border: 1px solid #1a3a6c;
}

/* ===== 探索更多 ===== */
.explore-section {
  margin: 0 auto 48px;
  max-width: 800px;
}
.explore-section h2 {
  font-family: 'Georgia', 'Times New Roman', 'Noto Serif SC', serif;
  font-size: 24px;
  font-weight: 700;
  color: #002b7f;
  text-align: center;
  margin-bottom: 24px;
}
.explore-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 16px;
}
.explore-card {
  border: 1px solid #d4d4d4;
  padding: 28px 16px;
  text-align: center;
  background: #fff;
  transition: box-shadow 0.2s;
  cursor: default;
}
.explore-card:hover {
  box-shadow: 0 2px 12px rgba(0,0,0,0.1);
}
.explore-card .icon {
  font-size: 28px;
  margin-bottom: 8px;
}
.explore-card h3 {
  font-family: 'Georgia', 'Times New Roman', serif;
  font-size: 16px;
  color: #002b7f;
  margin-bottom: 4px;
}
.explore-card p {
  font-family: 'Arial', sans-serif;
  font-size: 11px;
  color: #888;
  letter-spacing: 0.5px;
}

/* ===== CTA 横幅 ===== */
.cta-banner {
  background: #002b7f;
  color: #fff;
  text-align: center;
  padding: 40px 48px;
  max-width: 800px;
  margin: 0 auto 48px;
}
.cta-banner h2 {
  font-family: 'Georgia', 'Times New Roman', serif;
  font-size: 26px;
  font-weight: 700;
  margin-bottom: 12px;
}
.cta-banner p {
  font-family: 'Arial', sans-serif;
  font-size: 14px;
  line-height: 1.6;
  max-width: 500px;
  margin: 0 auto 20px;
  opacity: 0.9;
}
.cta-banner .cta-btn {
  display: inline-block;
  background: #fff;
  color: #002b7f;
  font-family: 'Arial', sans-serif;
  font-weight: 700;
  font-size: 13px;
  letter-spacing: 1px;
  padding: 12px 32px;
  text-decoration: none;
  transition: background 0.2s;
}
.cta-banner .cta-btn:hover {
  background: #eef3fa;
}

/* ===== 页脚 ===== */
footer {
  width: 100%;
  background: #fff;
  border-top: 1px solid #d4d4d4;
  padding: 40px 40px 24px;
}
footer .footer-inner {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 32px;
  margin-bottom: 32px;
}
footer .footer-col h4 {
  font-family: 'Arial', sans-serif;
  font-size: 12px;
  font-weight: 700;
  color: #002b7f;
  letter-spacing: 1px;
  margin-bottom: 12px;
  text-transform: uppercase;
}
footer .footer-col a {
  display: block;
  font-family: 'Arial', sans-serif;
  font-size: 12px;
  color: #555;
  text-decoration: none;
  line-height: 2;
}
footer .footer-col a:hover {
  color: #002b7f;
  text-decoration: underline;
}
.footer-social {
  max-width: 1200px;
  margin: 0 auto;
  padding: 16px 0;
  border-top: 1px solid #eee;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 12px;
}
.footer-social .social-icons {
  display: flex;
  gap: 16px;
}
.footer-social .social-icons a {
  font-family: 'Arial', sans-serif;
  font-size: 12px;
  color: #555;
  text-decoration: none;
  letter-spacing: 0.5px;
}
.footer-social .social-icons a:hover { color: #002b7f; }
.footer-bottom {
  max-width: 1200px;
  margin: 0 auto;
  padding-top: 16px;
  border-top: 1px solid #eee;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 8px;
  font-family: 'Arial', sans-serif;
  font-size: 11px;
  color: #999;
}
.footer-bottom a {
  color: #999;
  text-decoration: none;
}
.footer-bottom a:hover { color: #002b7f; }
.footer-bottom .links { display: flex; gap: 16px; flex-wrap: wrap; }

/* ===== 响应式 ===== */
@media (max-width: 768px) {
  .nav { flex-direction: column; gap: 12px; padding: 12px 20px; }
  .nav-links { flex-wrap: wrap; justify-content: center; gap: 14px; font-size: 12px; }
  .nav-logo-text { font-size: 12px; }
  .nav-logo-text small { font-size: 8px; }
  .nav-search { display: none; }
  main { padding: 24px 16px; }
  .about-lead h1 { font-size: 28px; }
  .about-lead p { font-size: 16px; }
  .grid-2col { grid-template-columns: 1fr; gap: 24px; }
  .grid-2col h2 { font-size: 20px; }
  .hero-quote { padding: 24px 20px; margin: 0 0 32px; }
  .hero-quote p { font-size: 18px; }
  .explore-grid { grid-template-columns: 1fr 1fr; }
  .access-card { padding: 24px 16px; margin: 0 0 32px; }
  .access-card h2 { font-size: 15px; }
  .access-card .input-row { flex-direction: column; gap: 8px; }
  .access-card .legal-warning { font-size: 9px; padding: 8px 10px; }
  .access-card .card-warning { font-size: 10px; padding: 10px 0; }
  .access-card .toggle-pwd { font-size: 20px; right: 12px; }
  footer .footer-inner { grid-template-columns: 1fr 1fr; gap: 20px; }
  footer { padding: 28px 20px 16px; }
  .cta-banner { padding: 28px 20px; margin: 0 0 32px; }
  .cta-banner h2 { font-size: 20px; }
  .cta-banner p { font-size: 13px; }
  .video-container { margin: 0 16px 32px; }
}
@media (max-width: 480px) {
  .top-bar { padding: 6px 16px; gap: 12px; font-size: 10px; flex-wrap: wrap; justify-content: center; }
  .nav-links { gap: 10px; font-size: 11px; }
  .nav-links a { white-space: nowrap; }
  .about-lead h1 { font-size: 22px; }
  .about-lead p { font-size: 14px; }
  .about-lead .seal-row { flex-wrap: wrap; gap: 10px; }
  .about-lead .seal-row .signature { font-size: 10px; text-align: center; }
  .hero-quote p { font-size: 16px; }
  .grid-2col h2 { font-size: 18px; }
  .grid-2col p, .grid-2col ul li { font-size: 13px; }
  .explore-grid { grid-template-columns: 1fr; gap: 10px; }
  .explore-card { padding: 20px 12px; }
  .access-card { padding: 20px 12px; }
  .access-card h2 { font-size: 13px; letter-spacing: 1px; }
  .access-card .card-sub { font-size: 8px; }
  .access-card .watermark { font-size: 24px; }
  .access-card .input-row { flex-direction: column; gap: 8px; }
  .access-card .input-wrapper input { font-size: 14px; padding: 8px 38px 8px 10px; letter-spacing: 2px; }
  .access-card .toggle-pwd { font-size: 18px; right: 10px; }
  .access-card button { padding: 10px 20px; font-size: 12px; width: 100%; }
  .footer-social { flex-direction: column; text-align: center; }
  .footer-social .social-icons { flex-wrap: wrap; justify-content: center; gap: 10px; }
  .footer-bottom { flex-direction: column; text-align: center; }
  .footer-bottom .links { justify-content: center; }
  .cta-banner h2 { font-size: 17px; }
  .cta-banner p { font-size: 12px; }
  .cta-banner .cta-btn { padding: 10px 20px; font-size: 12px; }
  .video-inner { padding: 12px; }
  .video-title { font-size: 14px; }
}
</style>