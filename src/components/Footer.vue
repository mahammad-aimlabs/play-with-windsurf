<script setup>
import { ref } from 'vue'

const currentYear = new Date().getFullYear()

const footerLinks = ref([
  {
    title: 'Product',
    links: [
      { name: 'Features', href: '#services' },
      { name: 'Pricing', href: '#' },
      { name: 'Integrations', href: '#' },
      { name: 'Changelog', href: '#' }
    ]
  },
  {
    title: 'Company',
    links: [
      { name: 'About', href: '#about' },
      { name: 'Blog', href: '#' },
      { name: 'Careers', href: '#' },
      { name: 'Press', href: '#' }
    ]
  },
  {
    title: 'Resources',
    links: [
      { name: 'Documentation', href: '#' },
      { name: 'Help Center', href: '#' },
      { name: 'Community', href: '#' },
      { name: 'API Reference', href: '#' }
    ]
  },
  {
    title: 'Legal',
    links: [
      { name: 'Privacy', href: '#' },
      { name: 'Terms', href: '#' },
      { name: 'Cookie Policy', href: '#' },
      { name: 'Licenses', href: '#' }
    ]
  }
])

const socialLinks = ref([
  { name: 'Twitter', icon: '𝕏', href: '#' },
  { name: 'GitHub', icon: '⌘', href: '#' },
  { name: 'LinkedIn', icon: 'in', href: '#' },
  { name: 'Discord', icon: '◈', href: '#' }
])
</script>

<template>
  <footer class="footer">
    <div class="footer-container">
      <!-- Top Section -->
      <div class="footer-top">
        <!-- Brand Column -->
        <div class="footer-brand">
          <a href="#" class="logo">
            <span class="logo-icon">◆</span>
            <span class="logo-text">MyBrand</span>
          </a>
          <p class="brand-description">
            Building the future of digital experiences. 
            Join us on our mission to empower creators worldwide.
          </p>
          <div class="social-links">
            <a 
              v-for="social in socialLinks" 
              :key="social.name"
              :href="social.href"
              class="social-link"
              :aria-label="social.name"
            >
              {{ social.icon }}
            </a>
          </div>
        </div>

        <!-- Links Columns -->
        <div class="footer-links">
          <div v-for="column in footerLinks" :key="column.title" class="link-column">
            <h4 class="column-title">{{ column.title }}</h4>
            <ul class="link-list">
              <li v-for="link in column.links" :key="link.name">
                <a :href="link.href" class="footer-link">{{ link.name }}</a>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <!-- Divider -->
      <div class="footer-divider"></div>

      <!-- Bottom Section -->
      <div class="footer-bottom">
        <p class="copyright">
          © {{ currentYear }} MyBrand. All rights reserved.
        </p>
        <div class="bottom-links">
          <a href="#" class="bottom-link">Privacy Policy</a>
          <span class="separator">•</span>
          <a href="#" class="bottom-link">Terms of Service</a>
          <span class="separator">•</span>
          <a href="#" class="bottom-link">Cookies</a>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
/* ========== BASE FOOTER ========== */
.footer {
  width: 100%;
  background: linear-gradient(180deg, #0f0f1a 0%, #0a0a12 100%);
  color: #fff;
  border-top: 1px solid rgba(255, 255, 255, 0.08);
}

.footer-container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 80px 24px 40px;
}

/* ========== TOP SECTION ========== */
.footer-top {
  display: grid;
  grid-template-columns: 1.5fr 2fr;
  gap: 80px;
  margin-bottom: 60px;
}

/* ========== BRAND COLUMN ========== */
.footer-brand {
  max-width: 320px;
}

.logo {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  text-decoration: none;
  margin-bottom: 20px;
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

.brand-description {
  font-size: 15px;
  color: rgba(255, 255, 255, 0.6);
  line-height: 1.7;
  margin-bottom: 24px;
}

/* ========== SOCIAL LINKS ========== */
.social-links {
  display: flex;
  gap: 12px;
}

.social-link {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(255, 255, 255, 0.08);
  border-radius: 10px;
  color: rgba(255, 255, 255, 0.7);
  text-decoration: none;
  font-size: 16px;
  font-weight: 600;
  transition: all 0.25s ease;
}

.social-link:hover {
  background: rgba(233, 69, 96, 0.2);
  color: #e94560;
  transform: translateY(-2px);
}

/* ========== LINKS SECTION ========== */
.footer-links {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 40px;
}

.column-title {
  font-size: 14px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1px;
  color: #fff;
  margin-bottom: 20px;
}

.link-list {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.footer-link {
  color: rgba(255, 255, 255, 0.6);
  text-decoration: none;
  font-size: 14px;
  transition: all 0.25s ease;
  display: inline-block;
}

.footer-link:hover {
  color: #e94560;
  transform: translateX(4px);
}

/* ========== DIVIDER ========== */
.footer-divider {
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.1), transparent);
  margin-bottom: 30px;
}

/* ========== BOTTOM SECTION ========== */
.footer-bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 20px;
}

.copyright {
  font-size: 14px;
  color: rgba(255, 255, 255, 0.5);
}

.bottom-links {
  display: flex;
  align-items: center;
  gap: 12px;
}

.bottom-link {
  font-size: 14px;
  color: rgba(255, 255, 255, 0.5);
  text-decoration: none;
  transition: color 0.25s ease;
}

.bottom-link:hover {
  color: #e94560;
}

.separator {
  color: rgba(255, 255, 255, 0.3);
}

/* ========== RESPONSIVE: TABLET ========== */
@media (max-width: 1024px) {
  .footer-container {
    padding: 60px 24px 30px;
  }

  .footer-top {
    grid-template-columns: 1fr;
    gap: 50px;
  }

  .footer-brand {
    max-width: 100%;
    text-align: center;
  }

  .social-links {
    justify-content: center;
  }

  .footer-links {
    grid-template-columns: repeat(4, 1fr);
  }
}

/* ========== RESPONSIVE: MOBILE ========== */
@media (max-width: 768px) {
  .footer-container {
    padding: 50px 20px 30px;
  }

  .footer-top {
    gap: 40px;
    margin-bottom: 40px;
  }

  .footer-links {
    grid-template-columns: repeat(2, 1fr);
    gap: 30px;
  }

  .footer-bottom {
    flex-direction: column;
    text-align: center;
  }
}

/* ========== RESPONSIVE: SMALL MOBILE ========== */
@media (max-width: 480px) {
  .footer-container {
    padding: 40px 16px 24px;
  }

  .footer-links {
    grid-template-columns: 1fr 1fr;
    gap: 24px;
  }

  .column-title {
    font-size: 13px;
    margin-bottom: 14px;
  }

  .footer-link {
    font-size: 13px;
  }

  .link-list {
    gap: 10px;
  }

  .social-links {
    gap: 10px;
  }

  .social-link {
    width: 36px;
    height: 36px;
    font-size: 14px;
  }

  .logo-text {
    font-size: 20px;
  }

  .logo-icon {
    font-size: 24px;
  }

  .brand-description {
    font-size: 14px;
  }

  .copyright,
  .bottom-link {
    font-size: 13px;
  }

  .bottom-links {
    gap: 8px;
  }
}
</style>
