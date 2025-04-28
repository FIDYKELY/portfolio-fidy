<script setup>
import PageTitle from '@/components/PageTitle.vue';
import AboutMe from '@/components/AboutMe.vue';
import MesTechnos from '@/components/MesTechnos.vue';
import MesXp from '@/components/MesXp.vue';
import MesProjets from '@/components/MesProjets.vue';
</script>

<template>
  <div class="portfolio-container">
    <section id="accueil" class="section">
      <PageTitle/>
    </section>

    <section id="apropos" class="section">
      <AboutMe/>
    </section>

    <section id="competences" class="section">
      <MesTechnos/>
    </section>

    <section id="projets" class="section">
      <div class="section-content">
        <h2 class="section-title">Mon Parcours & Projets</h2>
        <div class="experience-projects-container">
          <MesXp/>
          <MesProjets/>
        </div>
      </div>
    </section>

    <section id="contact" class="section">
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
  padding-top: 80px;
  background-color: #111827;
  color: #E5E7EB;
}

.section {
  min-height: 100vh;
  padding: 4rem 2rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.section:nth-child(even) {
  background-color: #1F2937;
}

.section-content {
  max-width: 1200px;
  margin: 0 auto;
  width: 100%;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 2rem;
  text-align: center;
  background: linear-gradient(45deg, #60A5FA, #34D399);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.experience-projects-container {
  display: grid;
  gap: 2rem;
  margin-top: 2rem;
}

.contact-container {
  text-align: center;
  padding: 2rem;
  background-color: #1F2937;
  border-radius: 1rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.contact-container p {
  color: #E5E7EB;
  font-size: 1.2rem;
  margin-bottom: 1.5rem;
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
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.contact-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(96, 165, 250, 0.3);
}

@media (max-width: 768px) {
  .section {
    padding: 3rem 1rem;
  }

  .section-title {
    font-size: 2rem;
  }
}
</style>
