<template>
  <main class="page">
    <br><br><br><br><br><br><br>
    
    <div class="shape square-blue"></div>
    <div class="shape circle-pink"></div>
    
    <div class="status">
      <span class="dot">●</span> 
      SYSTEM STATUS: ONLINE | 
      
      <span v-if="pending">UPDATING_ENVIRONMENT...</span>
      
      <span v-else-if="error || !weather" class="text-red">ERROR: OFFLINE</span>
      
      <span v-else>
        PRETORIA: {{ Math.round(weather?.main?.temp) }}°C / {{ weather?.weather?.[0]?.description?.toUpperCase() }}
      </span>
    </div>

    <div class="title" @click="toggleTitle">
      <h1 class="main-title">
        {{ currentTitle }}<span v-if="isAnimating" class="terminal-cursor">|</span>
      </h1>
    </div>

    <div class="yellow-box">
      <div v-if="advice?.slip?.advice">
        <p class="advice-tag">SYSTEM_ADVICE.SYS:</p>
        <p class="advice-text">"{{ advice?.slip?.advice }}"</p>
      </div>
      <p v-else class="advice-text">My code works. I’m just as surprised as you are.</p>
      
      <div class="divider"></div>
      <p class="tech-stack">Vue.js • Node • Nuxt • Jamstack</p>
    </div>

    <br><br><br><br><br><br>

    <div class="stripe">
      <div class="stripe-content">
        <span>VUE.JS • NUXT.JS • NODE.JS • JAMSTACK • UNIVERSITY OF PRETORIA • </span>
        <span>VUE.JS • NUXT.JS • NODE.JS • JAMSTACK • UNIVERSITY OF PRETORIA • </span>
      </div>
    </div>

    <div class="profile-box">
      <div class="profile-bar">
        <span class="bar-text">USER_PROFILE.EXE</span>
        <div class="bar-dots">
          <span>○</span><span>○</span><span>●</span>
        </div>
      </div>

      <div class="profile-content">
        <div class="profile-photo">
          <img src="/your-photo.jpg" alt="Keagan's Photo" class="photo-img">
        </div>
        
        <div class="profile-info">
          <h2>WHO AM I?</h2>
          <p>
            I am <strong>Keagan</strong>, a 2nd-year Multimedia student at the 
            <strong>University of Pretoria</strong>.
          </p>
          <p>
            I focus on building high-performance <strong>Jamstack</strong> applications that prioritize simplicity and speed.
          </p>

          <div class="details-box dark">
            <div class="detail-row">
              <strong>/FOCUS</strong>
              <div class="pill-wrap">
                <span class="pill hover-yellow">Full Stack Development</span>
              </div>
            </div>
            
            <div class="detail-row">
              <strong>/CODE</strong>
              <div class="pill-wrap">
                <span class="pill hover-blue">HTML</span>
                <span class="pill hover-blue">CSS</span>
                <span class="pill hover-blue">JS</span>
                <span class="pill hover-blue">C++</span>
              </div>
            </div>

            <div class="detail-row">
              <strong>/TECH</strong>
              <div class="pill-wrap">
                <span class="pill hover-pink">Node.js</span>
                <span class="pill hover-pink">Nuxt.js</span>
                <span class="pill hover-pink">Docker</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="github-box">
      <div class="github-header">
        GITHUB_PROFILE.SYS
      </div>
      
      <div v-if="githubPending" class="git-loading">CONNECTING_TO_SERVER...</div>
      
      <div v-else-if="githubData" class="git-body">
        <img :src="githubData?.avatar_url" class="git-avatar" alt="GitHub Avatar" />
        <div class="git-right">
          <p class="git-user">USER_ID: {{ githubData?.login?.toUpperCase() }}</p>
          
          <div class="git-stats-container">
            <div class="git-stat-box">
              <span class="label">PUBLIC_REPOS</span>
              <span class="value">{{ githubData?.public_repos }}</span>
            </div>
            <div class="git-stat-box">
              <span class="label">FOLLOWERS</span>
              <span class="value">{{ githubData?.followers }}</span>
            </div>
          </div>

          <a :href="githubData?.html_url" target="_blank" class="git-link-btn">
            INITIALIZE_GITHUB_PROTOCOL
          </a>
        </div>
      </div>
      <div v-else class="git-error">CRITICAL_ERROR: GITHUB_UNAVAILABLE</div>
    </div>

    <div class="hero-actions">
      <NuxtLink to="/projects" class="btn btn-black">VIEW PROJECTS</NuxtLink>
      <a href="#" class="btn btn-white">DOWNLOAD CV</a>
    </div>
  </main>
</template>

<script setup>
import { ref } from 'vue'

const titleA = "Developer in TRAINING"
const titleB = "Keagan Coetzee"
const currentTitle = ref(titleA)
const isAnimating = ref(false)

