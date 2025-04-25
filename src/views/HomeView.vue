<template>
  <div class="home">
    <header class="header">
      <nav class="nav">
        <router-link to="/" class="logo">Gishai</router-link>
        <div class="nav-links">
          <router-link to="/home" class="nav-link" active-class="active-link">首页</router-link>
          <router-link to="/about" class="nav-link" active-class="active-link">关于</router-link>
          <router-link to="/projects" class="nav-link" active-class="active-link">项目</router-link>
          <router-link to="/contact" class="nav-link" active-class="active-link">联系</router-link>
        </div>
      </nav>
    </header>
    
    <main class="main-content">
      <h1 class="fade-in">欢迎来到Gishai</h1>
      <p class="fade-in delay-1">这里将展示网站的主要内容</p>
      
      <div class="cards-container fade-in delay-2">
        <div class="card">
          <h3>项目展示</h3>
          <p>浏览我的最新作品和项目案例</p>
        </div>
        <div class="card">
          <h3>技术分享</h3>
          <p>阅读我的技术博客和学习笔记</p>
        </div>
        <div class="card">
          <h3>关于我</h3>
          <p>了解我的背景和专业技能</p>
        </div>
      </div>
    </main>
    
    <footer class="footer fade-in delay-3">
      <p>© 2023 Gishai. All rights reserved.</p>
    </footer>
  </div>
</template>

<script setup>
import { onMounted } from 'vue';

onMounted(() => {
  // 平滑滚动效果
  document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function(e) {
      e.preventDefault();
      document.querySelector(this.getAttribute('href')).scrollIntoView({
        behavior: 'smooth'
      });
    });
  });
});
</script>

<style scoped>
.home {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.header {
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 1rem 2rem;
}

.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
  color: #333;
  text-decoration: none;
}

.nav-links {
  display: flex;
  gap: 2rem;
}

.nav-link {
  color: #333;
  text-decoration: none;
  transition: all 0.3s;
  padding: 0.5rem 1rem;
  border-radius: 4px;
}

.nav-link:hover {
  color: #0066cc;
  background-color: rgba(0, 102, 204, 0.1);
}

.active-link {
  color: #0066cc;
  font-weight: bold;
  border-bottom: 2px solid #0066cc;
}

.main-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 2rem;
  text-align: center;
}

.fade-in {
  opacity: 0;
  animation: fadeIn 1s ease-in forwards;
}

.delay-1 {
  animation-delay: 0.5s;
}

.delay-2 {
  animation-delay: 1s;
}

.delay-3 {
  animation-delay: 1.5s;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* 平滑滚动样式 */
html {
  scroll-behavior: smooth;
}

@media (max-width: 768px) {
  .nav {
    flex-direction: column;
    gap: 1rem;
  }
  
  .nav-links {
    flex-direction: column;
    gap: 1rem;
  }
  
  .cards-container {
    flex-direction: column;
  }
}
.cards-container {
  display: flex;
  justify-content: center;
  gap: 2rem;
  margin-top: 3rem;
  flex-wrap: wrap;
}

.card {
  background: white;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  padding: 1.5rem;
  width: 280px;
  transition: transform 0.3s, box-shadow 0.3s;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
}

.footer {
  text-align: center;
  padding: 2rem;
  background-color: #f8f9fa;
  margin-top: auto;
}
</style>