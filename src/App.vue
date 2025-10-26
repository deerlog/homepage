<script setup>
const skillGroups = [
  {
    title: '前端开发',
    items: ['Vue 3 / Vue Router / Pinia', 'TypeScript & JavaScript (ES2023)', 'HTML5 & CSS3 / TailwindCSS', '响应式设计与可访问性']
  },
  {
    title: '全栈与工程化',
    items: ['Node.js & Express', 'RESTful API 设计', 'Vite / Webpack / CI 自动化', 'Docker & 简单部署']
  },
  {
    title: '设计与体验',
    items: ['交互设计思维', 'Figma 原型设计', '动效与动画', '微交互优化']
  }
]

const projectHighlights = [
  {
    name: '个人知识空间',
    description: '使用 Vue 3 + Vite 打造的轻量笔记平台，支持 Markdown 编辑、标签分类与渐进式增强体验。',
    link: '#'
  },
  {
    name: '数字作品集',
    description: '整合设计与开发案例的可视化网站，采用毛玻璃与玻璃拟态风格，加强沉浸感。',
    link: '#'
  },
  {
    name: '旅行随记',
    description: '结合地图与游记的分享页面，支持暗色主题与多语言切换，为个人兴趣项目。',
    link: '#'
  }
]

const contactLinks = [
  { label: 'Email', value: 'hello@example.com', href: 'mailto:hello@example.com' },
  { label: 'GitHub', value: '@yourgithub', href: 'https://github.com/yourgithub' },
  { label: '知乎', value: '@你的知乎', href: 'https://www.zhihu.com' }
]

const currentYear = new Date().getFullYear()
</script>

<template>
  <div class="page">
    <header class="hero" id="top">
      <div class="hero__mask"></div>
      <nav class="nav">
        <div class="nav__brand">Ming.</div>
        <div class="nav__links">
          <a href="#about">关于我</a>
          <a href="#skills">技能栈</a>
          <a href="#projects">项目</a>
          <a href="#contact">联系</a>
        </div>
      </nav>

      <div class="hero__content glass-panel">
        <span class="hero__tag">前端工程师 / 设计爱好者</span>
        <h1>你好，我是明。</h1>
        <p>
          热爱打造精致的用户体验，将技术与设计融合，专注于 Vue 生态与现代 Web 技术。
          未来计划为个人项目扩展后台管理能力。
        </p>
        <div class="hero__actions">
          <a class="btn btn--primary" href="#projects">查看项目</a>
          <a class="btn" href="#contact">联系我</a>
        </div>
      </div>
    </header>

    <main class="content">
      <section id="about" class="section section--about">
        <div class="section__inner glass-panel">
          <div class="section__title">
            <span>ABOUT</span>
            <h2>关于我</h2>
          </div>
          <div class="section__body">
            <p>
              我喜欢研究前沿的 Web 技术与设计趋势，探索极简但富有表现力的界面方案。平时会记录学习心得，维护个人知识库，并尝试把想法快速落地。
            </p>
            <p>
              近期专注在 Vue 3 生态、前端工程化以及视觉表达的结合，希望能够通过产品表达热爱，也期待未来扩展为更完整的个人系统。
            </p>
          </div>
        </div>
      </section>

      <section id="skills" class="section">
        <div class="section__inner">
          <div class="section__title section__title--center">
            <span>SKILLS</span>
            <h2>核心技能栈</h2>
          </div>
          <div class="grid">
            <article v-for="group in skillGroups" :key="group.title" class="glass-card">
              <h3>{{ group.title }}</h3>
              <ul>
                <li v-for="item in group.items" :key="item">{{ item }}</li>
              </ul>
            </article>
          </div>
        </div>
      </section>

      <section id="projects" class="section">
        <div class="section__inner">
          <div class="section__title section__title--center">
            <span>PROJECTS</span>
            <h2>个人项目精选</h2>
          </div>
          <div class="grid grid--projects">
            <article v-for="project in projectHighlights" :key="project.name" class="glass-card glass-card--project">
              <div class="project__header">
                <h3>{{ project.name }}</h3>
              </div>
              <p>{{ project.description }}</p>
              <a v-if="project.link !== '#'" class="project__link" :href="project.link" target="_blank" rel="noopener noreferrer">
                访问项目
              </a>
            </article>
          </div>
        </div>
      </section>

      <section id="contact" class="section section--contact">
        <div class="section__inner glass-panel">
          <div class="section__title">
            <span>CONTACT</span>
            <h2>与我联系</h2>
          </div>
          <div class="contact__grid">
            <div class="contact__info">
              <p>
                如果你对我的作品或想法感兴趣，欢迎随时留言交流。未来我也会在此基础上加入轻量后台管理，让记录与更新更加便捷。
              </p>
              <div class="contact__links">
                <a v-for="link in contactLinks" :key="link.label" :href="link.href" target="_blank" rel="noopener noreferrer">
                  <span>{{ link.label }}</span>
                  <strong>{{ link.value }}</strong>
                </a>
              </div>
            </div>
            <form class="contact__form" @submit.prevent>
              <label>
                姓名
                <input type="text" name="name" placeholder="你的称呼" />
              </label>
              <label>
                邮箱
                <input type="email" name="email" placeholder="example@email.com" />
              </label>
              <label>
                留言
                <textarea name="message" rows="4" placeholder="想聊点什么？"></textarea>
              </label>
              <button type="submit" class="btn btn--primary" disabled>发送（即将开放）</button>
            </form>
          </div>
        </div>
      </section>
    </main>

    <footer class="footer">
      <div class="footer__inner glass-panel">
        <span>© {{ currentYear }} Ming · Personal Space</span>
        <a href="#top">回到顶部 ↑</a>
      </div>
    </footer>
  </div>
