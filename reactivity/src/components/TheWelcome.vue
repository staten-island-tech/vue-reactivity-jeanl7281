<script>
export default {
  data() {
    return {
      animals: ["pig", "cow", "ostrich", "dog", "sheep", "turkey"],
      rodents: ["Mouse", "Hamster", "Gerbil", "Rat", "Guinea Pig"],
      dogs: [
        "Golden Retriever",
        "Pug",
        "Poodle",
        "Husky",
        "Pomeranian",
        "Chihuahua",
        "Bulldog",
        "Samoyed",
      ],
      cats: [
        "Siamese",
        "British Shorthair",
        "Persian",
        "Sphynx",
        "American Shorthair",
        "Abyssinian",
        "Burmese",
        "Scottish Fold",
      ],
    };
  },
  methods: {},
};
</script>

<template>
  <h2>Animals</h2>
  <p v-for="animal in animals" :key="animal">{{ animal }}</p>
  <p v-for="cat in cats" :key="cat">{{ cat }}</p>
</template>

<style scoped>
p {
  text-align: center;
  margin-bottom: 6rem;
}
</style>
