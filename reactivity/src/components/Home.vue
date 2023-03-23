<script>
export default {
  data() {
    return {
      student: "Sopie",
      animals: ["pig", "cow", "ostrich", "dog"],
      graduated: true,
      selected: "",
    };
  },
  methods: {},
};
</script>

<template>
  <h1 v-if="selected === 'A'">Correct Answer</h1>
  <h1 v-else-if="selected === ''">Select an asnwer</h1>
  <h1 v-else>"Wrong"</h1>
  <h1>{{ student }}</h1>
  <ul>
    <li v-for="animal in animals" :key="animal">{{ animal }}</li>
  </ul>
  <select v-model="selected">
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  <span>{{ selected }}</span>
</template>