</template>

<style scoped>
.page {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  color: rgba(255, 255, 255, 0.88);
  backdrop-filter: blur(0px);
}

.hero {
  position: relative;
  min-height: 85vh;
  padding: 3rem clamp(1.5rem, 4vw, 5rem) 8rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  overflow: hidden;
}

.hero::before,
.hero::after {
  content: '';
  position: absolute;
  width: 320px;
  height: 320px;
  border-radius: 50%;
  filter: blur(60px);
  opacity: 0.4;
  z-index: 0;
}

.hero::before {
  top: -120px;
  right: -80px;
  background: radial-gradient(circle at 30% 30%, rgba(255, 255, 255, 0.6), transparent 70%);
}

.hero::after {
  bottom: -140px;
  left: -60px;
  background: radial-gradient(circle at 70% 70%, rgba(255, 255, 255, 0.45), transparent 70%);
}

.hero__mask {
  position: absolute;
  inset: 0;
  background: rgba(20, 24, 44, 0.2);
  backdrop-filter: blur(20px);
  z-index: 1;
}

.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
  z-index: 2;
}

.nav__brand {
  font-size: 1.5rem;
  font-weight: 600;
  letter-spacing: 0.1rem;
}

.nav__links {
  display: flex;
  gap: 1.5rem;
  font-size: 0.95rem;
}

.nav__links a {
  position: relative;
  padding-bottom: 0.25rem;
}

.nav__links a::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 2px;
  background: rgba(255, 255, 255, 0.6);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.3s ease;
}

.nav__links a:hover::after {
  transform: scaleX(1);
}

.hero__content {
  position: relative;
  z-index: 2;
  max-width: min(680px, 100%);
  padding: clamp(2rem, 5vw, 3.5rem);
  border-radius: 24px;
  background: rgba(18, 24, 50, 0.25);
  border: 1px solid rgba(255, 255, 255, 0.25);
  box-shadow: 0 25px 60px -20px rgba(2, 8, 20, 0.65);
}

.hero__content::before {
  content: '';
  position: absolute;
  inset: 1px;
  border-radius: 23px;
  background: linear-gradient(120deg, rgba(255, 255, 255, 0.08), rgba(255, 255, 255, 0.02));
  pointer-events: none;
}

