<script setup>
import { ref, onMounted } from 'vue'

const logoImage = ref(null)
const showLogo = ref(false)

// Tenta carregar o logo - adicione o arquivo logo.png em public/images/
// Se preferir usar outro formato, altere a extensão abaixo (logo.jpg, logo.svg, etc)
onMounted(() => {
  // Tenta carregar a imagem usando uma URL da pasta public
  const img = new Image()
  img.onload = () => {
    logoImage.value = '/images/logo.png'
    showLogo.value = true
  }
  img.onerror = () => {
    // Se o arquivo não existir, mostra o emoji do escudo
    showLogo.value = false
  }
  img.src = '/images/logo.png'
})

const guardaCivilNumber = ref('(82) 98830-0793')
const patrulhaMariaPenhaNumber = ref('(82) 98830-0887')

const callNumber = (number) => {
  window.location.href = `tel:${number.replace(/\D/g, '')}`
}
</script>

<template>
  <div class="app-container">
    <header class="header">
      <div class="header-content">
        <div class="logo-section">
          <img v-if="showLogo && logoImage" :src="logoImage" alt="Logo Guarda Civil Municipal" class="logo-image" />
          <div v-else class="shield-icon">🛡️</div>
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
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes pulse {
  0%, 100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
}

@keyframes shimmer {
  0% {
    background-position: -1000px 0;
  }
  100% {
    background-position: 1000px 0;
  }
}

.app-container {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: linear-gradient(to right, #0d3b66 0%, #1a5490 35%, #9B59B6 90%);
  position: relative;
  overflow-x: hidden;
}


.header {
  background: linear-gradient(to right, #0d3b66 0%, #1a5490 35%, #9B59B6 90%);
  padding: 1.5rem 1rem;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
  border-bottom: 4px solid #FFD700;
  position: relative;
  z-index: 1;
  animation: fadeInDown 0.8s ease-out;
}

@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.header::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, #FFD700, transparent);
  opacity: 0.5;
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
  gap: 1.5rem;
  margin-bottom: 0.5rem;
  animation: fadeInUp 0.8s ease-out 0.2s both;
}

.logo-image {
  width: 140px;
  height: auto;
  max-height: 160px;
  object-fit: contain;
  filter: drop-shadow(0 4px 8px rgba(0, 0, 0, 0.4));
  transition: transform 0.3s ease;
  animation: pulse 3s ease-in-out infinite;
}

.logo-image:hover {
  transform: scale(1.1) rotate(5deg);
}

.shield-icon {
  font-size: 4rem;
  filter: drop-shadow(0 4px 8px rgba(0, 0, 0, 0.4));
  animation: pulse 3s ease-in-out infinite;
  transition: transform 0.3s ease;
}

.shield-icon:hover {
  transform: scale(1.1);
}

.title {
  font-size: 2rem;
  font-weight: 800;
  color: #ffffff;
  margin: 0;
  text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.4), 0 0 20px rgba(255, 255, 255, 0.2);
  letter-spacing: 0.5px;
  background: linear-gradient(135deg, #ffffff 0%, #f0f0f0 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.subtitle {
  font-size: 1.1rem;
  color: #FFD700;
  margin: 0;
  font-weight: 600;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
  letter-spacing: 1px;
  animation: fadeIn 1s ease-out 0.4s both;
}

.main-content {
  flex: 1;
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  padding: 2rem 1rem;
  position: relative;
  z-index: 1;
}

.hero-section {
  text-align: center;
  margin-bottom: 2.5rem;
  animation: fadeInUp 0.8s ease-out 0.6s both;
}

.hero-title {
  font-size: 2.5rem;
  font-weight: 800;
  color: #ffffff;
  margin-bottom: 1rem;
  text-shadow: 3px 3px 8px rgba(0, 0, 0, 0.4), 0 0 30px rgba(255, 255, 255, 0.1);
  letter-spacing: -0.5px;
  line-height: 1.2;
}

.hero-description {
  font-size: 1.15rem;
  color: rgba(255, 255, 255, 0.95);
  line-height: 1.6;
  max-width: 800px;
  margin: 0 auto 1rem;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
}

.buttons-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
  max-width: 1000px;
  margin-left: auto;
  margin-right: auto;
  animation: fadeInUp 0.8s ease-out 0.8s both;
}

