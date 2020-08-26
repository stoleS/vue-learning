<template>
  <b-card
    class="result-info-box"
    border-variant="primary"
    :header="box.title"
    :header-bg-variant="box.color"
    header-text-variant="white"
    align="center"
  >
    <b-card-text>Lorem ipsum dolor sit amet.</b-card-text>
  </b-card>
</template>

<script>
export default {
  props: {
    box: Object,
  },
};
</script>

<style scoped>
.result-info-box {
  width: 30%;
}
</style>