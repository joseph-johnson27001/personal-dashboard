<template>
  <div class="header">
    <h1>{{ name }}</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "Joe Johnson",
    };
  },
};
</script>

<style scoped>
.header {
  text-align: center;
  padding: 30px;
}

h1 {
  font-family: "Roboto", sans-serif;
  font-size: 2.5rem;
  color: #333;
  margin: 0;
  text-shadow: 1px 1px 2px rgba(255, 255, 255, 0.8);
}
</style>
