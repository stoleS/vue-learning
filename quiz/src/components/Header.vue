<template>
  <div>
    <b-nav tabs>
      <b-nav-item disabled>
        <b>Quiz tut</b>
      </b-nav-item>
      <b-nav-item disabled>Correct: {{ correctAnswers }}</b-nav-item>
      <b-nav-item disabled>Answered: {{ total }}</b-nav-item>
      <b-nav-item disabled>Total: {{ questionsNumber }}</b-nav-item>
    </b-nav>
  </div>
</template>

<script>
export default {
  props: {
    correctAnswers: Number,
    total: Number,
    questionsNumber: Number,
  },
};
</script>