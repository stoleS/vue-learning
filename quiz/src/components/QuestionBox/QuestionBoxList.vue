<template>
  <b-list-group class="list-group">
    <b-list-group-item
      v-for="(answer, i) in shuffledAnswers"
      :key="i"
      @click="selectAnswer(i)"
      :active="i === selectedIndex && !answered"
      button
      :variant="answerVariant(i)"
    >{{ answer }}</b-list-group-item>
  </b-list-group>
</template>

<script>
export default {
  props: {
    shuffledAnswers: Object,
    selectAnswer: Function,
    selectedIndex: Number,
    answered: Boolean,
    answerVariant: Function,
  },
};
</script>

<style scoped>
.list-group {
  margin-bottom: 15px;
}
</style>