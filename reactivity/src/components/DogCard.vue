<template>
  <div class="choice">
    <button class="dog" @click="$emit('addDogList')">
      {{ dog }} ${{ price }}
    </button>
    <img class="image" :src="dogImage" :alt="description[0]" />
    <h1 class="description">{{ description }}</h1>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    dog: String,
    price: Number,
    dogImage: String,
    description: String,
  },
};
</script>

<style>
.dog {
  height: 2rem;
}
.image {
  height: 10rem;
  object-fit: cover;
  display: block;
}
.description {
  font-size: 12px;
  align-content: center;
}
.choice {
  display: flex;
  flex-direction: column;
  margin-left: 20px;
  width: 12.7vw;
}
</style>