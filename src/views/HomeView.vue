<script setup lang="ts">
import { ref, onMounted } from 'vue'
interface IOption {
  name: string
  value: string
}

const asyncData1 = ref();
const asyncData2 = ref();

onMounted(() => {
  fetch('https://jsonplaceholder.typicode.com/todos/1')
      .then(response => response.json())
      .then(json => {
        console.log(json);
        asyncData1.value = "asyncData1 some tree calls fire";
        setTimeout(() => {          
          asyncData2.value = "asyncData2 cat beats lion and mouse cries";
        }, 5000);
      })
});

const options: IOption[] = [{name: "Project name", value: "spa-seo-cmv"},{name: "Github Actions Workflow", value: "true"},{name: "Navigation drawer", value: "SimpleDrawer"},{name: "Header", value: "SimpleHeader"},{name: "Footer", value: "SimpleFooter"}];
</script>

<template>
  <div>
    <h2>{{ asyncData1 }}</h2>
    <h2>{{ asyncData2 }}</h2>
    <h3>Congratulations with scaffolding your vue webapp!</h3>
    <p v-if="options.length">
      Selected options:
    </p>
    <ul>
      <li
        v-for="option in options"
        :key="option.name"
      >
        {{ `${option.name}: ${option.value}` }}
      </li>
    </ul>
  </div>
</template>
