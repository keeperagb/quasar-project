<template>
  <div class="row justify-around q-py-md">
    <cardDash />
    <cardDash />
    <cardDash />
    <cardDash />
  </div>
</template>

<script>
import cardDash from "./Card/cardDash.vue";
export default {
  name: "topoDash",
  components: {
    cardDash,
  },
};
</script>

<style lang="scss">
.cor {
  color: $red-1;
  background-color: $grey-3;
}
.my-card {
}
</style>