const toggleTitle = async () => {
  if (isAnimating.value) return
  isAnimating.value = true
  const targetText = currentTitle.value === titleA ? titleB : titleA
  
  while (currentTitle.value.length > 0) {
    currentTitle.value = currentTitle.value.slice(0, -1)
    await new Promise(r => setTimeout(r, 60))
  }
  
  await new Promise(r => setTimeout(r, 300))
  
  for (const char of targetText) {
    currentTitle.value += char
    await new Promise(r => setTimeout(r, 120))
  }
  isAnimating.value = false
}

// API Weather
const apiKey = '4ac6aa2f367d198f1c7749c82db9d9b1' 
const city = 'Pretoria'

const { data: weather, pending, error } = await useFetch(
  `https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=${apiKey}`,
  { lazy: true, server: false }
)

// API Github
const githubUsername = 'KeaganCoetzee' 

const { data: githubData, pending: githubPending } = await useFetch(
  `https://api.github.com/users/${githubUsername}`,
  { lazy: true, server: false }
)
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Alfa+Slab+One&family=Roboto:wght@400;900&display=swap');

.page { 
  display: flex; 
  flex-direction: column; 
  align-items: center; 
  justify-content: center; 
  min-height: 100vh; 
  text-align: center; 
}

.shape { 
  position: absolute; 
  z-index: 0; 
  border: 4px solid black; 
  box-shadow: 8px 8px 0px rgba(0,0,0,0.2); 
  pointer-events: none; 
  animation: float 6s ease-in-out infinite; 
}

.square-blue { 
  width: 60px; 
  height: 60px; 
  background-color: #3b82f6; 
  top: 25%; 
  left: 5%; 
}

.circle-pink {
  width: 80px; 
  height: 80px; 
  background-color: #ec4899; 
  border-radius: 50%; 
  bottom: 20%; 
  right: 5%; 
  animation-delay: -3s; 
}

@keyframes float { 
  0%, 100% { transform: translate(0, 0) rotate(0deg); } 
  33% { transform: translate(15px, -25px) rotate(5deg); } 
  66% { transform: translate(-10px, 15px) rotate(-5deg); } 
}
  
.title { 
  font-family: 'Alfa Slab One', serif; 
  cursor: pointer; 
  margin: 20px 0; 
  position: relative; 
  z-index: 10; 
}

.main-title { 
  font-size: 7.5rem; 
  margin: 0; 
  line-height: 1.1; 
  -webkit-text-stroke: 2px black; 
  color: white; 
  text-shadow: 4px 4px 0px black; 
}

.terminal-cursor { 
  display: inline-block; 
  margin-left: 10px; 
  animation: blink 1s step-end infinite; 
  color: black; 
  font-family: sans-serif; 
}

@keyframes blink { 50% { opacity: 0; } }

.status { 
  border: 3px solid black; 
  box-shadow: 4px 4px 0px black; 
  background: white; 
  padding: 5px 15px; 
  font-family: 'Courier New', monospace; 
  font-weight: bold; 
  position: relative; 
  z-index: 10; 
}

.text-red { color: #ff0000; }

.yellow-box { 
  background-color: #ffff00; 
  border: 3px solid black; 
  padding: 30px; 
  margin: 20px 0; 
  box-shadow: 10px 10px 0px black; 
  font-family: 'Courier New', monospace; 
  position: relative; 
  z-index: 10; 
  max-width: 700px; 
  text-align: left;
}

.advice-tag { 
  font-size: 0.7rem; 
  text-decoration: underline; 
  margin-bottom: 5px; 
}

.advice-text { 
  font-size: 1.2rem; 
  font-weight: 900; 
}

.divider { 
  height: 3px; 
  background: black; 
  margin: 15px 0; 
}

.tech-stack {
  font-family: 'Courier New', Courier, monospace;
}

.profile-box {
  display: flex; 
  flex-direction: column; 
  border: 4px solid black; 
  box-shadow: 12px 12px 0px #ffff00; 
  background-color: rgb(244, 224, 197); 
  width: 95%; 
  max-width: 950px; 
  margin: 100px 0 100px 0; 
  position: relative; 
  z-index: 10; 
  animation: reveal linear both; 
  animation-timeline: view(); 
  animation-range: entry 10% cover 30%; 
}

.profile-bar { 
  background: black; 
  color: white; 
  padding: 10px 15px; 
  display: flex; 
  justify-content: space-between; 
  font-family: 'Courier New', monospace; 
  font-weight: bold; 
}

.profile-content { 
  display: grid; 
  grid-template-columns: 350px 1fr; 
}

.profile-photo { 
  border-right: 4px solid black; 
  background: white; 
  padding: 25px; 
}

.photo-img { 
  width: 100%; 
  height: auto; 
  border: 4px solid black;
}

.profile-info { 
  padding: 40px; 
  text-align: left; 
  font-family: 'Roboto', sans-serif; 
}

.profile-info h2 { 
  font-family: 'Alfa Slab One', serif; 
  font-size: 2.8rem; 
  margin-top: 0; 
  color: black; 
}

.details-box.dark { 
  margin-top: 20px; 
  padding: 25px; 
  border: 4px solid black; 
  background-color: #1a1a1a; 
  color: #eeeeee; 
  box-shadow: 8px 8px 0px black; 
}

.detail-row { 
  margin-bottom: 15px; 
}

.detail-row strong { 
  color: #888; 
  font-size: 0.8rem; 
  display: block; 
  margin-bottom: 8px; 
}

.pill { 
  display: inline-block; 
  padding: 8px 18px; 
  border: 3px solid #333; 
  background: #252525; 
  color: #fff; 
  font-weight: 900; 
  font-size: 0.95rem; 
  margin: 5px; 
  transition: all 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275); 
  cursor: pointer; 
}