.contact-button {
  background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
  border: none;
  border-radius: 20px;
  padding: 2.5rem;
  cursor: pointer;
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2), 0 0 0 1px rgba(255, 255, 255, 0.1);
  display: flex;
  align-items: center;
  gap: 1.75rem;
  text-align: left;
  position: relative;
  overflow: hidden;
}

.contact-button::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
  transition: left 0.5s ease;
}

.contact-button:hover::before {
  left: 100%;
}

.contact-button::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 4px;
  transition: all 0.4s ease;
}

.guarda-civil::after {
  background: linear-gradient(90deg, #0d3b66 0%, #1a5490 50%, #2c5aa0 100%);
}

.patrulha-maria-penha::after {
  background: linear-gradient(90deg, #9B59B6 0%, #8B7FA8 50%, #a569bd 100%);
}

.contact-button:hover {
  transform: translateY(-8px) scale(1.02);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3), 0 0 0 1px rgba(255, 255, 255, 0.2);
}

.guarda-civil:hover {
  box-shadow: 0 20px 40px rgba(13, 59, 102, 0.4), 0 0 0 1px rgba(255, 255, 255, 0.2);
}

.contact-button:hover::after {
  height: 100%;
  opacity: 0.08;
}

.contact-button:active {
  transform: translateY(-4px) scale(1);
}

.button-icon {
  font-size: 3.5rem;
  flex-shrink: 0;
  transition: transform 0.3s ease;
  filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.2));
}

.contact-button:hover .button-icon {
  transform: scale(1.15) rotate(5deg);
}

.guarda-civil .button-icon {
  filter: drop-shadow(0 4px 8px rgba(13, 59, 102, 0.4));
}

.patrulha-maria-penha .button-icon {
  filter: drop-shadow(0 4px 8px rgba(155, 89, 182, 0.4));
}

.button-content {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  flex: 1;
  position: relative;
  z-index: 1;
}

.button-label {
  font-size: 1.2rem;
  font-weight: 700;
  color: #0d3b66;
  display: block;
  letter-spacing: 0.3px;
}

.patrulha-maria-penha .button-label {
  color: #9B59B6;
}

.button-number {
  font-size: 1.75rem;
  font-weight: 800;
  color: #0d3b66;
  display: block;
  letter-spacing: 1.5px;
  transition: all 0.3s ease;
  font-family: 'Courier New', monospace;
}

.guarda-civil:hover .button-number {
  color: #1a5490;
  text-shadow: 0 0 15px rgba(26, 84, 144, 0.6);
  transform: scale(1.05);
}

.patrulha-maria-penha .button-number {
  color: #9B59B6;
}

.patrulha-maria-penha:hover .button-number {
  color: #8B7FA8;
  text-shadow: 0 0 15px rgba(155, 89, 182, 0.6);
  transform: scale(1.05);
}

.info-section {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2.5rem;
  margin-top: 4rem;
  animation: fadeInUp 0.8s ease-out 1s both;
}

.info-card {
  background: rgba(255, 255, 255, 0.12);
  backdrop-filter: blur(20px);
  border-radius: 20px;
  padding: 2.5rem;
  border: 1px solid rgba(255, 255, 255, 0.25);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
  transition: all 0.4s ease;
  position: relative;
  overflow: hidden;
}

.info-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: linear-gradient(90deg, #FFD700, #FFA500, #FFD700);
  transform: scaleX(0);
  transition: transform 0.4s ease;
}

.info-card:hover {
  transform: translateY(-5px);
  background: rgba(255, 255, 255, 0.15);
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.3);
}

.info-card:hover::before {
  transform: scaleX(1);
}

