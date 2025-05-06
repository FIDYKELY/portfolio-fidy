<script setup>
import { ref } from 'vue';
import ProjectSingle from './ProjectSingle.vue';

let projects = ref([
    {
        name: "Le projet N°1",
        image: "project1.jpg",
        tags: "VueJS;PHP;HTML",
        description: "Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet.",
        tasks: "Lorem ipsum lorem ipsum dolor sit amet.;Lorem ipsum lorem ipsum dolor sit amet.;Lorem ipsum lorem ipsum dolor sit amet."
    },
    {
        name: "Le projet N°2",
        image: "project2.jpg",
        tags: "VueJS;PHP;HTML",
        description: "Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet.",
        tasks: "Lorem ipsum lorem ipsum dolor sit amet.;Lorem ipsum lorem ipsum dolor sit amet.;Lorem ipsum lorem ipsum dolor sit amet."
    },
    {
        name: "Le projet N°3",
        image: "project3.jpg",
        tags: "VueJS;PHP;HTML",
        description: "Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet.",
        tasks: "Lorem ipsum lorem ipsum dolor sit amet.;Lorem ipsum lorem ipsum dolor sit amet.;Lorem ipsum lorem ipsum dolor sit amet."
    },
    {
        name: "Le projet N°4",
        image: "logo.svg",
        tags: "VueJS;PHP;HTML",
        description: "Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet.",
        tasks: "Lorem ipsum lorem ipsum dolor sit amet.;Lorem ipsum lorem ipsum dolor sit amet.;Lorem ipsum lorem ipsum dolor sit amet."
    },
    {
        name: "Le projet N°5",
        image: "logo.svg",
        tags: "VueJS;PHP;HTML",
        description: "Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet.",
        tasks: "Lorem ipsum lorem ipsum dolor sit amet.;Lorem ipsum lorem ipsum dolor sit amet.;Lorem ipsum lorem ipsum dolor sit amet."
    },
    {
        name: "Le projet N°6",
        image: "logo.svg",
        tags: "VueJS;PHP;HTML",
        description: "Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet.",
        tasks: "Lorem ipsum lorem ipsum dolor sit amet.;Lorem ipsum lorem ipsum dolor sit amet.;Lorem ipsum lorem ipsum dolor sit amet."
    },
]);
</script>

<template>
    <div id="projects" class="projects-container">
        <h2 class="text-highlight-1 section-title">Quelques projets</h2>
        <div class="projects-grid">
            <ProjectSingle 
                v-for="(project, index) in projects" 
                :key="project.name" 
                :project="project" 
                :reverse="index % 2 === 0 ? false : true"
            />
        </div>
    </div>
</template>

<style scoped>
.projects-container {
    width: 100%;
    padding: 2rem 0;
    opacity: 0;
    animation: fadeIn 0.8s ease forwards;
    animation-delay: 0.4s;
}

.projects-grid {
    display: flex;
    flex-direction: column;
    gap: 4rem;
    margin-top: 2rem;
}

.section-title {
    font-size: 2rem;
    margin-bottom: 2rem;
    text-align: center;
    background: linear-gradient(45deg, #60A5FA, #34D399);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
}

@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@media (max-width: 768px) {
    .projects-container {
        padding: 1rem 0;
    }

    .projects-grid {
        gap: 2rem;
    }
}
</style>
