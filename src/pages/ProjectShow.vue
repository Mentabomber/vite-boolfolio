<script>
import axios from 'axios';

const API_URL = 'http://localhost:8000/api';

export default {
    name: 'ProjectShow',
    data() {
        return {
            project: {}
        }
    },
    mounted() {

        const projectId = this.$route.params.id;

        axios.get(API_URL + '/Project-show/' + projectId)
             .then(res => this.project = res.data.project)
             .catch(err => console.error(err));
    }
}
</script>
<template>
    <h1>{{ project.title }}</h1>
    <p>description: {{ project.description }}</p>
    <p>manager: {{ project.project_manager }}</p>
    <img :src="project.thumb" alt="">
    <h4>Go to 
        <router-link :to="{ name: 'home' }">HOME</router-link>
    </h4>
</template>

