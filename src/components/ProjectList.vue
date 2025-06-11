<template>
  <div class="container mt-5">
    <h2>Portfolio</h2>
    <div class="row">
      <div class="col-md-4" v-for="project in projects" :key="project.id">
        <div class="card mb-3">
          <img :src="project.image" class="card-img-top" v-if="project.image" />
          <div class="card-body">
            <h5 class="card-title">{{ project.title }}</h5>
            <p class="card-text">{{ project.description }}</p>
            <a :href="project.link" target="_blank" class="btn btn-primary">Link</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      projects: []
    };
  },
  mounted() {
    axios.get('http://localhost:8000/api/projects/')
      .then(response => {
        this.projects = response.data;
      })
      .catch(error => {
        console.error(error);
      });
  }
};
</script>
