<template>
  <div
    class="habit-card"
    :style="{ background: progressBackground }"
    @click="incrementScore"
  >
    <div class="left">
      <h3>{{ name }}</h3>
      <p class="streak"><i class="fas fa-fire"></i> {{ streak }}</p>
    </div>
    <div class="right">
      <p>{{ score }}/{{ maxScore }}</p>
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
  padding: 25px 10px;
  margin: 10px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
  width: 100%;
  max-width: 500px;
  transition: background-color 0.3s;
  cursor: pointer;
  border: 1px solid white;
}

h3 {
  font-weight: 100;
}

.left {
  flex: 1;
}

.right {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}

.streak {
  position: absolute;
  top: -5px;
  right: 10px;
  font-size: 0.9rem;
  display: flex;
  align-items: center;
}

.streak i {
  margin-right: 4px; /* Adds space between icon and streak number */
  color: orange; /* Change icon color to orange */
}
</style>
