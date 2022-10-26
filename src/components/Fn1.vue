<script lang="ts" setup>
import { reactive, ref, computed, onMounted } from 'vue'

const props = defineProps(['foo1'])
console.log('setup props', props.foo1)
const emits = defineEmits(["fn1ppp"])

let count = ref(0);
const data1 = reactive({
  count: 0,
  message: 'sdsd',
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})

// 一个计算属性 ref
const publishedBooksMessage = computed(() => {
  return data1.books.length > 0 ? 'Yes' : 'No'
})

// 声明一个 ref 来存放该元素的引用
// 必须和模板里的 ref 同名
const inputRef: any = ref(null)


onMounted(() => {
  inputRef.value.focus()
  console.log('onMounted');
});

// 事件函数
function handleClick () {
  data1.count++
}

function handleClick2 () {
  count.value++
}

function postProps () {
  emits('fn1ppp', 666)
}

console.log('set up update')
</script>

<template>
  <p>Has published books:</p>
  <span>{{ publishedBooksMessage }}</span>
  <div>
    {{ data1.count }}
    <button @click="handleClick">add</button>
  </div>
  <div>
    {{ count }}
    <button @click="handleClick2">add</button>
  </div>
  <div>
    {{ props.foo1 }}
    <button @click="postProps">post event</button>
  </div>
  <p>Message is: {{ data1.message }}</p>
  <input ref="inputRef" v-model="data1.message" placeholder="input for" />
</template>
