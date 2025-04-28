<script setup>
import { ref } from 'vue';

const isMenuOpen = ref(false);
const sections = [
  { id: 'accueil', label: 'Accueil' },
  { id: 'apropos', label: 'À Propos' },
  { id: 'competences', label: 'Compétences' },
  { id: 'projets', label: 'Projets' },
  { id: 'contact', label: 'Contact' }
];

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId);
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' });
    isMenuOpen.value = false;
  }
};
</script>

<template>
  <nav class="navbar">
    <div class="nav-links" :class="{ 'active': isMenuOpen }">
      <button class="menu-toggle" @click="toggleMenu" :aria-expanded="isMenuOpen">
        <span class="hamburger" :class="{ 'active': isMenuOpen }">
          <span></span>
          <span></span>
          <span></span>
        </span>
      </button>
      <button class="close-menu" @click="toggleMenu" aria-label="Fermer le menu">
        <span class="close-icon">×</span>
      </button>
      <ul>
        <li v-for="section in sections" :key="section.id">
          <a href="#" @click.prevent="scrollToSection(section.id)">{{ section.label }}</a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background: rgba(17, 24, 39, 0.98);
  backdrop-filter: blur(10px);
  padding: 1rem 2rem;
  z-index: 1000;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
  height: 70px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.nav-links {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  max-width: 800px;
}

.nav-links ul {
  display: flex;
  gap: 2rem;
  list-style: none;
  margin: 0;
  padding: 0;
}

.nav-links a {
  color: #E5E7EB;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
  position: relative;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  font-size: 1rem;
}

.nav-links a::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 2px;
  background: linear-gradient(45deg, #60A5FA, #34D399);
  transition: width 0.3s ease;
}

.nav-links a:hover {
  color: #60A5FA;
  background: rgba(96, 165, 250, 0.1);
}

.nav-links a:hover::after {
  width: 80%;
}

.menu-toggle {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
  position: absolute;
  right: 1rem;
}

.hamburger {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.hamburger span {
  display: block;
  width: 25px;
  height: 2px;
  background: #E5E7EB;
  transition: all 0.3s ease;
}

.close-menu {
  display: none;
  background: none;
  border: none;
  color: #E5E7EB;
  font-size: 2rem;
  cursor: pointer;
  padding: 0.5rem;
  position: absolute;
  top: 1rem;
  right: 1rem;
  transition: color 0.3s ease;
}

.close-menu:hover {
  color: #60A5FA;
}

@media (max-width: 768px) {
  .menu-toggle {
    display: block;
  }

  .close-menu {
    display: block;
  }

  .nav-links {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: rgba(17, 24, 39, 0.98);
    padding: 4rem 1rem 1rem;
    transform: translateX(-100%);
    opacity: 0;
    transition: all 0.3s ease;
    visibility: hidden;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .nav-links.active {
    transform: translateX(0);
    opacity: 1;
    visibility: visible;
  }

  .nav-links ul {
    flex-direction: column;
    gap: 1.5rem;
    text-align: center;
    margin-top: 2rem;
  }

  .nav-links a {
    display: block;
    padding: 0.75rem 1rem;
    font-size: 1.2rem;
  }

  .hamburger.active span:first-child {
    transform: rotate(45deg) translate(8px, 8px);
  }

  .hamburger.active span:nth-child(2) {
    opacity: 0;
  }

  .hamburger.active span:last-child {
    transform: rotate(-45deg) translate(7px, -7px);
  }
}
</style>
