<template>
  <div class="home">
    <h1>Update Name and Age Ref Demo</h1>
    <p>My name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick">click me</button>
    
    <input type="text" v-model="name">
    <p><button @click="age++">Increase Age</button></p>

    <h1>Update Ninja One</h1>
    <p>{{ ninjaOne.name }} - {{ ninjaOne.age }}</p>
    <button @click="updateNinjaOne">Update ninja one</button>

    <h2>Reactive</h2>
    <p>{{ ninjaTwo.name }} - {{ ninjaTwo.age }}</p>
    <button @click="updateNinjaTwo">Update ninja two</button>
  </div>
</template>

<script>
import { ref, reactive } from 'vue'

export default {
  name: 'Home',
  setup() {

    const ninjaOne = ref({ name: 'mario', age: 30 })
    const ninjaTwo = reactive({ name: 'luigi', age: 35 })

    const updateNinjaOne = () => {
      ninjaOne.value.age = 40
    }

    const updateNinjaTwo = () => {
      ninjaTwo.age = 45
    }

    const name = ref('Kyle')
    const age = ref(49)

    const handleClick = () => {
      name.value = 'Julie'
      age.value = 47
    }

    return { name, age, handleClick, ninjaOne, updateNinjaOne, ninjaTwo, updateNinjaTwo }
  }
}
</script>
