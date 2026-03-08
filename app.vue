<template>
  <div class="app-wrapper">
    <header class="navbar">
      <div class="logo-box">KEAGAN.exe</div>
      
      <nav class="nav-links">
        <NuxtLink to="/" class="nav-tab">/ABOUT</NuxtLink>
        <NuxtLink to="/projects" class="nav-tab">/WORK</NuxtLink>
        <NuxtLink to="/contact" class="nav-tab contact-btn">/CONTACT_ME</NuxtLink>
      </nav>
    </header>

    <NuxtPage /> 
  </div>
</template>

<style>

html {
  scroll-behavior: smooth;
}

:root {
  --yellow: #ffff00;
  --bg-cream: #fdfbf0;
}

body {
  margin: 0;
  padding: 0;
  background-color: var(--bg-cream);
  background-image: url('/dottedPaper.png');
  background-size: 800px; 
  background-repeat: repeat;
  font-family: 'Courier New', Courier, monospace;
}

.app-wrapper {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  padding: 0;
}

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: absolute;
  top: 30px;
  left: 40px;
  right: 40px;
  z-index: 1000;
  pointer-events: none;
}

.logo-box, .nav-links {
  pointer-events: auto;
}

.logo-box {
  border: 3px solid black;
  padding: 8px 15px;
  background: white;
  font-weight: 900;
  box-shadow: 4px 4px 0px black;
  font-size: 1.1rem;
}

.nav-links {
  display: flex;
  gap: 12px;
}

.nav-tab {
  border: 3px solid black;
  background-color: white;
  padding: 8px 18px;
  text-decoration: none;
  color: black;
  font-weight: 900;
  font-size: 0.9rem;
  box-shadow: 4px 4px 0px black;
  transition: all 0.1s ease;
}

.nav-tab:hover, .router-link-active {
  background-color: var(--yellow);
  transform: translate(2px, 2px);
  box-shadow: 2px 2px 0px black;
}

.contact-btn {
  background: black;
  color: white;
}

.contact-btn:hover {
  background: var(--yellow);
  color: black;
}
</style>