.hero__tag {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  padding: 0.35rem 0.75rem;
  margin-bottom: 1.5rem;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.12);
  font-size: 0.85rem;
  letter-spacing: 0.08rem;
}

.hero__tag::before {
  content: '';
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: #87f1ff;
  box-shadow: 0 0 12px rgba(135, 241, 255, 0.8);
}

.hero h1 {
  font-size: clamp(2.5rem, 6vw, 4rem);
  margin-bottom: 1rem;
}

.hero p {
  font-size: 1.05rem;
  color: rgba(255, 255, 255, 0.78);
  margin-bottom: 2rem;
}

.hero__actions {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.75rem 1.8rem;
  border-radius: 999px;
  font-weight: 500;
  border: 1px solid rgba(255, 255, 255, 0.35);
  color: rgba(255, 255, 255, 0.9);
  background: rgba(255, 255, 255, 0.08);
  transition: transform 0.3s ease, background 0.3s ease, border 0.3s ease;
}

.btn:hover {
  transform: translateY(-2px);
  background: rgba(255, 255, 255, 0.16);
  border-color: rgba(255, 255, 255, 0.45);
}

.btn--primary {
  background: linear-gradient(135deg, rgba(135, 241, 255, 0.7), rgba(148, 187, 233, 0.7));
  border: 1px solid rgba(200, 246, 255, 0.65);
  color: rgba(10, 23, 44, 0.95);
  backdrop-filter: blur(12px);
  box-shadow: 0 12px 30px -15px rgba(135, 241, 255, 0.9);
}

.btn--primary:hover {
  background: linear-gradient(135deg, rgba(135, 241, 255, 0.85), rgba(148, 187, 233, 0.9));
}

.content {
  flex: 1;
  padding: clamp(3rem, 6vw, 6rem) clamp(1.5rem, 4vw, 4.5rem) clamp(4rem, 6vw, 6rem);
}

.section {
  margin-bottom: clamp(4rem, 7vw, 6rem);
}

.section--about {
  margin-top: -6rem;
}

