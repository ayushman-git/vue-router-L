<template>
  <h1>Jobs</h1>
  <div v-for="(job, index) in jobs" :key="index" class="job">
    <router-link
      :to="{ name: 'JobDetails', params: { id: job.id, somethingElse: 'Hi' } }"
    >
      <h2>{{ job.title }}</h2>
    </router-link>
  </div>
</template>

<script>
export default {
  name: "Jobs",
  data() {
    return {
      jobs: [],
    };
  },
  mounted() {
    this.fetchJobs();
  },
  methods: {
    async fetchJobs() {
      try {
        const rawData = await fetch("http://localhost:3001/jobs");
        const dataJson = await rawData.json();
        this.jobs = dataJson;
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>

<style scoped>
.job h2 {
  background: #f4f4f4;
  padding: 20px;
  border-radius: 10px;
  margin: 10px auto;
  max-width: 600px;
  cursor: pointer;
  color: #444;
}
.job h2:hover {
  background: #ddd;
}
.job a {
  text-decoration: none;
}
</style>