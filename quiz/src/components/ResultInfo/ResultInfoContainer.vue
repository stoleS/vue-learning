<template>
  <div class="result-info-container">
    <InfoBox v-for="(type, i) in infoBoxes" :key="i" :box="type" />
  </div>
</template>

<script>
import InfoBox from "./ResultInfoBox.vue";
export default {
  props: {},
  components: {
    InfoBox,
  },
  data() {
    return {
      infoBoxes: [
        { title: "Correct", color: "success" },
        { title: "Answered", color: "dark" },
        { title: "Total", color: "info" },
      ],
    };
  },
};
</script>

<style scoped>
.result-info-container {
  margin-top: 40px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
</style>