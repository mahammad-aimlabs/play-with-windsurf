<script setup>
import { ref } from 'vue'

const features = ref([
  {
    icon: '🚀',
    title: 'Lightning Fast',
    description: 'Built for speed with optimized performance that delivers results in milliseconds.'
  },
  {
    icon: '🔒',
    title: 'Secure by Design',
    description: 'Enterprise-grade security with end-to-end encryption and compliance standards.'
  },
  {
    icon: '🎨',
    title: 'Beautiful UI',
    description: 'Stunning interfaces crafted with attention to detail and modern design principles.'
  },
  {
    icon: '📱',
    title: 'Fully Responsive',
    description: 'Seamless experience across all devices from mobile to desktop screens.'
  }
])

const stats = ref([
  { value: '10K+', label: 'Active Users' },
  { value: '99.9%', label: 'Uptime' },
  { value: '50+', label: 'Countries' },
  { value: '24/7', label: 'Support' }
])
</script>

<template>
  <main class="main-content">
    <!-- Hero Section -->
    <section id="home" class="hero">
      <div class="hero-container">
        <div class="hero-content">
          <span class="hero-badge">Welcome to MyBrand</span>
          <h1 class="hero-title">
            Build Something
            <span class="gradient-text">Amazing</span>
            Today
          </h1>
          <p class="hero-description">
            Transform your ideas into reality with our powerful platform. 
            We provide the tools you need to create, innovate, and succeed.
          </p>
          <div class="hero-buttons">
            <button class="btn btn-primary">Get Started Free</button>
            <button class="btn btn-secondary">Watch Demo</button>
          </div>
        </div>
        <div class="hero-visual">
          <div class="hero-card">
            <div class="card-glow"></div>
            <div class="card-content">
              <div class="card-icon">◆</div>
              <div class="card-lines">
                <span></span>
                <span></span>
                <span></span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Stats Section -->
    <section class="stats">
      <div class="stats-container">
        <div v-for="stat in stats" :key="stat.label" class="stat-item">
          <span class="stat-value">{{ stat.value }}</span>
          <span class="stat-label">{{ stat.label }}</span>
        </div>
      </div>
    </section>

    <!-- Features Section -->
    <section id="services" class="features">
      <div class="features-container">
        <div class="section-header">
          <span class="section-badge">Features</span>
          <h2 class="section-title">Everything You Need</h2>
          <p class="section-description">
            Powerful features designed to help you build faster and smarter.
          </p>
        </div>
        <div class="features-grid">
          <div v-for="feature in features" :key="feature.title" class="feature-card">
            <div class="feature-icon">{{ feature.icon }}</div>
            <h3 class="feature-title">{{ feature.title }}</h3>
            <p class="feature-description">{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="about">
      <div class="about-container">
        <div class="about-content">
          <span class="section-badge">About Us</span>
          <h2 class="section-title">We're on a Mission</h2>
          <p class="about-text">
            Founded in 2024, we've been dedicated to empowering developers and businesses 
            with cutting-edge tools. Our team of passionate engineers works tirelessly 
            to deliver solutions that make a difference.
          </p>
          <p class="about-text">
            We believe in simplicity, performance, and user experience. Every feature 
            we build is crafted with care to ensure it meets the highest standards.
          </p>
          <button class="btn btn-primary">Learn More</button>
        </div>
        <div class="about-visual">
          <div class="about-grid">
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
            <div class="grid-item"></div>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section id="contact" class="cta-section">
      <div class="cta-container">
        <h2 class="cta-title">Ready to Get Started?</h2>
        <p class="cta-description">
          Join thousands of satisfied users and take your project to the next level.
        </p>
        <div class="cta-form">
          <input type="email" placeholder="Enter your email" class="cta-input" />
          <button class="btn btn-primary">Subscribe</button>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
/* ========== BASE STYLES ========== */
.main-content {
  width: 100%;
  background: linear-gradient(180deg, #0f0f1a 0%, #1a1a2e 100%);
  color: #fff;
}

/* ========== HERO SECTION ========== */
.hero {
  min-height: calc(100vh - 80px);
  display: flex;
  align-items: center;
  padding: 60px 24px;
  position: relative;
  overflow: hidden;
}

.hero::before {
  content: '';
  position: absolute;
  top: -50%;
  right: -20%;
  width: 600px;
  height: 600px;
  background: radial-gradient(circle, rgba(233, 69, 96, 0.15) 0%, transparent 70%);
  pointer-events: none;
}

.hero-container {
  max-width: 1400px;
  margin: 0 auto;
  width: 100%;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
}

.hero-badge {
  display: inline-block;
  padding: 8px 16px;
  background: rgba(233, 69, 96, 0.15);
  color: #e94560;
  border-radius: 50px;
  font-size: 14px;
  font-weight: 600;
  margin-bottom: 24px;
}

.hero-title {
  font-size: 56px;
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 24px;
}

.gradient-text {
  background: linear-gradient(135deg, #e94560, #ff6b6b);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-description {
  font-size: 18px;
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.7;
  margin-bottom: 32px;
  max-width: 500px;
}

.hero-buttons {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
}

/* ========== BUTTONS ========== */
.btn {
  padding: 14px 32px;
  border-radius: 50px;
  font-size: 15px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.25s ease;
  border: none;
}

.btn-primary {
  background: linear-gradient(135deg, #e94560, #ff6b6b);
  color: #fff;
  box-shadow: 0 4px 15px rgba(233, 69, 96, 0.35);
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(233, 69, 96, 0.45);
}

.btn-secondary {
  background: rgba(255, 255, 255, 0.1);
  color: #fff;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.btn-secondary:hover {
  background: rgba(255, 255, 255, 0.15);
  border-color: rgba(255, 255, 255, 0.3);
}

/* ========== HERO VISUAL ========== */
.hero-visual {
  display: flex;
  justify-content: center;
  align-items: center;
}

.hero-card {
  width: 350px;
  height: 400px;
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
  border-radius: 24px;
  position: relative;
  overflow: hidden;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.4);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.card-glow {
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: conic-gradient(from 0deg, transparent, #e94560, transparent 30%);
  animation: rotate 4s linear infinite;
  opacity: 0.3;
}

@keyframes rotate {
  100% {
    transform: rotate(360deg);
  }
}

.card-content {
  position: absolute;
  inset: 2px;
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
  border-radius: 22px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 30px;
}

.card-icon {
  font-size: 64px;
  color: #e94560;
  filter: drop-shadow(0 0 20px rgba(233, 69, 96, 0.5));
}

.card-lines {
  display: flex;
  flex-direction: column;
  gap: 12px;
  width: 60%;
}

.card-lines span {
  height: 12px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 6px;
}

.card-lines span:nth-child(2) {
  width: 80%;
}

.card-lines span:nth-child(3) {
  width: 60%;
}

/* ========== STATS SECTION ========== */
.stats {
  padding: 60px 24px;
  background: rgba(255, 255, 255, 0.02);
  border-top: 1px solid rgba(255, 255, 255, 0.05);
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}

.stats-container {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 40px;
}

.stat-item {
  text-align: center;
}

.stat-value {
  display: block;
  font-size: 42px;
  font-weight: 800;
  background: linear-gradient(135deg, #e94560, #ff6b6b);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 8px;
}

.stat-label {
  font-size: 16px;
  color: rgba(255, 255, 255, 0.6);
}

/* ========== FEATURES SECTION ========== */
.features {
  padding: 100px 24px;
}

.features-container {
  max-width: 1200px;
  margin: 0 auto;
}

.section-header {
  text-align: center;
  margin-bottom: 60px;
}

.section-badge {
  display: inline-block;
  padding: 8px 16px;
  background: rgba(233, 69, 96, 0.15);
  color: #e94560;
  border-radius: 50px;
  font-size: 14px;
  font-weight: 600;
  margin-bottom: 16px;
}

.section-title {
  font-size: 42px;
  font-weight: 800;
  margin-bottom: 16px;
}

.section-description {
  font-size: 18px;
  color: rgba(255, 255, 255, 0.6);
  max-width: 500px;
  margin: 0 auto;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
}

.feature-card {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 20px;
  padding: 32px;
  transition: all 0.3s ease;
}

.feature-card:hover {
  background: rgba(255, 255, 255, 0.06);
  border-color: rgba(233, 69, 96, 0.3);
  transform: translateY(-4px);
}

.feature-icon {
  font-size: 40px;
  margin-bottom: 20px;
}

.feature-title {
  font-size: 20px;
  font-weight: 700;
  margin-bottom: 12px;
}

.feature-description {
  font-size: 15px;
  color: rgba(255, 255, 255, 0.6);
  line-height: 1.6;
}

/* ========== ABOUT SECTION ========== */
.about {
  padding: 100px 24px;
  background: rgba(255, 255, 255, 0.02);
}

.about-container {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
}

.about-content .section-badge {
  margin-bottom: 16px;
}

.about-content .section-title {
  text-align: left;
  margin-bottom: 24px;
}

.about-text {
  font-size: 16px;
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.8;
  margin-bottom: 20px;
}

.about-visual {
  display: flex;
  justify-content: center;
}

.about-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
  width: 100%;
  max-width: 400px;
}

.grid-item {
  aspect-ratio: 1;
  background: linear-gradient(135deg, rgba(233, 69, 96, 0.2) 0%, rgba(255, 107, 107, 0.1) 100%);
  border-radius: 20px;
  border: 1px solid rgba(233, 69, 96, 0.2);
}

.grid-item:nth-child(2) {
  transform: translateY(30px);
}

.grid-item:nth-child(3) {
  transform: translateY(-30px);
}

/* ========== CTA SECTION ========== */
.cta-section {
  padding: 100px 24px;
  text-align: center;
}

.cta-container {
  max-width: 600px;
  margin: 0 auto;
}

.cta-title {
  font-size: 36px;
  font-weight: 800;
  margin-bottom: 16px;
}

.cta-description {
  font-size: 18px;
  color: rgba(255, 255, 255, 0.6);
  margin-bottom: 32px;
}

.cta-form {
  display: flex;
  gap: 12px;
  max-width: 450px;
  margin: 0 auto;
}

.cta-input {
  flex: 1;
  padding: 14px 24px;
  background: rgba(255, 255, 255, 0.08);
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 50px;
  color: #fff;
  font-size: 15px;
  outline: none;
  transition: all 0.25s ease;
}

.cta-input::placeholder {
  color: rgba(255, 255, 255, 0.4);
}

.cta-input:focus {
  border-color: #e94560;
  background: rgba(255, 255, 255, 0.1);
}

/* ========== RESPONSIVE: TABLET ========== */
@media (max-width: 1024px) {
  .hero-title {
    font-size: 44px;
  }

  .hero-container {
    gap: 40px;
  }

  .hero-card {
    width: 300px;
    height: 350px;
  }

  .features-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .stats-container {
    grid-template-columns: repeat(2, 1fr);
    gap: 30px;
  }
}

/* ========== RESPONSIVE: MOBILE ========== */
@media (max-width: 768px) {
  .hero {
    min-height: auto;
    padding: 40px 20px 60px;
  }

  .hero-container {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .hero-title {
    font-size: 36px;
  }

  .hero-description {
    margin: 0 auto 32px;
  }

  .hero-buttons {
    justify-content: center;
  }

  .hero-visual {
    order: -1;
    margin-bottom: 20px;
  }

  .hero-card {
    width: 250px;
    height: 280px;
  }

  .card-icon {
    font-size: 48px;
  }

  .stats-container {
    grid-template-columns: repeat(2, 1fr);
  }

  .stat-value {
    font-size: 32px;
  }

  .features {
    padding: 60px 20px;
  }

  .features-grid {
    grid-template-columns: 1fr;
  }

  .section-title {
    font-size: 32px;
  }

  .about {
    padding: 60px 20px;
  }

  .about-container {
    grid-template-columns: 1fr;
    gap: 40px;
  }

  .about-content {
    text-align: center;
  }

  .about-content .section-title {
    text-align: center;
  }

  .about-visual {
    order: -1;
  }

  .about-grid {
    max-width: 280px;
  }

  .grid-item:nth-child(2),
  .grid-item:nth-child(3) {
    transform: none;
  }

  .cta-section {
    padding: 60px 20px;
  }

  .cta-title {
    font-size: 28px;
  }

  .cta-form {
    flex-direction: column;
  }

  .cta-form .btn {
    width: 100%;
  }
}

/* ========== RESPONSIVE: SMALL MOBILE ========== */
@media (max-width: 480px) {
  .hero-title {
    font-size: 28px;
  }

  .hero-description {
    font-size: 16px;
  }

  .btn {
    padding: 12px 24px;
    font-size: 14px;
  }

  .stat-value {
    font-size: 28px;
  }

  .stat-label {
    font-size: 14px;
  }

  .section-title {
    font-size: 26px;
  }

  .feature-card {
    padding: 24px;
  }
}
</style>