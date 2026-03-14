<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const menuItems = ref([
  { name: 'Home', href: '#' },
  { name: 'About', href: '#about' },
  { name: 'Services', href: '#services' },
  { name: 'Portfolio', href: '#portfolio' },
  { name: 'Contact', href: '#contact' }
])

const activeItem = ref('Home')
const isMenuOpen = ref(false)

const setActive = (name) => {
  activeItem.value = name
  isMenuOpen.value = false
}

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
  document.body.style.overflow = isMenuOpen.value ? 'hidden' : ''
}

const closeMenu = () => {
  isMenuOpen.value = false
  document.body.style.overflow = ''
}

onUnmounted(() => {
  document.body.style.overflow = ''
})
</script>

<template>
  <header class="header">
    <div class="header-container">
      <!-- Logo - Always Left -->
      <a href="#" class="logo">
        <span class="logo-icon">◆</span>
        <span class="logo-text">MyBrand</span>
      </a>

      <!-- Desktop Navigation - Center -->
      <nav class="desktop-nav">
        <ul class="nav-list">
          <li v-for="item in menuItems" :key="item.name">
            <a 
              :href="item.href"
              :class="['nav-link', { active: activeItem === item.name }]"
              @click="setActive(item.name)"
            >
              {{ item.name }}
            </a>
          </li>
        </ul>
      </nav>

      <!-- Desktop CTA - Right -->
      <button class="cta-button desktop-cta">Get Started</button>

      <!-- Mobile Menu Toggle - Right on Mobile -->
      <button 
        class="menu-toggle" 
        @click="toggleMenu"
        :class="{ active: isMenuOpen }"
        aria-label="Toggle menu"
      >
        <span class="hamburger"></span>
      </button>
    </div>

    <!-- Mobile Overlay -->
    <Transition name="fade">
      <div 
        v-if="isMenuOpen"
        class="overlay"
        @click="closeMenu"
      ></div>
    </Transition>

    <!-- Mobile Slide-in Navigation -->
    <Transition name="slide">
      <nav v-if="isMenuOpen" class="mobile-nav">
        <div class="mobile-nav-header">
          <a href="#" class="logo" @click="closeMenu">
            <span class="logo-icon">◆</span>
            <span class="logo-text">MyBrand</span>
          </a>
          <button class="close-btn" @click="closeMenu" aria-label="Close menu">
            <span></span>
            <span></span>
          </button>
        </div>

        <ul class="mobile-nav-list">
          <li v-for="item in menuItems" :key="item.name">
            <a 
              :href="item.href"
              :class="['mobile-nav-link', { active: activeItem === item.name }]"
              @click="setActive(item.name)"
            >
              {{ item.name }}
            </a>
          </li>
        </ul>

        <div class="mobile-nav-footer">
          <button class="cta-button" @click="closeMenu">Get Started</button>
        </div>
      </nav>
    </Transition>
  </header>
</template>

<style scoped>
/* ========== BASE HEADER ========== */
.header {
  position: sticky;
  top: 0;
  left: 0;
  right: 0;
  width: 100%;
  height: 80px;
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.3);
  z-index: 1000;
}

.header-container {
  width: 100%;
  height: 100%;
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 24px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
}

/* ========== LOGO ========== */
.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  text-decoration: none;
  flex-shrink: 0;
}

.logo-icon {
  font-size: 28px;
  color: #e94560;
  filter: drop-shadow(0 0 8px rgba(233, 69, 96, 0.5));
  transition: transform 0.3s ease;
}

.logo:hover .logo-icon {
  transform: rotate(180deg);
}

.logo-text {
  font-size: 22px;
  font-weight: 700;
  color: #fff;
  letter-spacing: 0.5px;
}

/* ========== DESKTOP NAVIGATION ========== */
.desktop-nav {
  display: flex;
  justify-content: center;
  flex: 1;
}

.nav-list {
  display: flex;
  align-items: center;
  gap: 8px;
  list-style: none;
  margin: 0;
  padding: 0;
}

.nav-link {
  display: block;
  padding: 10px 20px;
  color: rgba(255, 255, 255, 0.75);
  text-decoration: none;
  font-size: 15px;
  font-weight: 500;
  border-radius: 8px;
  transition: all 0.25s ease;
  position: relative;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: 6px;
  left: 50%;
  transform: translateX(-50%) scaleX(0);
  width: 24px;
  height: 2px;
  background: #e94560;
  border-radius: 2px;
  transition: transform 0.25s ease;
}

.nav-link:hover {
  color: #fff;
  background: rgba(255, 255, 255, 0.08);
}

.nav-link:hover::after,
.nav-link.active::after {
  transform: translateX(-50%) scaleX(1);
}

.nav-link.active {
  color: #fff;
}

/* ========== CTA BUTTON ========== */
.cta-button {
  padding: 12px 28px;
  background: linear-gradient(135deg, #e94560, #ff6b6b);
  color: #fff;
  border: none;
  border-radius: 50px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.25s ease;
  box-shadow: 0 4px 15px rgba(233, 69, 96, 0.35);
  white-space: nowrap;
  flex-shrink: 0;
}

.cta-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(233, 69, 96, 0.45);
}

.cta-button:active {
  transform: translateY(0);
}

/* ========== HAMBURGER MENU TOGGLE ========== */
.menu-toggle {
  display: none;
  width: 44px;
  height: 44px;
  background: rgba(255, 255, 255, 0.1);
  border: none;
  border-radius: 10px;
  cursor: pointer;
  position: relative;
  flex-shrink: 0;
  transition: background 0.25s ease;
}

