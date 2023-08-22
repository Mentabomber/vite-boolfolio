<script>

  import axios from 'axios';

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
   <div class="col-1 border"> {{ project.title }} <span>
    {{ project.description }}
    </span>
   </div>
</template>

<style>
.card{
  width: 250px;
}
</style>