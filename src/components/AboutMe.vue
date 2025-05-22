<template>
    <div id="about-me" class="section fade-in">
        <div class="section-content">
            <h2 class="section-title">Qui suis-je ?</h2>
            <p class="default-text">Je suis un <span class="text-highlight-2">développeur web</span> passionné par
                la création de site web et d'application web innovante.
            </p>
            <h3 class="section-title">Expériences Professionnelles</h3>
            <ul class="list">
                <li class="list-item">2024-2025 : Stage pré-embauche Trois mois au sein de l'Atout Service en tant que développeur Magento</li>
                <li class="list-item">2024 : Stage Trois mois au sein de Profily en tant que développeur JS (Vue JS, node JS)</li>
            </ul>
            <h3 class="section-title">Education</h3>
            <ul class="list">
                <li class="list-item">2024 : E.S.M.I.A Master 2 M.I.A.G.E</li>
                <li class="list-item">2022-2023 : E.S.M.I.A Master de méthodes informatiques appliquées à la gestion des entreprises (Master 1 M.I.A.G.E)</li>
                <li class="list-item">2018-2021 : E.S.M.I.A Licence en Sciences et Technologies, Parcours Informatique, Risques et Décision</li>
            </ul>
        </div>
    </div>
</template>

#about-me {
    opacity: 0;
    transform: translateY(30px) scale(0.98);
    transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
    will-change: transform, opacity;
}

#about-me.visible {
    opacity: 1;
    transform: translateY(0) scale(1);
}

.section-content {
    transform: translateZ(0);
    transition: transform 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    will-change: transform;
}

#about-me:hover .section-content {
    transform: translateZ(20px);
}

.section-title {
    position: relative;
    display: inline-block;
    transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    will-change: transform;
}

#about-me:hover .section-title {
    transform: translateZ(30px);
}

.default-text {
    transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    will-change: transform;
}

#about-me:hover .default-text {
    transform: translateZ(20px);
}

.list {
    list-style: none;
    padding: 0;
    margin: 1rem 0;
}

.list-item {
    position: relative;
    padding: 0.5rem 0;
    padding-left: 1.5rem;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    will-change: transform;
}

.list-item::before {
    content: '•';
    position: absolute;
    left: 0;
    color: var(--vt-c-custom-text-2);
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

#about-me:hover .list-item {
    transform: translateX(10px);
}

#about-me:hover .list-item::before {
    transform: scale(1.5);
    color: var(--vt-c-custom-text-1);
}

