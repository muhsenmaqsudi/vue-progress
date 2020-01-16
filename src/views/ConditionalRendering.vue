<template>
  <div>
    <h1 class="text-xl font-bold">Conditional Rendering</h1>
    <div class="flex p-4">
      <div class="w-1/2 border-2">
        <h2 class="text-lg font-semibold text-red-300">v-if</h2>
        <h3 v-if="awesome">Vue is awesome!</h3>
        <h3 v-else>Oh no 😢</h3>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ConditionalRendering",
  data() {
    return {
      awesome: true
    };
  }
};
</script>

<style lang="scss" scoped></style>
