<template>
  <div
    class="habit-card"
    :style="{ background: progressBackground }"
    @click="incrementScore"
  >
    <div class="left">
      <h3>{{ name }}</h3>
      <p>🔥 Streak: {{ streak }}</p>
    </div>
    <div class="right">
      <p>Score: {{ score }}/{{ maxScore }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    name: String,
    score: Number,
    maxScore: Number,
    streak: Number,
  },
  computed: {
    progressBarWidth() {
      return (this.score / this.maxScore) * 100;
    },
    progressBackground() {
      const progressPercentage = this.progressBarWidth;
      return `linear-gradient(to right, #4caf50 ${progressPercentage}%, #d0d0d0 ${progressPercentage}%)`;
    },
  },
  methods: {
    incrementScore() {
      this.$emit("update:score", this.score + 1);
    },
  },
};
</script>

<style scoped>
.habit-card {
  border-radius: 10px;
  padding: 20px;
  margin: 10px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  max-width: 500px;
  transition: background-color 0.3s;
  cursor: pointer;
}

.left {
  flex: 1;
}

.right {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}
</style>
