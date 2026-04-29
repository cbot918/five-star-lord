<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>
<template>
  <div class="app-container">
    <div class="header">
      <span class="job">戰士</span>
      <span class="username">Yale</span>
    </div>

    <div class="body">
      <div class="character-preview">
        <img src="@/assets/pics/knight.png" alt="Knight" class="knight-img" />
      </div>

      <div class="content-text">
        <div class="section-container">
          <div class="section-title">敵人</div>
          <div class="enemy-list">
            <img src="@/assets/pics/sheep2.png" alt="Cute Sheep" class="enemy-img" />
            <img src="@/assets/pics/cat_fighter.png" alt="Cat Fighter" class="enemy-img" />
            <img src="@/assets/pics/assassin.png" alt="Assassin" class="enemy-img" />
            <img src="@/assets/pics/void_dragon.png" alt="Boss Void Dragon" class="enemy-img" />
          </div>
        </div>

        <div class="section-container">
          <div class="section-title">裝備</div>
          <div class="grid-layout">
            <div class="grid-item active">武器</div>
            <div class="grid-item">頭盔</div>
            <div class="grid-item">裝甲</div>
            <div class="grid-item">鞋子</div>
          </div>
        </div>

        <div class="section-container">
          <div class="section-title">背包</div>
          <div class="grid-layout">
            <div class="grid-item">格子1</div>
            <div class="grid-item">格子2</div>
            <div class="grid-item">格子3</div>
            <div class="grid-item">格子4</div>
          </div>
        </div>

        <div class="upgrade-btn">晉升</div>
      </div>
    </div>

    <nav class="navbar">
      <div class="nav-item">人物</div>
      <div class="nav-item">軍營</div>
      <div class="nav-item">街道</div>
      <div class="nav-item">寵物</div>
    </nav>
  </div>
</template>

<style scoped>
/* --- 基礎佈局 --- */
.app-container {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  margin: 0 auto;
  background-color: #1a1a1a;
  color: white;
  overflow: hidden;
  font-family: sans-serif;
}

.header {
  padding: 15px;
  background: #333;
  display: flex;
  justify-content: space-between;
  border-bottom: 2px solid #b8860b;
}

.job {
  color: #ff4500;
  font-weight: bold;
}

.body {
  flex: 1;
  overflow-y: auto;
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

/* --- 角色圖片 --- */
.character-preview {
  width: 100%;
  max-width: 260px;
  margin-bottom: 25px;
}

.knight-img {
  width: 100%;
  height: auto;
  border-radius: 12px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.6);
  border: 1px solid #444;
}

/* --- 區塊共通樣式 (敵人/裝備/背包) --- */
.section-container {
  width: 100%;
  margin-bottom: 20px;
  background: rgba(255, 255, 255, 0.05);
  padding: 15px;
  border-radius: 10px;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.section-title {
  text-align: center;
  width: 100%;
  font-size: 1.1rem;
  font-weight: bold;
  margin-bottom: 15px;
  color: #cfccbd;
  letter-spacing: 3px;
  text-shadow: 1px 1px 2px black;
}

.content-text {
  width: 100%;
}

/* --- 敵人列表 (Flex) --- */
.enemy-list {
  display: flex;
  gap: 12px;
  overflow-x: auto;
  padding-bottom: 8px;
}

.enemy-img {
  width: 65px;
  height: 65px;
  object-fit: cover;
  border: 2px solid #555;
  border-radius: 8px;
  background: #000;
  flex-shrink: 0;
}

/* --- 裝備與背包網格 (Grid) --- */
.grid-layout {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

.grid-item {
  background: #2a2a2a;
  border: 1px solid #444;
  height: 65px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  color: #999;
  border-radius: 6px;
  cursor: pointer;
  transition: all 0.2s;
}

.grid-item:hover {
  border-color: #b8860b;
  background: #333;
  color: #fff;
}

/* 若格子內有裝備的樣式例 */
.grid-item.active {
  border-color: #ff4500;
  color: #eee;
}

/* --- 晉升按鈕 --- */
.upgrade-btn {
  width: 100%;
  padding: 15px;
  background: linear-gradient(180deg, #b8860b 0%, #8b6508 100%);
  color: white;
  text-align: center;
  border-radius: 8px;
  font-weight: bold;
  margin: 10px 0 30px 0;
  cursor: pointer;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
}

.upgrade-btn:active {
  transform: translateY(2px);
  filter: brightness(0.9);
}

/* --- 底部導覽 --- */
.navbar {
  display: flex;
  justify-content: space-around;
  align-items: center;
  height: 65px;
  background: #222;
  border-top: 2px solid #444;
  padding-bottom: env(safe-area-inset-bottom);
}

.nav-item {
  flex: 1;
  text-align: center;
  font-size: 15px;
  font-weight: 500;
  color: #888;
  cursor: pointer;
}

.nav-item:hover {
  color: #b8860b;
}

/* --- 捲軸美化 --- */
.enemy-list::-webkit-scrollbar {
  height: 4px;
}
.enemy-list::-webkit-scrollbar-thumb {
  background: #444;
  border-radius: 10px;
}

/* --- 桌機版適配 --- */
@media (min-width: 768px) {
  .app-container {
    max-width: 450px;
    height: 92vh;
    margin: 4vh auto;
    border-radius: 24px;
    border: 6px solid #333;
    box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
  }
}
</style>

<!-- 
<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style> -->
