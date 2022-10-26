<script setup lang="ts">
import { reactive } from 'vue'
// import TheWelcome from '../components/TheWelcome.vue'
import Fn1 from '../components/Fn1.vue'

const datap = reactive({ foo1: 0 })

function handleFn1ppp (data: number) {
  console.log('handleFn1ppp', data);
  datap.foo1 += data
}
</script>

<template>
  <main>
    <Fn1 :foo1="datap.foo1" @fn1ppp="handleFn1ppp" />
    <!-- <TheWelcome /> -->
  </main>
</template>
