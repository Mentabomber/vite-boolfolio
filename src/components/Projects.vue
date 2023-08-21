<script>

  import axios from 'axios';
  import ProjectCard from './ProjectCard.vue';

  export default {
    name: 'Projects',
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
        console.log(data);

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

  <h1>Projects</h1>
  <ul>
    <li v-for="project in projects" :key="project.id">
      <a href="">{{ project.id }} {{ project.title }}</a>

      <ProjectCard  />
      
    </li>
  </ul>

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

<style>
ul {
  list-style: none;
}
.page {

width: 50px;
}

a{
  text-decoration: none;
}
</style>