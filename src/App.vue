<template>
  <div>
    <label>Counter: {{ counter.count }}</label>
  </div>
  <div>
    <button @click="increment">Increment</button>
    <button @click="decrement">Decrement</button>
  </div>
</template>

<script lang="ts" setup>
import { useCounterStore } from "../src/store/store";

const counter = useCounterStore();

function increment() {
  counter.increment();
}

function decrement() {
  counter.decrement();
}
</script>
