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
      
      <!-- 工具区域 -->
      <div class="section-title scroll-animation">
        <h2>实用工具</h2>
        <div class="underline"></div>
      </div>
      
      <div class="cards-container scroll-animation">
        <div class="card tool-card">
          <div class="card-icon">🔍</div>
          <h3>GIS数据查询</h3>
          <p>快速查询和检索地理信息系统数据，支持多种格式和坐标系</p>
          <button class="card-btn">立即使用</button>
        </div>
        
        <div class="card tool-card">
          <div class="card-icon">🗺️</div>
          <h3>地图可视化</h3>
          <p>将复杂的地理数据转化为直观的可视化地图，支持自定义样式</p>
          <button class="card-btn">立即使用</button>
        </div>
        
        <div class="card tool-card">
          <div class="card-icon">📊</div>
          <h3>空间分析</h3>
          <p>强大的空间分析工具，支持缓冲区分析、叠加分析和网络分析</p>
          <button class="card-btn">立即使用</button>
        </div>
        
        <div class="card tool-card">
          <div class="card-icon">📱</div>
          <h3>移动端采集</h3>
          <p>便捷的移动端数据采集工具，支持离线采集和实时同步</p>
          <button class="card-btn">立即使用</button>
        </div>
      </div>
    </main>
    
    <footer class="footer fade-in delay-3">
      <p>© 2023 Gishai. All rights reserved.</p>
    </footer>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';

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
  
  // 滚动动画效果
  const scrollAnimations = document.querySelectorAll('.scroll-animation');
  
  const checkScroll = () => {
    scrollAnimations.forEach(element => {
      const elementTop = element.getBoundingClientRect().top;
      const windowHeight = window.innerHeight;
      
      if (elementTop < windowHeight * 0.8) {
        element.classList.add('active');
      }
    });
  };
  
  // 初始检查
  checkScroll();
  
  // 滚动时检查
  window.addEventListener('scroll', checkScroll);
});
</script>

<style scoped>
.home {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

:root {
  --primary-color: #0066cc;
  --secondary-color: #004d99;
  --text-color: #333;
  --card-background: white;
  --shadow-color: rgba(0, 0, 0, 0.1);
  --animation-duration: 1s;
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
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
}

.tool-card {
  background: var(--card-background, white);
  border-radius: 12px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
  padding: 2rem;
  transition: transform 0.5s, box-shadow 0.5s;
}

.tool-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
}

.card-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
  color: var(--primary-color, #0066cc);
}

.card-btn {
  background-color: var(--primary-color, #0066cc);
  color: white;
  border: none;
  padding: 0.6rem 1.2rem;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
  transition: background-color 0.3s, transform 0.3s;
  margin-top: auto;
}

.card-btn:hover {
  background-color: var(--secondary-color, #004d99);
  transform: scale(1.05);
}

.footer {
  text-align: center;
  padding: 2rem;
  background-color: #f8f9fa;
  margin-top: auto;
}
</style>