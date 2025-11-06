<script setup>
import { ref } from 'vue'

const guardaCivilNumber = ref('(82) 99999-9999')
const patrulhaMariaPenhaNumber = ref('(82) 98888-8888')

const callNumber = (number) => {
  window.location.href = `tel:${number.replace(/\D/g, '')}`
}
</script>

<template>
  <div class="app-container">
    <header class="header">
      <div class="header-content">
        <div class="logo-section">
          <div class="shield-icon">🛡️</div>
          <h1 class="title">Guarda Civil Municipal</h1>
        </div>
        <p class="subtitle">Palmeira dos Índios - AL</p>
      </div>
    </header>

    <main class="main-content">
      <div class="hero-section">
        <div class="hero-text">
          <h2 class="hero-title">Protegendo e Servindo Nossa Comunidade</h2>
          <p class="hero-description">
            A Guarda Civil Municipal de Palmeira dos Índios está sempre pronta para atender 
            e proteger os cidadãos. Em caso de emergência, entre em contato através dos canais abaixo.
          </p>
        </div>
      </div>

      <div class="buttons-container">
        <button 
          class="contact-button guarda-civil" 
          @click="callNumber(guardaCivilNumber)"
        >
          <div class="button-icon">📞</div>
          <div class="button-content">
            <span class="button-label">Guarda Civil Municipal</span>
            <span class="button-number">{{ guardaCivilNumber }}</span>
          </div>
        </button>

        <button 
          class="contact-button patrulha-maria-penha" 
          @click="callNumber(patrulhaMariaPenhaNumber)"
        >
          <div class="button-icon">💜</div>
          <div class="button-content">
            <span class="button-label">Patrulha Maria da Penha</span>
            <span class="button-number">{{ patrulhaMariaPenhaNumber }}</span>
          </div>
        </button>
      </div>

      <div class="info-section">
        <div class="info-card">
          <h3>Missão</h3>
          <p>Garantir a segurança e o bem-estar da população de Palmeira dos Índios, 
             promovendo a ordem pública e a proteção dos direitos dos cidadãos.</p>
        </div>
        <div class="info-card">
          <h3>Atendimento</h3>
          <p>Nossos serviços estão disponíveis 24 horas por dia, 7 dias por semana, 
             para garantir a segurança e proteção de todos os cidadãos.</p>
        </div>
      </div>
    </main>

    <footer class="footer">
      <p>&copy; 2025 Guarda Civil Municipal de Palmeira dos Índios - AL. Todos os direitos reservados.</p>
    </footer>
  </div>
</template>

<style scoped>
.app-container {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: linear-gradient(135deg, #0d3b66 0%, #1a5490 100%);
}

.header {
  background: linear-gradient(135deg, #0d3b66 0%, #1a5490 100%);
  padding: 2rem 1rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
  border-bottom: 3px solid #FFD700;
}

.header-content {
  max-width: 1200px;
  margin: 0 auto;
  text-align: center;
}

.logo-section {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 0.5rem;
}

.shield-icon {
  font-size: 3rem;
  filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.3));
}

.title {
  font-size: 2rem;
  font-weight: 700;
  color: #ffffff;
  margin: 0;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.subtitle {
  font-size: 1.1rem;
  color: #FFD700;
  margin: 0;
  font-weight: 500;
}

.main-content {
  flex: 1;
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  padding: 3rem 1rem;
}

.hero-section {
  text-align: center;
  margin-bottom: 3rem;
}

.hero-title {
  font-size: 2.5rem;
  font-weight: 700;
  color: #ffffff;
  margin-bottom: 1rem;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.hero-description {
  font-size: 1.2rem;
  color: rgba(255, 255, 255, 0.9);
  line-height: 1.6;
  max-width: 800px;
  margin: 0 auto;
}

.buttons-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
  max-width: 900px;
  margin-left: auto;
  margin-right: auto;
}

.contact-button {
  background: #ffffff;
  border: none;
  border-radius: 16px;
  padding: 2rem;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  display: flex;
  align-items: center;
  gap: 1.5rem;
  text-align: left;
  position: relative;
  overflow: hidden;
}

.contact-button::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 5px;
  transition: height 0.3s ease;
}

.guarda-civil::before {
  background: linear-gradient(90deg, #0d3b66 0%, #1a5490 100%);
}

.patrulha-maria-penha::before {
  background: linear-gradient(90deg, #9B59B6 0%, #8B7FA8 100%);
}

.contact-button:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
}

.guarda-civil:hover {
  box-shadow: 0 8px 25px rgba(13, 59, 102, 0.4);
}

.contact-button:hover::before {
  height: 100%;
  opacity: 0.1;
}

.contact-button:active {
  transform: translateY(-2px);
}

.button-icon {
  font-size: 3rem;
  flex-shrink: 0;
}

.guarda-civil .button-icon {
  filter: drop-shadow(0 2px 4px rgba(13, 59, 102, 0.3));
}

.patrulha-maria-penha .button-icon {
  filter: drop-shadow(0 2px 4px rgba(155, 89, 182, 0.3));
}

.button-content {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  flex: 1;
}

.button-label {
  font-size: 1.1rem;
  font-weight: 600;
  color: #0d3b66;
  display: block;
}

.patrulha-maria-penha .button-label {
  color: #9B59B6;
}

.button-number {
  font-size: 1.5rem;
  font-weight: 700;
  color: #0d3b66;
  display: block;
  letter-spacing: 1px;
  transition: all 0.3s ease;
}

.guarda-civil:hover .button-number {
  color: #1a5490;
  text-shadow: 0 0 10px rgba(26, 84, 144, 0.5);
}

.patrulha-maria-penha .button-number {
  color: #9B59B6;
}

.info-section {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
  margin-top: 3rem;
}

.info-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border-radius: 12px;
  padding: 2rem;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.info-card h3 {
  color: #FFD700;
  font-size: 1.5rem;
  margin-bottom: 1rem;
  font-weight: 600;
}

.info-card p {
  color: rgba(255, 255, 255, 0.9);
  line-height: 1.6;
  margin: 0;
}

.footer {
  background: #0d3b66;
  padding: 1.5rem;
  text-align: center;
  border-top: 3px solid #FFD700;
  margin-top: auto;
}

.footer p {
  color: rgba(255, 255, 255, 0.8);
  margin: 0;
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  .title {
    font-size: 1.5rem;
  }

  .hero-title {
    font-size: 1.8rem;
  }

  .hero-description {
    font-size: 1rem;
  }

  .buttons-container {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .contact-button {
    padding: 1.5rem;
  }

  .button-icon {
    font-size: 2.5rem;
  }

  .button-number {
    font-size: 1.3rem;
  }
}
</style>
