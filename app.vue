<script setup lang="ts">
const { $client } = useNuxtApp()
const text = ref('world')

const back = ref();

// add a watch to the text ref
watch(text, async (newVal, oldVal) => {
  back.value = await $client.hello.useQuery({ text: newVal })

})

</script>

<template>
  <div>
    <h1>Hello World</h1>
    <input type="text" v-model="text">
    <h2>{{ text }}</h2>
    <h2>{{ back }}</h2>
  </div>
</template>
