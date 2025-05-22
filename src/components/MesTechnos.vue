<script setup>

</script>

<template>
    <div id="skills">
        <h2 class="text-highlight-1 section-title">Mes technos préférées</h2>
        <div id="icons-list">
            <div class="techno-container"><i class="techno-icon devicon-html5-plain"></i> <br/> <span>HTML</span></div>
            <div class="techno-container"><i class="techno-icon devicon-css3-plain"></i> <br/> <span>CSS</span></div>
            <div class="techno-container"><i class="techno-icon devicon-javascript-plain"></i> <br/> <span>JS</span></div>
            <div class="techno-container"><i class="techno-icon devicon-mysql-original"></i> <br/> <span>SQL</span></div>
            <div class="techno-container"><i class="techno-icon devicon-php-plain"></i> <br/> <span>PHP</span></div>
            <div class="techno-container"><i class="techno-icon devicon-wordpress-plain"></i> <br/> <span>Wordpress</span></div>
            <div class="techno-container"><i class="techno-icon devicon-photoshop-plain"></i> <br/> <span>Photoshop</span></div>
            <div class="techno-container"><i class="techno-icon devicon-blender-original"></i> <br/> <span>Blender</span></div>
            <div class="techno-container"><i class="techno-icon devicon-unity-plain"></i> <br/> <span>Unity</span></div>
            <div class="techno-container"><i class="techno-icon devicon-git-plain"></i> <br/> <span>Git</span></div>
            <div class="techno-container"><i class="techno-icon devicon-graphql-plain"></i> <br/> <span>GraphQL</span></div>
            <div class="techno-container"><i class="techno-icon devicon-bootstrap-plain"></i> <br/> <span>Bootstrap</span></div>
            <div class="techno-container"><i class="techno-icon devicon-tailwindcss-original"></i> <br/> <span>Tailwind</span></div>
            <div class="techno-container"><i class="techno-icon devicon-jquery-plain"></i> <br/> <span>jQuery</span></div>
            <div class="techno-container"><i class="techno-icon devicon-vuejs-plain"></i> <br/> <span>VueJS</span></div>
            <div class="techno-container"><i class="techno-icon devicon-symfony-original"></i> <br/> <span>Symfony</span></div>
        </div>
    </div>
</template>

<style scoped>
    #skills {
        margin-top: 60px;
    }

    #icons-list {
        display: grid;
        grid-template-columns: repeat(8, 1fr);
        grid-template-rows: repeat(2, 1fr);
        grid-column-gap: 5px;
        grid-row-gap: 50px;
        margin-top: 35px;
    }

    .techno-container {
        text-align: center;
        color: var(--vt-c-custom-text-1); 
        transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        transform: translateZ(0);
        will-change: transform;
        position: relative;
        overflow: hidden;
    }

    .techno-container::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(45deg, rgba(96, 165, 250, 0.1), rgba(52, 211, 153, 0.1));
        opacity: 0;
        transition: opacity 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        z-index: -1;
    }

    .techno-container:hover {
        transform: translateZ(20px) scale(1.1);
        color: var(--vt-c-custom-text-2);
    }

    .techno-container:hover::before {
        opacity: 1;
    }

    .techno-container span {
        font-weight: bold;
        display: block;
        margin-top: 0.5rem;
        transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .techno-container:hover span {
        transform: translateY(-5px);
    }

    .techno-icon {
        font-size: 80px;
        margin: 0 auto;
        color: var(--vt-c-custom-text-1);
        transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        transform: translateZ(0);
        will-change: transform;
    }

    .techno-container:hover .techno-icon {
        color: var(--vt-c-custom-text-2);
        transform: translateZ(30px) scale(1.1);
    }

    @media screen and (max-width: 905px) {
        #icons-list {
            grid-template-columns: repeat(4, 1fr);
            grid-template-rows: repeat(4, 1fr);
            grid-column-gap: 5px;
            grid-row-gap: 40px;
        }
    }

    @media screen and (max-width: 450px) {
        #icons-list {
            grid-template-columns: repeat(2, 1fr);
            grid-template-rows: repeat(8, 1fr);
            grid-column-gap: 5px;
            grid-row-gap: 20px;
        }
    }
</style>