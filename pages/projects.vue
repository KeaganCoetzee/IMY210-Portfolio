<template>
  
  <main class="projects-section">
    <br><br><br>
    
    <div class="system-path-header">
      <div class="path-bar">
        <span class="path-text">C:\USERS\KEAGAN\DOCUMENTS\SELECTED_WORK.SYS</span>
        <div class="window-controls">
          <span>_</span><span>□</span><span>×</span>
        </div>
      </div>
      <div class="title-area">
        <h1 class="main-title">PORTFOLIO</h1>
        <div class="subtitle-tag">VERSION 2.0.26</div>
      </div>
    </div>

    <div class="projects-grid">
      <div class="project-card">
        <div class="card-header">
          <span class="header-dot">●</span>
          <span class="header-title">ASSIGNMENT_01.EXE</span>
        </div>
        <div class="card-image-placeholder">
          <img src="/folderIcon.png" alt="Folder Icon" class="project-icon">
        </div>
        <div class="card-content">
          <h3>ListNode Practical</h3>
          <p>A technical assessment focusing on data structures and backend logic for the University of Pretoria.</p>
          <div class="tag-row">
            <span class="mini-pill hover-yellow">JAVASCRIPT</span>
            <span class="mini-pill hover-yellow">DATA_STRUCTURES</span>
          </div>
          <a href="/ListNode.zip" download="Keagan_ListNode_Prac.zip" class="btn-card">DOWNLOAD .ZIP</a>
        </div>
      </div>

      <div class="project-card">
        <div class="card-header dark">
          <span class="header-dot">●</span>
          <span class="header-title">PROJECT_RED.SYS</span>
        </div>
        <div class="card-image-placeholder">
          <img src="/hatIcon.png" alt="Hat Icon" class="project-icon">
        </div>
        <div class="card-content">
          <h3>Red Dead Website</h3>
          <p>A themed web project developed to showcase advanced CSS and interactive design principles.</p>
          <div class="tag-row">
            <span class="mini-pill hover-blue">HTML5</span>
            <span class="mini-pill hover-blue">CSS_GRID</span>
            <span class="mini-pill hover-blue">THEMING</span>
          </div>
          <a href="/Red_Dead_Website.zip" download="Keagan_RedDead_Project.zip" class="btn-card">DOWNLOAD .ZIP</a>
        </div>
      </div>

      <div class="project-card">
        <div class="card-header">
          <span class="header-dot">●</span>
          <span class="header-title">WEB_DEV.EXE</span>
        </div>
        <div class="card-image-placeholder">
          <img src="/webIcon.png" alt="Web Icon" class="project-icon">
        </div>
        <div class="card-content">
          <h3>Terminal To-Do</h3>
          <p>Mastering modern web architecture and state management within the Multimedia degree at UP.</p>
          <div class="tag-row">
            <span class="mini-pill hover-pink">VUE_JS</span>
            <span class="mini-pill hover-pink">VITE</span>
            <span class="mini-pill hover-pink">PINIA</span>
          </div>
          <a href="/To-do-terminal.zip" download="Keagan_Todo_App.zip" class="btn-card">DOWNLOAD .ZIP</a>
        </div>
      </div>
    </div>

    <div class="back-home">
      <NuxtLink to="/" class="btn-back">← RETURN TO TERMINAL</NuxtLink>
    </div>
  </main>
</template>

<style scoped>
/*Keagan Coetzee u25122003*/
  
@import url('https://fonts.googleapis.com/css2?family=Alfa+Slab+One&family=Roboto:wght@400;900&display=swap');

  
.projects-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 60px 20px;
  min-height: 100vh;
}

.system-path-header {
  width: 100%;
  max-width: 1300px;
  border: 4px solid black;
  background: white;
  margin-bottom: 60px;
  box-shadow: 12px 12px 0px black;
}

.path-bar {
  background: black;
  color: white;
  padding: 10px 20px;
  display: flex;
  justify-content: space-between;
  font-family: 'Courier New', monospace;
  font-size: 0.9rem;
  font-weight: bold;
}

.window-controls span {
  margin-left: 15px;
  cursor: pointer;
}

.title-area {
  padding: 40px;
  text-align: left;
  background: #ffff00;
  border-top: 4px solid black;
}

.main-title {
  font-family: 'Alfa Slab One', serif;
  font-size: 5rem;
  margin: 0;
  color: black;
  line-height: 1;
}

.subtitle-tag {
  font-family: 'Courier New', monospace;
  font-weight: 900;
  background: black;
  color: white;
  display: inline-block;
  padding: 5px 15px;
  margin-top: 15px;
  font-size: 1.2rem;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(380px, 1fr));
  gap: 40px;
  width: 100%;
  max-width: 1300px;
  margin-bottom: 60px;
}

.project-card {
  background: white;
  border: 4px solid black;
  box-shadow: 10px 10px 0px black;
  transition: all 0.2s ease;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.project-card:hover {
  transform: translate(-5px, -5px);
  box-shadow: 15px 15px 0px black;
}

.card-header {
  background: #eee;
  border-bottom: 4px solid black;
  padding: 8px 15px;
  display: flex;
  align-items: center;
  gap: 8px;
}

.card-header.dark {
  background: #333;
  color: white;
}

.header-dot { 
  color: #ff0055; 
  font-size: 1.2rem; 
}

.header-title { 
  font-family: monospace; 
  font-weight: bold; 
  font-size: 0.8rem; 
}

.card-image-placeholder {
  height: 200px;
  background: white;
  display: flex;
  align-items: center;
  justify-content: center;
  border-bottom: 4px solid black;
}

.project-icon {
  max-width: 120px;
  height: auto;
}

.card-content {
  padding: 25px;
  text-align: left;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.card-content h3 {
  font-family: 'Alfa Slab One', serif;
  margin: 0 0 10px 0;
}

.tag-row {
  margin: 20px 0;
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  flex-grow: 1;
}

.mini-pill {
  border: 2px solid black;
  padding: 5px 10px;
  font-size: 0.8rem;
  font-weight: bold;
}

.hover-yellow:hover { background: #ffff00; }
.hover-blue:hover { background: #00f0ff; }
.hover-pink:hover { background: #ff00ff; color: white; }

.btn-card {
  display: block;
  padding: 15px;
  background: black;
  color: white;
  text-decoration: none;
  font-weight: bold;
  border: 2px solid black;
  text-align: center;
  font-family: 'Courier New', monospace;
  transition: 0.2s;
}

.btn-card:hover {
  background: #ffff00;
  color: black;
}

.btn-back {
  font-family: 'Alfa Slab One', serif;
  text-decoration: none;
  color: black;
  border: 4px solid black;
  padding: 15px 30px;
  background: white;
  box-shadow: 6px 6px 0px black;
  margin-bottom: 50px;
  display: inline-block;
  transition: 0.2s;
}

.btn-back:hover {
  background: black;
  color: white;
}
</style>
