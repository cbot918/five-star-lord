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
      <div class="top-section">
        <div class="character-preview">
          <img src="@/assets/pics/knight.png" alt="Knight" class="knight-img" />
        </div>

        <div class="stats-container">
          <div class="stat-item">血量: <span class="val">100/100</span></div>
          <div class="stat-item">爆發力: <span class="val">50</span></div>
          <div class="stat-item">戰鬥熟練度: <span class="val">Lv.5</span></div>
          <div class="stat-item">戰鬥經驗值: <span class="val">80%</span></div>
        </div>

        <div class="upgrade-btn-small">晉升</div>
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
  padding: 15px;
  display: flex;
  flex-direction: column;
}

/* --- 上半部角色與數值資訊 (新配置) --- */
.top-section {
  display: flex;
  align-items: center; /* 垂直置中 */
  gap: 12px;
  margin-bottom: 20px;
  background: rgba(255, 255, 255, 0.05);
  padding: 12px;
  border-radius: 12px;
  border: 1px solid rgba(184, 134, 11, 0.3);
}

.character-preview {
  flex: 0 0 25%; /* 佔比 1/4 */
}

.knight-img {
  width: 100%;
  aspect-ratio: 1 / 1; /* 強制正方形 */
  object-fit: cover;
  border-radius: 8px;
  border: 1px solid #444;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
}

.stats-container {
  flex: 1; /* 佔據剩餘空間 */
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.stat-item {
  font-size: 13px;
  color: #999;
  white-space: nowrap;
}

.stat-item .val {
  color: #eee;
  font-weight: bold;
  margin-left: 4px;
}

/* --- 小型正方形晉升按鈕 --- */
.upgrade-btn-small {
  width: 55px;
  height: 55px;
  min-width: 55px;
  background: linear-gradient(180deg, #b8860b 0%, #8b6508 100%);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
  font-size: 14px;
  font-weight: bold;
  cursor: pointer;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.4);
  border: 1px solid #d4af37;
}

.upgrade-btn-small:active {
  transform: scale(0.95);
  filter: brightness(0.8);
}

/* --- 區塊共通樣式 --- */
.section-container {
  width: 100%;
  margin-bottom: 15px;
  background: rgba(255, 255, 255, 0.05);
  padding: 15px;
  border-radius: 10px;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.section-title {
  text-align: center;
  width: 100%;
  font-size: 1rem;
  font-weight: bold;
  margin-bottom: 12px;
  color: #cfccbd;
  letter-spacing: 2px;
  text-shadow: 1px 1px 2px black;
}

.content-text {
  width: 100%;
}

/* --- 敵人列表 --- */
.enemy-list {
  display: flex;
  gap: 12px;
  overflow-x: auto;
  padding-bottom: 8px;
}

.enemy-img {
  width: 60px;
  height: 60px;
  object-fit: cover;
  border: 2px solid #555;
  border-radius: 8px;
  background: #000;
  flex-shrink: 0;
}

/* --- 網格佈局 --- */
.grid-layout {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

.grid-item {
  background: #2a2a2a;
  border: 1px solid #444;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
  color: #888;
  border-radius: 6px;
  cursor: pointer;
  transition: all 0.2s;
}

.grid-item.active {
  border-color: #ff4500;
  color: #eee;
  background: #332211;
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
}

/* --- 捲軸與桌機適配 --- */
.enemy-list::-webkit-scrollbar {
  height: 4px;
}
.enemy-list::-webkit-scrollbar-thumb {
  background: #444;
  border-radius: 10px;
}

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