.section__inner {
  position: relative;
  max-width: 1100px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.glass-panel {
  position: relative;
  backdrop-filter: blur(18px);
}

.section__inner.glass-panel {
  padding: clamp(2.5rem, 5vw, 3.5rem);
  border-radius: 28px;
  background: rgba(12, 18, 40, 0.35);
  border: 1px solid rgba(255, 255, 255, 0.2);
  box-shadow: 0 20px 60px -30px rgba(2, 8, 20, 0.75);
}

.section__inner.glass-panel::before {
  content: '';
  position: absolute;
  inset: 1px;
  border-radius: 27px;
  background: linear-gradient(120deg, rgba(255, 255, 255, 0.08), rgba(255, 255, 255, 0.015));
  pointer-events: none;
}

.section__title span {
  font-size: 0.85rem;
  letter-spacing: 0.4rem;
  opacity: 0.7;
}

.section__title h2 {
  font-size: clamp(1.8rem, 4vw, 2.5rem);
  margin-top: 0.8rem;
}

.section__title--center {
  text-align: center;
  margin-bottom: 2.5rem;
}

.section__body {
  display: grid;
  gap: 1.25rem;
  font-size: 1.05rem;
  color: rgba(255, 255, 255, 0.8);
}

.grid {
  display: grid;
  gap: clamp(1.5rem, 3vw, 2.5rem);
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
}

.glass-card {
  position: relative;
  padding: clamp(1.8rem, 4vw, 2.5rem);
  border-radius: 26px;
  background: rgba(18, 24, 50, 0.25);
  border: 1px solid rgba(255, 255, 255, 0.22);
  backdrop-filter: blur(18px);
  box-shadow: 0 20px 50px -30px rgba(5, 10, 30, 0.75);
  transition: transform 0.3s ease, border 0.3s ease, box-shadow 0.3s ease;
}

.glass-card::before {
  content: '';
  position: absolute;
  inset: 1px;
  border-radius: 25px;
  background: linear-gradient(160deg, rgba(255, 255, 255, 0.08), rgba(255, 255, 255, 0.02));
  pointer-events: none;
}

.glass-card:hover {
  transform: translateY(-6px);
  border-color: rgba(255, 255, 255, 0.35);
  box-shadow: 0 30px 60px -35px rgba(5, 10, 30, 0.8);
}

.glass-card h3 {
  font-size: 1.3rem;
  margin-bottom: 1.2rem;
}

.glass-card ul {
  list-style: none;
  display: grid;
  gap: 0.75rem;
  color: rgba(255, 255, 255, 0.75);
}

.glass-card li {
  display: flex;
  gap: 0.6rem;
}

.glass-card li::before {
  content: '•';
  color: rgba(135, 241, 255, 0.9);
}

.grid--projects {
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
}

.glass-card--project {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.project__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.project__header h3 {
  font-size: 1.35rem;
}

.project__link {
  align-self: flex-start;
  padding: 0.55rem 1.4rem;
  border-radius: 999px;
  background: rgba(135, 241, 255, 0.15);
  border: 1px solid rgba(135, 241, 255, 0.45);
  color: rgba(255, 255, 255, 0.85);
  font-size: 0.9rem;
  transition: transform 0.3s ease, background 0.3s ease;
}

.project__link:hover {
  transform: translateY(-2px);
  background: rgba(135, 241, 255, 0.25);
}

.section--contact .section__inner {
  gap: clamp(2rem, 5vw, 3rem);
}

.contact__grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: clamp(2rem, 4vw, 3rem);
}

.contact__info {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  color: rgba(255, 255, 255, 0.82);
}

.contact__links {
  display: grid;
  gap: 0.9rem;
}

.contact__links a {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.85rem 1rem;
  border-radius: 18px;
  background: rgba(135, 241, 255, 0.12);
  border: 1px solid rgba(135, 241, 255, 0.35);
  color: rgba(255, 255, 255, 0.88);
}

.contact__links span {
  font-size: 0.9rem;
  letter-spacing: 0.1rem;
}

.contact__links strong {
  font-size: 1rem;
}

.contact__form {
  display: grid;
  gap: 1.2rem;
}

.contact__form label {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  font-size: 0.95rem;
  color: rgba(255, 255, 255, 0.78);
}

.contact__form input,
.contact__form textarea {
  padding: 0.75rem 1rem;
  border-radius: 18px;
  border: 1px solid rgba(255, 255, 255, 0.25);
  background: rgba(12, 18, 40, 0.45);
  color: rgba(255, 255, 255, 0.92);
  font: inherit;
  resize: vertical;
  transition: border 0.3s ease, background 0.3s ease;
}

.contact__form input:focus,
.contact__form textarea:focus {
  outline: none;
  border-color: rgba(135, 241, 255, 0.6);
  background: rgba(12, 18, 40, 0.65);
}

.footer {
  padding: 2rem clamp(1.5rem, 4vw, 3rem) 3rem;
}

.footer__inner {
  max-width: 1100px;
  margin: 0 auto;
  padding: 1.4rem 2rem;
  border-radius: 20px;
  background: rgba(10, 16, 32, 0.35);
  border: 1px solid rgba(255, 255, 255, 0.18);
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 0.9rem;
}

.footer__inner a {
  font-weight: 500;
}

@media (max-width: 960px) {
  .hero {
    padding: 2.5rem clamp(1.25rem, 5vw, 3rem) 7rem;
  }

  .nav__links {
    display: none;
  }

  .hero__content {
    padding: clamp(2rem, 7vw, 3rem);
  }

  .section--about {
    margin-top: -4rem;
  }
}

@media (max-width: 680px) {
  .content {
    padding: 3.5rem 1.25rem 4.5rem;
  }

  .section__inner.glass-panel {
    padding: 2rem 1.5rem;
  }

  .glass-card {
    padding: 1.8rem 1.5rem;
  }

  .footer__inner {
    flex-direction: column;
    gap: 0.8rem;
    text-align: center;
  }
}
</style>
