<script setup>
import { ref, onMounted } from 'vue';

const isMenuOpen = ref(false);
const isLoaded = ref(false);
const sections = [
  { id: 'accueil', label: 'Accueil' },
  { id: 'apropos', label: 'À Propos' },
  { id: 'competences', label: 'Compétences' },
  { id: 'projets', label: 'Projets' },
  { id: 'contact', label: 'Contact' }
];

onMounted(() => {
  setTimeout(() => {
    isLoaded.value = true;
  }, 500);
});

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
  <nav class="navbar" :class="{ 'loaded': isLoaded }">
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
        <li v-for="(section, index) in sections" :key="section.id" 
            :style="{ '--delay': `${index * 0.1}s` }">
          <a href="#" @click.prevent="scrollToSection(section.id)" class="nav-link">
            <span class="nav-text">{{ section.label }}</span>
            <span class="nav-background"></span>
          </a>
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
  transform: translateY(-100%);
  opacity: 0;
  transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1),
              opacity 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}

.navbar.loaded {
  transform: translateY(0);
  opacity: 1;
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

.nav-links li {
  opacity: 0;
  transform: translateY(20px);
  animation: fadeInUp 0.5s ease forwards;
  animation-delay: var(--delay);
}

.nav-link {
  color: #E5E7EB;
  text-decoration: none;
  font-weight: 500;
  position: relative;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  font-size: 1rem;
  display: block;
  perspective: 1000px;
  transform-style: preserve-3d;
  transition: transform 0.3s ease;
}

.nav-text {
  position: relative;
  z-index: 2;
  display: block;
  transition: transform 0.3s ease;
}

.nav-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(45deg, #60A5FA, #34D399);
  border-radius: 4px;
  opacity: 0;
  transform: translateZ(-1px);
  transition: opacity 0.3s ease;
}

.nav-link:hover {
  transform: translateZ(20px) rotateX(10deg);
}

.nav-link:hover .nav-text {
  transform: translateZ(30px);
}

.nav-link:hover .nav-background {
  opacity: 0.1;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.menu-toggle {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
  position: absolute;
  right: 1rem;
  transform: translateZ(0);
  transition: transform 0.3s ease;
}

.menu-toggle:hover {
  transform: translateZ(10px);
}

.hamburger {
  display: flex;
  flex-direction: column;
  gap: 6px;
  transform-style: preserve-3d;
}

.hamburger span {
  display: block;
  width: 25px;
  height: 2px;
  background: #E5E7EB;
  transition: all 0.3s ease;
  transform-origin: center;
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
  transition: all 0.3s ease;
  transform: translateZ(0);
}

.close-menu:hover {
  color: #60A5FA;
  transform: translateZ(10px) rotate(90deg);
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
