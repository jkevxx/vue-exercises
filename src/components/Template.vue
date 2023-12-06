<script setup lang="ts">

defineProps({
  msg: {
    type: String,
  }
})
</script>


<template>
  <div>
    <h1>{{ msg }}</h1>
  </div>
</template>


<style scoped>
h1 {
  color: #fff;
}
</style>