<script>

  import axios from 'axios';

  export default {
    name: 'Projects',
    mounted (){
      axios.get('http://localhost:8000/api/Project-index')
        .then(response => {
          const data = response.data;
          console.log(data);
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
</script>

<template>
  Ciao
</template>

<style>

</style>