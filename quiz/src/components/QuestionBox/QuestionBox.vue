<template>
  <div class="question-box">
    <b-jumbotron>
      <template v-slot:lead>{{ currentQuestion.question }}</template>

      <hr class="my-4" />

      <QuestionList
        :shuffledAnswers="shuffledAnswers"
        :selectAnswer="selectAnswer"
        :selectedIndex="selectedIndex"
        :answered="answered"
        :answerVariant="answerVariant"
      />

      <QuestionButtons
        :submitAnswer="submitAnswer"
        :selectedIndex="selectedIndex"
        :answered="answered"
        :next="next"
        :questionsNumber="questionsNumber"
        :total="total"
      />
    </b-jumbotron>
  </div>
</template>

<script>
import QuestionList from "./QuestionBoxList.vue";
import QuestionButtons from "./QuestionBoxButtons.vue";
export default {
  props: {
    currentQuestion: Object,
    next: Function,
    increment: Function,
    questionsNumber: Number,
    total: Number,
  },
  components: {
    QuestionList,
    QuestionButtons,
  },
  data() {
    return {
      selectedIndex: null,
      correctIndex: null,
      shuffledAnswers: [],
      answered: false,
    };
  },
  watch: {
    currentQuestion: {
      immediate: true,
      handler() {
        this.selectedIndex = null;
        this.shuffleAnswers();
        this.answered = false;
        this.correctIndex = this.shuffledAnswers.indexOf(
          this.currentQuestion.correct_answer
        );
      },
    },
  },
  methods: {
    selectAnswer(i) {
      this.selectedIndex = i;
    },
    shuffleAnswers() {
      let answers = [
        ...this.currentQuestion.incorrect_answers,
        this.currentQuestion.correct_answer,
      ];
      answers.sort(() => Math.random() - 0.5);
      this.shuffledAnswers = answers;
    },
    submitAnswer() {
      this.answered = true;
      let isCorrect = false;
      if (this.selectedIndex === this.correctIndex) {
        isCorrect = true;
      }
      this.increment(isCorrect);
    },
    answerVariant(i) {
      return this.answered && this.correctIndex === i
        ? "success"
        : this.answered &&
            this.selectedIndex === i &&
            this.correctIndex !== i &&
            "danger";
    },
  },
};
</script>

<style>
.question-box {
  margin-top: 40px;
}
</style>