.menu-toggle:hover {
  background: rgba(255, 255, 255, 0.15);
}

.hamburger,
.hamburger::before,
.hamburger::after {
  position: absolute;
  width: 22px;
  height: 2px;
  background: #fff;
  border-radius: 2px;
  transition: all 0.3s ease;
}

.hamburger {
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

.hamburger::before,
.hamburger::after {
  content: '';
  left: 0;
}

.hamburger::before {
  top: -7px;
}

.hamburger::after {
  top: 7px;
}

.menu-toggle.active .hamburger {
  background: transparent;
}

.menu-toggle.active .hamburger::before {
  top: 0;
  transform: rotate(45deg);
}

.menu-toggle.active .hamburger::after {
  top: 0;
  transform: rotate(-45deg);
}

/* ========== OVERLAY ========== */
.overlay {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.6);
  backdrop-filter: blur(4px);
  z-index: 1001;
}

/* ========== MOBILE NAVIGATION ========== */
.mobile-nav {
  position: fixed;
  top: 0;
  left: 0;
  width: 300px;
  max-width: 85vw;
  height: 100vh;
  height: 100dvh;
  background: linear-gradient(180deg, #1a1a2e 0%, #0f3460 100%);
  z-index: 1002;
  display: flex;
  flex-direction: column;
  box-shadow: 4px 0 30px rgba(0, 0, 0, 0.4);
}

.mobile-nav-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.close-btn {
  width: 40px;
  height: 40px;
  background: rgba(255, 255, 255, 0.1);
  border: none;
  border-radius: 10px;
  cursor: pointer;
  position: relative;
  transition: background 0.25s ease;
}

.close-btn:hover {
  background: rgba(233, 69, 96, 0.3);
}

.close-btn span {
  position: absolute;
  left: 50%;
  top: 50%;
  width: 18px;
  height: 2px;
  background: #fff;
  border-radius: 2px;
}

.close-btn span:first-child {
  transform: translate(-50%, -50%) rotate(45deg);
}

.close-btn span:last-child {
  transform: translate(-50%, -50%) rotate(-45deg);
}

.mobile-nav-list {
  flex: 1;
  list-style: none;
  margin: 0;
  padding: 16px 0;
  overflow-y: auto;
}

.mobile-nav-link {
  display: flex;
  align-items: center;
  padding: 16px 24px;
  color: rgba(255, 255, 255, 0.75);
  text-decoration: none;
  font-size: 16px;
  font-weight: 500;
  transition: all 0.25s ease;
  border-left: 3px solid transparent;
}

.mobile-nav-link:hover {
  color: #fff;
  background: rgba(255, 255, 255, 0.05);
  border-left-color: rgba(233, 69, 96, 0.5);
}

.mobile-nav-link.active {
  color: #fff;
  background: rgba(233, 69, 96, 0.15);
  border-left-color: #e94560;
}

.mobile-nav-footer {
  padding: 20px;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
}

.mobile-nav-footer .cta-button {
  width: 100%;
  padding: 14px 24px;
  font-size: 15px;
}

/* ========== TRANSITIONS ========== */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.slide-enter-active,
.slide-leave-active {
  transition: transform 0.3s ease;
}

.slide-enter-from,
.slide-leave-to {
  transform: translateX(-100%);
}

/* ========== RESPONSIVE: LARGE DESKTOP (1200px+) ========== */
@media (min-width: 1200px) {
  .header-container {
    padding: 0 48px;
  }

  .nav-link {
    padding: 12px 24px;
    font-size: 16px;
  }

  .cta-button {
    padding: 14px 32px;
    font-size: 15px;
  }
}

/* ========== RESPONSIVE: TABLET (768px - 1024px) ========== */
@media (max-width: 1024px) {
  .header-container {
    padding: 0 20px;
    gap: 16px;
  }

  .nav-link {
    padding: 8px 14px;
    font-size: 14px;
  }

  .cta-button {
    padding: 10px 20px;
    font-size: 13px;
  }

  .logo-text {
    font-size: 20px;
  }

  .logo-icon {
    font-size: 24px;
  }
}

/* ========== RESPONSIVE: MOBILE (<768px) ========== */
@media (max-width: 768px) {
  .header {
    height: 70px;
  }

  .header-container {
    padding: 0 16px;
  }

  .desktop-nav,
  .desktop-cta {
    display: none;
  }

  .menu-toggle {
    display: block;
  }

  .logo-text {
    font-size: 18px;
  }

  .logo-icon {
    font-size: 22px;
  }
}

/* ========== RESPONSIVE: SMALL MOBILE (<480px) ========== */
@media (max-width: 480px) {
  .header {
    height: 64px;
  }

  .header-container {
    padding: 0 12px;
  }

  .mobile-nav {
    width: 280px;
  }

  .logo-text {
    font-size: 16px;
  }

  .logo-icon {
    font-size: 20px;
  }

  .menu-toggle {
    width: 40px;
    height: 40px;
  }

  .mobile-nav-link {
    padding: 14px 20px;
    font-size: 15px;
  }
}

/* ========== LANDSCAPE MODE ========== */
@media (max-height: 500px) and (orientation: landscape) {
  .header {
    height: 56px;
  }

  .mobile-nav {
    width: 260px;
  }

  .mobile-nav-header {
    padding: 12px 16px;
  }

  .mobile-nav-link {
    padding: 10px 20px;
    font-size: 14px;
  }

  .mobile-nav-footer {
    padding: 12px 16px;
  }

  .mobile-nav-footer .cta-button {
    padding: 10px 20px;
    font-size: 14px;
  }
}
</style>
