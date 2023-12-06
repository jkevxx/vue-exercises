<script setup lang="ts">
import { computed, ref } from 'vue';

defineProps({
  msg: String,
});

const count = ref<number>(0);
const arrayNumbers = ref<number[]>([]);

const increment = () => {
  count.value++;
};

const decrement = () => {
  count.value--;
};

const resetCount = () => {
  count.value = 0;
};

const saveNumber = () => {
  arrayNumbers.value.push(count.value);

};

const toggleButton = computed(() => {
  const numSearched = arrayNumbers.value.find((num) => num === count.value);
  console.log(numSearched)
  if (numSearched === 0) return true;
  return numSearched ? true : false;
});

const classCounter = computed(() => {
  if (count.value === 0) {
    return 'zero';
  }
  if (count.value > 0) {
    return 'positive';
  }
  return 'negative';
})
</script>

<template>
  <h1>{{ msg }}</h1>

  <!-- <h2 :class="{ positive: count > 0, negative: count < 0 }">{{ count }}</h2> -->
  <!-- <h2 :class="count > 0 ? 'positive' : 'negative'">{{ count }}</h2> -->
  <h2 :class="classCounter">{{ count }}</h2>
  <button type="button" @click="increment">Increment</button>
  <button type="button" @click="decrement">Decrement</button>
  <button type="button" @click="resetCount">Reset Count</button>
  <button type="button" @click="saveNumber" :disabled="toggleButton">
    Save Number
  </button>

  <h3>{{ arrayNumbers }}</h3>
</template>

<style scoped>
.negative {
  color: red;
}

.positive {
  color: green;
}

.zero {
  color: #fff;
}

button {
  border-radius: 8px;
  border: 1px solid transparent;
  padding: 0.6em 1.2em;
  font-size: 1em;
  font-weight: 500;
  font-family: inherit;
  background-color: #1a1a1a;
  cursor: pointer;
  transition: border-color 0.25s;
}

button:hover {
  border-color: #646cff;
}

button:focus,
button:focus-visible {
  outline: 4px auto -webkit-focus-ring-color;
}
</style>
