<template>
  <section>
    <h3>Current Goals</h3>
    <GoalList v-if="goals && goals.length > 0" :goals="goals"/>
  </section>
</template>

<script>
import api from '../../services/api';
import GoalList from './GoalList';

export default {
  data() {
    return {
      goals: null
    };
  }, 
  components: {
    GoalList
  },
  created() {
    api.getGoals()
      .then(goals => {
        this.goals = goals;
      })
      .catch(err => {
        this.error = err;
      });
  }
};
</script>

<style>

</style>