.pill.hover-yellow:hover { 
  background: #ffff00; 
  color: black; 
  transform: translateY(-4px); 
  box-shadow: 5px 5px 0px #888800; 
}

.pill.hover-blue:hover { 
  background: #00f0ff; 
  color: black; 
  transform: translateY(-4px); 
  box-shadow: 5px 5px 0px #008899; 
}

.pill.hover-pink:hover { 
  background: #ff00ff; 
  color: white; 
  transform: translateY(-4px); 
  box-shadow: 5px 5px 0px #990099; 
}

.github-box {
  width: 95%; 
  max-width: 1100px; 
  background: white; 
  border: 6px solid black; 
  box-shadow: 20px 20px 0px black; 
  margin-bottom: 150px; 
  z-index: 10; 
}

.github-header { 
  background: black; 
  color: white; 
  padding: 15px 25px; 
  font-family: 'Courier New', monospace; 
  font-weight: bold; 
  font-size: 1.2rem; 
}

.git-body { 
  display: flex; 
  padding: 50px; 
  gap: 50px; 
  align-items: center; 
}

.git-avatar { 
  width: 220px; 
  height: 220px; 
  border: 6px solid black; 
}

.git-right { 
  flex: 1; 
  text-align: left; 
  display: flex; 
  flex-direction: column; 
  gap: 25px; 
}

.git-user { 
  font-family: 'Alfa Slab One', serif; 
  font-size: 2.2rem; 
  margin: 0; 
}

.git-stats-container { 
  display: flex; 
  gap: 40px; 
}

.git-stat-box { 
  background: #f0f0f0; 
  border: 4px solid black; 
  padding: 20px 35px; 
  display: flex; 
  flex-direction: column; 
}

.git-stat-box .label { 
  font-size: 0.9rem; 
  font-weight: 900; 
  font-family: 'Courier New', monospace; 
}

.git-stat-box .value { 
  font-family: 'Alfa Slab One', serif; 
  font-size: 3rem; 
}

.git-link-btn { 
  background: black; 
  color: white; 
  text-decoration: none; 
  padding: 20px 30px; 
  text-align: center; 
  font-weight: 900; 
  font-family: 'Courier New', monospace; 
  border: 4px solid black; 
  transition: 0.2s; 
  font-size: 1.1rem; 
}

.git-link-btn:hover { 
  background: #ffff00; 
  color: black; 
  transform: translate(-5px, -5px); 
  box-shadow: 8px 8px 0px black; 
}

.stripe { 
  width: 100vw; 
  background: black; 
  color: white; 
  padding: 25px 0; 
  overflow: hidden; 
  border-top: 5px solid #ffff00; 
  border-bottom: 5px solid #ffff00; 
  position: relative; 
  z-index: 10; 
}

.stripe-content { 
  display: flex; 
  white-space: nowrap; 
  animation: scroll 30s linear infinite; 
}

.stripe-content span { 
  font-family: 'Alfa Slab One', serif; 
  font-size: 2.2rem; 
  padding-right: 80px; 
}

@keyframes scroll { 
  from { transform: translateX(0); } 
  to { transform: translateX(-50%); } 
}

.hero-actions { 
  margin: 60px 0 150px 0; 
  position: relative; 
  z-index: 10; 
}

.btn { 
  display: inline-block; 
  padding: 15px 30px; 
  border: 4px solid black; 
  text-decoration: none; 
  font-weight: 900; 
  margin: 15px; 
  font-size: 1.1rem; 
}

.btn-black { background: black; color: white; }
.btn-white { background: white; color: black; box-shadow: 6px 6px 0px black; }

@keyframes reveal { 
  from { opacity: 0; transform: translateY(100px) scale(0.95); } 
  to { opacity: 1; transform: translateY(0) scale(1); } 
}
</style>
