<script setup>
import { ref, onMounted } from 'vue';
import SocialIcon from './SocialIcon.vue';

const skills = [
  'Ingénieur en informatique',
  'Développeur frontend',
  'Développeur backend',
  'Développeur fullstack'
];
const currentSkill = ref(0);
const showSkill = ref(true);

onMounted(() => {
  setInterval(() => {
    showSkill.value = false;
    setTimeout(() => {
      currentSkill.value = (currentSkill.value + 1) % skills.length;
      showSkill.value = true;
    }, 400); // temps de transition
  }, 2200);
});
</script>

<template>
  <div id="top-line" class="hero-container">
    <div class="hero-content">
      <h1 class="hero-title fade-in-up" style="--delay: 0.1s">Salut, moi c'est <span class="text-highlight-1">Fidiniaina</span></h1>
      <div class="skills-animated-wrapper">
        <transition name="fade-slide">
          <span v-if="showSkill" :key="currentSkill" class="skills-animated">{{ skills[currentSkill] }}</span>
        </transition>
      </div>
      <p class="hero-desc fade-in-up" style="--delay: 0.5s">Passionné par la création de sites et d'applications web modernes, je conçois des expériences numériques élégantes et performantes.</p>
      <div id="social" class="fade-in-up" style="--delay: 0.7s">
        <SocialIcon img="github" link="https://github.com/FIDYKELY" alt="github"/>
        <SocialIcon img="facebook" link="https://www.facebook.com/profile.php?id=100004683916160" alt="facebook"/>
        <SocialIcon img="linkedin" link="https://www.linkedin.com/in/fidy-niaina-107273319/" alt="linkedin"/>
      </div>
    </div>
    <div class="hero-img-wrapper">
      <img id="profile-img" src="../assets/graduation.png" alt="photo de graduation" />
    </div>
  </div>
</template>

<style scoped>
.hero-container {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  min-height: 80vh;
  width: 100%;
  padding: 4rem 1rem 4rem 1rem;
  gap: 3rem;
  text-align: left;
}

.hero-content {
  max-width: 500px;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
}

.skills-animated-wrapper {
  min-height: 2.2rem;
  margin-bottom: 0.5rem;
  margin-top: -0.5rem;
  position: relative;
  display: flex;
  align-items: center;
  height: 2.2rem;
}

.skills-animated {
  font-size: 1.3rem;
  font-weight: 600;
  color: #34D399;
  letter-spacing: 0.5px;
  background: linear-gradient(45deg, #60A5FA, #34D399);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  display: inline-block;
  white-space: nowrap;
}

.fade-slide-enter-active, .fade-slide-leave-active {
  transition: all 0.4s cubic-bezier(0.4,0,0.2,1);
}
.fade-slide-enter-from {
  opacity: 0;
  transform: translateY(20px);
}
.fade-slide-enter-to {
  opacity: 1;
  transform: translateY(0);
}
.fade-slide-leave-from {
  opacity: 1;
  transform: translateY(0);
}
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}

.fade-in-up {
  opacity: 0;
  transform: translateY(30px);
  animation: fadeInUp 0.7s cubic-bezier(0.4,0,0.2,1) forwards;
  animation-delay: var(--delay, 0s);
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

.hero-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  background: linear-gradient(45deg, #60A5FA, #34D399);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.hero-subtitle {
  font-size: 1.5rem;
  font-weight: 500;
  color: #60A5FA;
  margin-bottom: 1rem;
}

.hero-desc {
  font-size: 1.1rem;
  color: #E5E7EB;
  margin-bottom: 1.5rem;
}

#social {
  display: flex;
  justify-content: flex-start;
  gap: 1.5rem;
  margin-top: 1rem;
}

.hero-img-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 480px;
  height: 650px;
  border-radius: 2.5rem;
  overflow: hidden;
  box-shadow: 0 24px 64px rgba(52, 211, 153, 0.20), 0 8px 32px rgba(96, 165, 250, 0.15);
  background: linear-gradient(135deg, #60A5FA22 0%, #34D39922 100%);
  transition: width 0.3s, height 0.3s;
}

#profile-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 2.5rem;
  box-shadow: 0 4px 16px rgba(0,0,0,0.10);
}

@media (max-width: 1400px) {
  .hero-img-wrapper {
    width: 350px;
    height: 480px;
  }
}

@media (max-width: 1200px) {
  .hero-img-wrapper {
    width: 300px;
    height: 400px;
  }
}

@media (max-width: 900px) {
  .hero-container {
    flex-direction: column;
    gap: 2rem;
    text-align: center;
    padding: 2rem 1rem 2rem 1rem;
  }
  .hero-content {
    align-items: center;
    text-align: center;
  }
  #social {
    justify-content: center;
  }
  .hero-img-wrapper {
    width: 220px;
    height: 320px;
  }
}

@media (max-width: 600px) {
  .hero-img-wrapper {
    width: 140px;
    height: 200px;
  }
  .hero-title {
    font-size: 1.5rem;
  }
  .hero-subtitle {
    font-size: 1.1rem;
  }
}
</style>
