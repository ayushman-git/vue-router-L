<template>
  <div>
    <pre>
      <code>
        {{ id }} {{somethingElse}}
        </code>
      </pre>
  </div>
</template>

<script>
export default {
  name: "JobDetails",
  props: ["id", "somethingElse"],
};
</script>

<style scoped>
</style>