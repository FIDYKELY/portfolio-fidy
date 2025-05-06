<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const props = defineProps({
    project: {
        type: Object,
        required: true
    },
    reverse: {
        type: Boolean,
        required: false
    }
});

let fadeInElements = ref();

onMounted(() => {
    fadeInElements.value = Array.from(document.getElementsByClassName('fade-in'));
    document.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
    document.removeEventListener('scroll', handleScroll);
});

const handleScroll = () => {
    for(let i = 0; i < fadeInElements.value.length; i++) {
        const elem = fadeInElements.value[i];
        if(isElemVisible(elem)) {
            elem.style.opacity = '1';
            elem.style.transform = 'translateY(0)';
            fadeInElements.value.splice(i, 1);
        }
    }
};

const isElemVisible = (el) => {
    const rect = el.getBoundingClientRect();
    const elemTop = rect.top + 200;
    const elemBottom = rect.bottom;
    return elemTop < window.innerHeight && elemBottom >= 0;
};

const getProjectTags = () => {
    return props.project.tags.split(';');
};

const getProjectTasks = () => {
    return props.project.tasks.split(';');
};
</script>

<template>
    <div class="project" :class="{ 'reverse': reverse }">
        <div class="project-content fade-in">
            <div class="project-image">
                <img :src="`/src/assets/${project.image}`" :alt="project.name">
            </div>
            <div class="project-info">
                <h3 class="project-title">{{ project.name }}</h3>
                <div class="project-tags">
                    <span v-for="tag in getProjectTags()" :key="tag" class="tag">{{ tag }}</span>
                </div>
                <p class="project-description">{{ project.description }}</p>
                <ul class="project-tasks">
                    <li v-for="task in getProjectTasks()" :key="task">
                        <span class="task-icon">✓</span>
                        <span class="task-text">{{ task }}</span>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<style scoped>
.project {
    width: 100%;
    margin-bottom: 2rem;
    opacity: 0;
    transform: translateY(30px);
    transition: all 0.6s ease;
}

.project-content {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2rem;
    background: rgba(31, 41, 55, 0.5);
    border-radius: 1rem;
    padding: 2rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(96, 165, 250, 0.1);
}

.project-image {
    width: 100%;
    height: 300px;
    overflow: hidden;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.project-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
}

.project-image:hover img {
    transform: scale(1.05);
}

.project-info {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

.project-title {
    font-size: 1.5rem;
    font-weight: 600;
    color: #60A5FA;
    margin: 0;
}

.project-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
}

.tag {
    background: rgba(96, 165, 250, 0.1);
    color: #60A5FA;
    padding: 0.25rem 0.75rem;
    border-radius: 1rem;
    font-size: 0.875rem;
    font-weight: 500;
}

.project-description {
    color: #E5E7EB;
    line-height: 1.6;
    margin: 0;
}

.project-tasks {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
}

.project-tasks li {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    color: #E5E7EB;
}

.task-icon {
    color: #34D399;
    font-weight: bold;
}

.task-text {
    font-size: 0.875rem;
}

.reverse .project-content {
    direction: rtl;
}

.reverse .project-info {
    direction: ltr;
}

.fade-in {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.6s ease, transform 0.6s ease;
}

@media (max-width: 768px) {
    .project-content {
        grid-template-columns: 1fr;
        gap: 1rem;
        padding: 1rem;
    }

    .project-image {
        height: 200px;
    }

    .reverse .project-content {
        direction: ltr;
    }
}
</style>