<template>
  //Keagan Coetzee u25122003
  <main class="contact-page">
    <h1 class="page-title">/CONTACT</h1>

    <div class="contact-container">
      <div class="status-bar">● INCOMING MESSAGE</div>
      
      <form name="contact" method="POST" data-netlify="true" class="brutalist-form">
        <div class="form-group">
          <label>SENDER_NAME:</label>
          <input type="text" name="name" placeholder="John Doe" required />
        </div>

        <div class="form-group">
          <label>SENDER_EMAIL:</label>
          <input type="email" name="email" placeholder="john@example.com" required />
        </div>

        <div class="form-group">
          <label>MESSAGE_BODY:</label>
          <textarea name="message" rows="5" placeholder="Type your message here..." required></textarea>
        </div>

        <button type="submit" class="submit-btn">SEND_MESSAGE</button>
      </form>
    </div>
  </main>
</template>

<style scoped>
.contact-page {
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.page-title {
  font-size: 3rem;
  background: white;
  border: 3px solid black;
  padding: 10px 30px;
  box-shadow: 6px 6px 0px var(--yellow);
  margin-bottom: 40px;
}

.contact-container {
  width: 100%;
  max-width: 500px;
  background: white;
  border: 3px solid black;
  box-shadow: 10px 10px 0px black;
}

.status-bar {
  background: black;
  color: white;
  padding: 5px 10px;
  font-weight: bold;
  font-size: 0.8rem;
}

.brutalist-form {
  padding: 20px;
}

.form-group {
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
}

.form-group label {
  font-weight: bold;
  margin-bottom: 5px;
}

input, textarea {
  border: 2px solid black;
  padding: 10px;
  font-family: 'Courier New', Courier, monospace;
  background: var(--bg-cream);
}

input:focus, textarea:focus {
  outline: none;
  background: var(--yellow);
}

.submit-btn {
  width: 100%;
  padding: 15px;
  background: black;
  color: white;
  border: none;
  font-weight: bold;
  cursor: pointer;
  transition: 0.1s;
}

.submit-btn:hover {
  background: var(--yellow);
  color: black;
  border: 2px solid black;
}
</style>
