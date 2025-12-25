<template>
<div style="font-family: sans-serif; padding: 2rem">
    <h2>Vue Watch vs WatchEffect Demo</h2>

    <div>
      <label>Count: </label>
      <button @click="count++">Increment</button>
      <span>{{ count }}</span>
    </div>

    <div>
      <label>Message: </label>
      <input v-model="message" />
    </div>

    <hr />

    <div>
      <h3>Watch Output:</h3>
      <p>{{ watchOutput }}</p>
    </div>

    <div>
      <h3>WatchEffect Output:</h3>
      <p>{{ watchEffectOutput }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref, watch, watchEffect } from 'vue';

// Reactive state
const count = ref(0);
const message = ref('Hello');

const watchOutput = ref('');
const watchEffectOutput = ref('');

// --- Using watch ---
watch(count, (newVal, oldVal) => {
  watchOutput.value = `Count changed from ${oldVal} to ${newVal}`;
});

// --- Using watchEffect ---
watchEffect(() => {
  watchEffectOutput.value = `Message is: "${message.value}", Count is: ${count.value}`;
});
</script>