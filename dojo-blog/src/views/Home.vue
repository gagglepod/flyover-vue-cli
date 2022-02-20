<template>
  <div class="home">
    <h1>Home</h1>
    <input type="text" v-model="search">
    <p>Search Term - {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">{{ name }}</div>
    <button @click="handleClick">Stop Watching</button>
  </div>
</template>

<script>
import { computed, ref, watch, watchEffect } from 'vue'

export default {
  name: 'Home',
  setup() {

    const search = ref('')
    const names = ref(['mario', 'luigi', 'yoshi', 'toad', 'bowser', 'koopa', 'peach'])

    const stopWatch = watch(search, () => {
      console.log('watch function ran')
    })

    const stopEffect = watchEffect(() => {
      console.log('watch effect function ran', search.value)
    })

    const matchingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value))
    })

    const handleClick = () => {
      stopWatch()
      stopEffect()
    }

    return { names, search, matchingNames, handleClick }
  }
}
</script>
