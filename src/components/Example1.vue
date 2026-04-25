<script setup>
import {onMounted, ref} from "vue";

  let props = defineProps(['surname','name'])
  let data = ref(null);

  onMounted(async () => {
    const response = await fetch('/data.json').then(res => res.json());
    data.value = response.users
    console.log(data.value)
  })
</script>

<template>
<p>Пример глобального компонента.</p>
  <p>Преподователь: {{ props.surname }} {{ props.name }}</p>
  <p>Пользователи:</p>
  <li v-for="user in data">
    {{ user.surname }} {{ user.name }}
  </li>

</template>

<style scoped>

</style>