<template>
  <div>
    <h1>My Course Goal</h1>
    <hr />
    <h2>Task 1:</h2>
    <!-- Task 1: Output your main course goal with help of the composition API -->
    <!-- Don't hardcode it into the template, instead hardcode it into the JS code -->

    <h3 v-if="isMainGoalVisible">Separe ref: {{ myMainGoal }}</h3>

    <hr />
    <h2>Task 2:</h2>

    <!-- Task 2: Toggle (show/ hide) the goal with help of the button  -->
    <button type="button" @click="toggleGoal">Separe ref: Toggle Goal</button>

    <hr />
    <h2>Task 3:</h2>

    <!-- Task 3: Manage data in three ways -->
    <h3>Separe ref: {{ myMainGoal }}</h3>
    <h3>Ref Object: {{ objGoal.myMainGoal }}</h3>
    <h3>Reactive Object: {{ objGoalReactive.myMainGoal }}</h3>

    <!-- Task 4: Also solve the assignment with the Options API -->
  </div>
</template>

<script>
import { ref, reactive } from 'vue'
export default {
  setup() {
    const isMainGoalVisible = ref(true);
    const myMainGoal = ref('My main go is to improve my knowlodge of Vue.js and get a new opportunies for my career.');

    const objGoal = ref(
      {
        myMainGoal: 'My main go is to improve my knowlodge of Vue.js and get a new opportunies for my career.',
        isMainGoalVisible: true
      }
    );

    const objGoalReactive = reactive({
      myMainGoal: 'My main go is to improve my knowlodge of Vue.js and get a new opportunies for my career.',
      isMainGoalVisible: true
    });

    setTimeout(() => {
      myMainGoal.value = myMainGoal.value + ' And get better salary =)';
      objGoal.value.myMainGoal = objGoal.value.myMainGoal + ' And get better salary =)';
      objGoalReactive.myMainGoal = objGoalReactive.myMainGoal + ' And get better salary =)';
    }, 3000);

    function showHideGoalHandle() {
      isMainGoalVisible.value = !isMainGoalVisible.value;
      objGoal.value.isMainGoalVisible = !objGoal.value.isMainGoalVisible;
    }

    return {
      myMainGoal,
      isMainGoalVisible,
      objGoal,
      objGoalReactive,
      toggleGoal: showHideGoalHandle
    }
  },
  /**
   * Here is the task 4
   */
  // data() {
  //   return {
  //     isMainGoalVisible: true,
  //     myMainGoal: 'My main go is to improve my knowlodge of Vue.js and get a new opportunies for my career.'
  //   }
  // },
  // methods: {
  //   toggleGoal() {
  //     this.isMainGoalVisible = !this.isMainGoalVisible;
  //   }
  // }
}
</script>

<style>
html {
  font-family: sans-serif;
}

body {
  margin: 3rem;
  text-align: center;
}
</style>