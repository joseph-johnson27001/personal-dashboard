<template>
  <div id="app">
    <div class="container">
      <TopHeader />
      <div class="dashboard">
        <HabitCard
          v-for="(habit, index) in habits"
          :key="index"
          :name="habit.name"
          :score="habit.score"
          :maxScore="habit.maxScore"
          :streak="habit.streak"
          @update:score="updateScore(index, $event)"
        />
      </div>
    </div>
  </div>
</template>

<script>
import TopHeader from "./components/TopHeader.vue";
import HabitCard from "./components/HabitCard.vue";

export default {
  components: {
    TopHeader,
    HabitCard,
  },
  data() {
    return {
      habits: [
        {
          name: "Fitness",
          score: 0,
          maxScore: 100,
          streak: 0,
          lastUpdated: null,
        },
        {
          name: "Mental Wellness",
          score: 0,
          maxScore: 100,
          streak: 0,
          lastUpdated: null,
        },
        {
          name: "Coding Progress",
          score: 0,
          maxScore: 100,
          streak: 0,
          lastUpdated: null,
        },
        {
          name: "Fasting",
          score: 0,
          maxScore: 30,
          streak: 0,
          lastUpdated: null,
        },
        {
          name: "Low Sugar Intake",
          score: 0,
          maxScore: 30,
          streak: 0,
          lastUpdated: null,
        },
        {
          name: "Low Alcohol Intake",
          score: 0,
          maxScore: 30,
          streak: 0,
          lastUpdated: null,
        },
      ],
    };
  },
  methods: {
    updateScore(index, newScore) {
      this.habits[index].score = newScore;

      const today = new Date().toISOString().split("T")[0];
      if (this.habits[index].lastUpdated === today) {
        this.habits[index].streak++;
      } else {
        this.habits[index].streak = 1;
      }
      this.habits[index].lastUpdated = today;
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

* {
  box-sizing: border-box;
  font-family: "Roboto", sans-serif;
}

body {
  margin: 0;
  background-color: #f4f8fb; /* Soft background for the entire page */
}

.container {
  max-width: 1200px;
  background: linear-gradient(to right, #e1f5fe, #b3e5fc);

  margin: 0 auto;
  padding: 20px;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.dashboard {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
}
</style>
