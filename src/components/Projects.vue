<template>
	<!-- My Projects -->
    <section class="pb-5" id="projects">
        <h1 class="mt-5 mb-5 pb-4 text-center">My Projects</h1>
        
        <!-- Created a div that will contain the card decks (2 cards in a row) -->
        <!-- We will group our cards into 3 inside chunkProjects -->
        <!-- This will loop through each  -->
        <div v-for="(group, index) in chunkedProjects" :key="index" class="card-deck my-5 justify-content-center">
            <!-- We will display the individual card from the chunkedProjects -->
            <ProjectCard v-for="project in group" :key="project.id" :project="project" />            
    
        </div>
    </section>

</template>

<script setup>
    import { computed } from 'vue';

    import ProjectCard from './ProjectCard.vue';
    import projects from '../data/projects.json';

    const chunkSize = 3;

    const chunkedProjects = computed(()=> {
        const chunks = []

        for (let i = 0; i < projects.length; i += chunkSize) {
            chunks.push(projects.slice(i, i+ chunkSize));
        }

        return chunks;
    })
</script>