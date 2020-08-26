<template>
  <div>
    <b-button
      @click="submitAnswer"
      :disabled="selectedIndex === null || answered === true"
      variant="primary"
      href="#"
      class="btn"
    >Submit</b-button>
    <b-button
      @click="next"
      :disabled="questionsNumber === total + 1 || !answered"
      variant="success"
      href="#"
      class="btn"
    >Next</b-button>
  </div>
</template>

<script>
export default {
  props: {
    submitAnswer: Function,
    selectedIndex: Number,
    answered: Boolean,
    next: Function,
    questionsNumber: Number,
    total: Number,
  },
};
</script>

<style scoped>
.btn {
  margin: 0 10px;
}
</style>
