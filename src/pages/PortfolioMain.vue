<script setup>
import { ref, onMounted } from 'vue';
import PageTitle from '@/components/PageTitle.vue';
import AboutMe from '@/components/AboutMe.vue';
import MesTechnos from '@/components/MesTechnos.vue';
import MesXp from '@/components/MesXp.vue';
import MesProjets from '@/components/MesProjets.vue';

const isLoaded = ref(false);
const currentSection = ref('accueil');

onMounted(() => {
  setTimeout(() => {
    isLoaded.value = true;
  }, 500);

  // Observer pour les animations au scroll
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');
        currentSection.value = entry.target.id;
      }
    });
  }, { threshold: 0.3 });

  document.querySelectorAll('.section').forEach(section => {
    observer.observe(section);
  });
});
</script>

<template>
  <div class="portfolio-container" :class="{ 'loaded': isLoaded }">
    <div class="cursor"></div>
    <div class="cursor-follower"></div>

    <section id="accueil" class="section" :class="{ 'visible': currentSection === 'accueil' }">
      <div class="section-content">
        <PageTitle/>
      </div>
    </section>

    <section id="apropos" class="section" :class="{ 'visible': currentSection === 'apropos' }">
      <div class="section-content">
        <AboutMe/>
      </div>
    </section>

    <section id="competences" class="section" :class="{ 'visible': currentSection === 'competences' }">
      <div class="section-content">
        <MesTechnos/>
      </div>
    </section>

    <section id="projets" class="section" :class="{ 'visible': currentSection === 'projets' }">
      <div class="section-content">
        <h2 class="section-title">Mon Parcours & Projets</h2>
        <div class="experience-projects-container">
          <div class="experience-section">
            <MesXp/>
          </div>
          <div class="projects-section">
            <MesProjets/>
          </div>
        </div>
      </div>
    </section>

    <section id="contact" class="section" :class="{ 'visible': currentSection === 'contact' }">
      <div class="section-content">
        <h2 class="section-title">Contact</h2>
        <div class="contact-container">
          <p>Vous souhaitez me contacter ? N'hésitez pas !</p>
          <a href="mailto:votre-email@example.com" class="contact-button">
            Me contacter
          </a>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.portfolio-container {
  padding-top: 70px;
  background-color: #111827;
  color: #E5E7EB;
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.6s ease, transform 0.6s ease;
  width: 100vw;
  margin: 0;
  padding: 0;
  overflow-x: hidden;
  position: relative;
}

.cursor {
  width: 8px;
  height: 8px;
  background: #60A5FA;
  border-radius: 50%;
  position: fixed;
  pointer-events: none;
  z-index: 9999;
  transition: transform 0.2s ease;
}

.cursor-follower {
  width: 40px;
  height: 40px;
  background: rgba(96, 165, 250, 0.1);
  border: 1px solid #60A5FA;
  border-radius: 50%;
  position: fixed;
  pointer-events: none;
  z-index: 9998;
  transition: transform 0.4s ease, width 0.4s ease, height 0.4s ease;
}

.portfolio-container.loaded {
  opacity: 1;
  transform: translateY(0);
}

.section {
  min-height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: relative;
  overflow: hidden;
  perspective: 1000px;
  margin: 0;
  padding: 0;
  opacity: 0;
  transform: translateY(50px);
  transition: opacity 0.8s ease, transform 0.8s ease;
}

.section.visible {
  opacity: 1;
  transform: translateY(0);
}

.section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(45deg, rgba(96, 165, 250, 0.1), rgba(52, 211, 153, 0.1));
  transform: translateZ(-1px);
  opacity: 0;
  transition: opacity 0.5s ease;
}

.section:hover::before {
  opacity: 1;
}

.section:nth-child(even) {
  background-color: #1F2937;
}

