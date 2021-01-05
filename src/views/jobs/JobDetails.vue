<template>
  <div v-if="job">
    <h1>{{ job.title }}</h1>
    <h3>{{ job.id }}</h3>
    <p>{{ job.details }}</p>
  </div>
</template>

<script>
export default {
  name: "JobDetails",
  props: ["id", "somethingElse"],
  data() {
    return {
      job: null,
    };
  },
  mounted() {
    this.fetchJob();
  },
  methods: {
    async fetchJob() {
      try {
        const rawData = await fetch(`http://localhost:3001/jobs/${this.id}`);
        const dataJson = await rawData.json();
        this.job = dataJson;
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>

<style scoped>
</style>