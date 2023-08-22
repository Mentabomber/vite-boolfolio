<script>

  // import axios from 'axios';

  export default {
    name: 'ProjectCard',
    props: {
      project: {
        type: Object,
        required: true
      }
    },
  }
</script>

<template>
   <div class="card col-2 border justify-content-between"> 
    <h3>
      {{ project.title }} 
    </h3>
    <span>
      {{ project.description }}
    </span>
    <br><br>
    <span>
      Go to  
      <router-link
      :to="{ 
          name: 'Project-index',
          params: { id: project.id }
      }"
      >
      Project
    </router-link></span>
   
   </div>
</template>

<style>
.card{

  padding: 10px;
}

</style>