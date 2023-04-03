<script>
export default {
  components: {ShoppingCart, CreateCards},
  data() {
    return {
      animalArray: [
        { name: "German Shepherd", price: "$2000"},
        { name: "Bulldog", price: "$2500"},
        { name: "Labrador Retriever", price: "$1000"},
        { name: "Golden Retriver", price: "$1000"},
        { name: "Husky", price: "$1750"},
        { name: "Pomeranian", price: "$6000"}
      ],
    cart: [],
    inCart: true,
    };
  },
  methods: {
    push: function (items) {
      this.cart.push(items);
      console.log(this.cart);
    },
    display: function() {
      this.inCart === !this.inCart;
    },
    removeItems: function (items) {
      this.cart = this.cart.filter((t) => t !== items);
      console.log(items);
    },
  },
};
</script>


<template>
  <div id="parent">
    <cartButton @click="display()" />
    <sub v-if="inCart === true">
      <cart 
      v-for="items in cart"
      :key="items"
      :name="items.name"
      :price="items.price"
      @click="removeItems(items)"
      />
    </sub>
  </div>
</template>
  
