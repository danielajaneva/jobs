<template>
  <h1>Job Details Page</h1>
  <div v-if="job">
    <h2>{{ job.title }}</h2>
    <p>The job id is : {{ id }}</p>
    <p>{{ job.details }}</p>
  </div>
  <div v-else>
    <p>Loading job details...</p>
  </div>
</template>

<script>
export default {
  props: ["id"],
  //   accept the id as a prop instead of targeting in data
  //   for the above opt. you must set "params:true" at the routes
  //   data() {
  //     return {
  //       id: this.$route.params.id,
  //     };
  //   },
  data() {
    return {
      job: null,
    };
  },

  mounted() {
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.job = data))
      .catch((err) => console.log(err.message));
  },
};
</script>

<style></style>
