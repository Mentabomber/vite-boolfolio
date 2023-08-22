<script>

import axios from 'axios';
import ProjectCard from '../components/ProjectCard.vue';

export default {
  name: 'Projects',
  components: {
    ProjectCard
  },
  data: function(){
    return{
      projects: [],
      pages: []
    }
    },
  methods:{ loadPage(target) {

    if (target == null) return;

    this.loadProjects(target);
  },
  loadProjects(target) {
    axios.get(target)
     .then(response => {

        const data = response.data;
        // console.log(data);

        this.projects = data.projects.data;
        this.pages = data.projects.links;
      })
      .catch(error => {
        console.log(error);
       });
}
},
mounted (){

  this.loadProjects('http://localhost:8000/api/Project-index');
}
}
</script>
<template>
    <h1>HOME</h1>
    
    <h2>Projects</h2>
    <div class="row justify-content-between">

            <ProjectCard  v-for="project in projects" :key="project.id" :project="project"/>

    </div>

    <div class="pages row justify-content-center cursor-pointer">
        <div v-for="(page, index) in pages"
            :key="index"
            class="page col "
            :class="(page.active ? 'bg-white text-dark' : 'bg-secondary text-white')
                    + ' '
                    + (page.url == null ? 'd-none' : '')"
            v-html="page.label"

            role="button"

            @click="loadPage(page.url)">
        </div>
    </div>
</template>