.info-card h3 {
  color: #FFD700;
  font-size: 1.75rem;
  margin-bottom: 1.25rem;
  font-weight: 700;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
  position: relative;
  z-index: 1;
}

.info-card p {
  color: rgba(255, 255, 255, 0.95);
  line-height: 1.8;
  margin: 0;
  font-size: 1.05rem;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.2);
  position: relative;
  z-index: 1;
}

.footer {
  background: linear-gradient(to right, #0d3b66 0%, #1a5490 35%, #9B59B6 90%);
  padding: 2rem 1.5rem;
  text-align: center;
  border-top: 4px solid #FFD700;
  margin-top: auto;
  box-shadow: 0 -4px 20px rgba(0, 0, 0, 0.2);
  position: relative;
  z-index: 1;
}

.footer p {
  color: rgba(255, 255, 255, 0.9);
  margin: 0;
  font-size: 0.95rem;
  letter-spacing: 0.5px;
}

@media (max-width: 768px) {
  .header {
    padding: 1rem 1rem;
  }

  .logo-section {
    gap: 1rem;
    margin-bottom: 0.25rem;
  }

  .logo-image {
    width: 80px;
    max-height: 100px;
  }

  .shield-icon {
    font-size: 2.5rem;
  }

  .title {
    font-size: 1.5rem;
  }

  .subtitle {
    font-size: 1rem;
    margin-top: 0.25rem;
  }

  .main-content {
    padding: 1rem 1rem;
  }

  .hero-section {
    margin-bottom: 1.5rem;
  }

  .hero-title {
    font-size: 1.5rem;
    margin-bottom: 0.75rem;
  }

  .hero-description {
    font-size: 1rem;
    line-height: 1.5;
    margin-bottom: 0.5rem;
  }

  .buttons-container {
    grid-template-columns: 1fr;
    gap: 1.25rem;
    margin-bottom: 2rem;
  }

  .contact-button {
    padding: 1.5rem;
  }

  .button-icon {
    font-size: 2.5rem;
  }

  .button-label {
    font-size: 1rem;
  }

  .button-number {
    font-size: 1.25rem;
  }

  .info-section {
    grid-template-columns: 1fr;
    gap: 1.5rem;
    margin-top: 2rem;
  }

  .info-card {
    padding: 1.5rem;
  }

  .info-card h3 {
    font-size: 1.25rem;
    margin-bottom: 0.75rem;
  }

  .info-card p {
    font-size: 0.95rem;
  }
}

@media (max-width: 480px) {
  .header {
    padding: 0.75rem 0.75rem;
  }

  .logo-section {
    gap: 0.75rem;
    margin-bottom: 0.25rem;
  }

  .logo-image {
    width: 70px;
    max-height: 90px;
  }

  .shield-icon {
    font-size: 2rem;
  }

  .title {
    font-size: 1.25rem;
  }

  .subtitle {
    font-size: 0.9rem;
  }

  .main-content {
    padding: 0.75rem 0.75rem;
  }

  .hero-section {
    margin-bottom: 1rem;
  }

  .hero-title {
    font-size: 1.25rem;
    margin-bottom: 0.5rem;
  }

  .hero-description {
    font-size: 0.9rem;
    line-height: 1.4;
    margin-bottom: 0.5rem;
  }

  .buttons-container {
    gap: 1rem;
    margin-bottom: 1.5rem;
  }

  .contact-button {
    padding: 1.25rem;
    flex-direction: row;
    text-align: left;
    gap: 1rem;
  }

  .button-icon {
    font-size: 2rem;
  }

  .button-label {
    font-size: 0.95rem;
  }

  .button-number {
    font-size: 1.1rem;
  }

  .button-content {
    align-items: flex-start;
  }

  .info-section {
    margin-top: 1.5rem;
    gap: 1.25rem;
  }

  .info-card {
    padding: 1.25rem;
  }

  .info-card h3 {
    font-size: 1.1rem;
    margin-bottom: 0.5rem;
  }

  .info-card p {
    font-size: 0.9rem;
  }
}
</style>