.section-content {
  width: 100vw;
  max-width: 100vw;
  margin: 0;
  padding: 0;
  opacity: 0;
  transform: translateY(30px);
  animation: fadeInUp 0.8s ease forwards;
  animation-delay: calc(var(--section-index, 0) * 0.2s);
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 2rem;
  text-align: center;
  background: linear-gradient(45deg, #60A5FA, #34D399);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  transform: translateZ(0);
  transition: transform 0.3s ease;
  padding: 0 1rem;
  position: relative;
  overflow: hidden;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(45deg, #60A5FA, #34D399);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.6s ease;
}

.section.visible .section-title::after {
  transform: scaleX(1);
}

.section-title:hover {
  transform: translateZ(20px);
}

.experience-projects-container {
  display: grid;
  grid-template-columns: 1fr;
  gap: 2rem;
  margin-top: 2rem;
  transform-style: preserve-3d;
  perspective: 1000px;
  padding: 0 1rem;
  width: 100%;
  max-width: 1200px;
  margin: 2rem auto;
}

.experience-section,
.projects-section {
  width: 100%;
  opacity: 0;
  transform: translateY(30px);
  animation: fadeInUp 0.8s ease forwards;
}

.experience-section {
  animation-delay: 0.2s;
}

.projects-section {
  animation-delay: 0.4s;
}

.contact-container {
  text-align: center;
  padding: 3rem 1rem;
  background-color: #1F2937;
  border-radius: 0;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transform: translateZ(0);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  margin: 0;
  width: 100%;
  position: relative;
  overflow: hidden;
}

.contact-container::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(45deg, #60A5FA, #34D399);
  opacity: 0;
  transition: opacity 0.3s ease;
  z-index: 0;
}

.contact-container:hover::before {
  opacity: 0.1;
}

.contact-container p {
  color: #E5E7EB;
  font-size: 1.2rem;
  margin-bottom: 1.5rem;
  transform: translateZ(0);
  transition: transform 0.3s ease;
  padding: 0 1rem;
  position: relative;
  z-index: 1;
}

.contact-container:hover p {
  transform: translateZ(30px);
}

.contact-button {
  display: inline-block;
  padding: 1rem 2rem;
  background: linear-gradient(45deg, #60A5FA, #34D399);
  color: white;
  text-decoration: none;
  border-radius: 30px;
  font-weight: 600;
  margin-top: 1rem;
  transition: all 0.3s ease;
  transform: translateZ(0);
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  position: relative;
  z-index: 1;
  overflow: hidden;
}

.contact-button::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(45deg, #34D399, #60A5FA);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.contact-button:hover::before {
  opacity: 1;
}

.contact-button:hover {
  transform: translateZ(30px) scale(1.05);
  box-shadow: 0 8px 20px rgba(96, 165, 250, 0.3);
}

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

@media (max-width: 768px) {
  .section {
    padding: 0;
  }

  .section-content {
    padding: 0;
  }

  .section-title {
    font-size: 2rem;
    padding: 0 1rem;
  }

  .contact-container {
    padding: 2rem 1rem;
  }

  .experience-projects-container {
    padding: 0 1rem;
  }
}

@media (min-width: 1024px) {
  .experience-projects-container {
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
  }
}
</style>

<script>
// Ajout du suivi du curseur personnalisé
document.addEventListener('DOMContentLoaded', () => {
  const cursor = document.querySelector('.cursor');
  const follower = document.querySelector('.cursor-follower');

  document.addEventListener('mousemove', (e) => {
    cursor.style.transform = `translate(${e.clientX - 4}px, ${e.clientY - 4}px)`;
    follower.style.transform = `translate(${e.clientX - 20}px, ${e.clientY - 20}px)`;
  });

  document.addEventListener('mousedown', () => {
    cursor.style.transform += ' scale(0.8)';
    follower.style.transform += ' scale(0.8)';
  });

  document.addEventListener('mouseup', () => {
    cursor.style.transform = cursor.style.transform.replace(' scale(0.8)', '');
    follower.style.transform = follower.style.transform.replace(' scale(0.8)', '');
  });

  document.querySelectorAll('a, button').forEach(element => {
    element.addEventListener('mouseenter', () => {
      follower.style.width = '60px';
      follower.style.height = '60px';
    });

    element.addEventListener('mouseleave', () => {
      follower.style.width = '40px';
      follower.style.height = '40px';
    });
  });
});
</script>
