<template>
    <h1>{{ project.title }}</h1>
    <p>code: {{ project.description }}</p>
    <p>weight: {{ project.project_manager }}</p>
    <img :src="project.thumb" alt="">
</template>

<script>
import axios from 'axios';

const API_URL = 'http://localhost:8000/api/v1';

export default {
    name: 'ProjectShow',
    data() {
        return {
            project: {}
        }
    },
    mounted() {

        const projectId = this.$route.params.id;

        axios.get(API_URL + '/project-show/' + projectId)
             .then(res => this.project = res.data.project)
             .catch(err => console.error(err));
    }
}
</script>