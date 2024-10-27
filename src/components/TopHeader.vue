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
  margin-bottom: 40px;
  background: linear-gradient(to right, #e1f5fe, #b3e5fc);
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

h1 {
  font-family: "Roboto", sans-serif;
  font-size: 2.5rem;
  color: #333;
  margin: 0;
  text-shadow: 1px 1px 2px rgba(255, 255, 255, 0.8);
}
</style>
