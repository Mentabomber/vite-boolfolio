<script>

  import axios from 'axios';

  export default {
    name: 'HelloWorld',
    mounted (){
      axios.get('http://localhost:8000/api/api')
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
  
</template>

<style>

</style>