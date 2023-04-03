<template>
  <div id="app">
    <section id="user-inputs">
      <h1 id="title">Pets:</h1>
      <h2>Click On Pet Type to Add To Cart</h2>
      <div class="pet-choices">
        <Card
          class="choice"
          v-for="(petChoice, index) in petChoices"
          @addpPetList="addPetList(index)"
          :key="index"
          :pet="petChoice.pet"
          :petImage="petChoice.petImage"
          :description="petChoice.description"
          :price="petChoice.price"
        />
      </div>
    </section>

    <section id="order-list">
      <h1>Your Order:</h1>
      <Cart
        class="cart"
        v-for="(petChoice, index) in order"
        :key="index"
        :order="petChoice.pet"
        :price="petChoice.price"
      />
      <h2>Subtotal: ${{ subtotal }}</h2>
      <button class="delete-btn" @click="removeLastItem()">
        Delete Last Pet
      </button>
      <button class="delete-btn" @click="removeAllItems()">
        Delete All Pets
      </button>
    </section>
  </div>
</template>

<script>
import Card from "./components/CreateCards.vue";
import Cart from "./components/ShoppingCart.vue";
export default {
  pet: "App",
  components: {
    Card,
    Cart,
  },
  data() {
    return{
      subtotal: 0,
      selectedPet: 0,
      petChoices: [
      {
    pet: "German Shepherd",
    price: 2000,
    description: "Large athletic, and intelligent dog with noble personalities",
    petImage:
      "https://www.petplace.com/static/d9ef35df99413fbc95fa70fb5e2cb4a5/0979f/petImage00077-2.jpg",
  },
  {
    pet: "Bulldog",
    price: 2500,
    description: "Stocky build and walk with a swinging gait",
    petImage:
      "https://encrypted-tbn0.gstatic.com/petImages?q=tbn:ANd9GcT9dsgCBp--4TcUhn10XSbdss0915ZYlvSMmA&usqp=CAU",
  },
  {
    pet: "Labrador Retriever",
    price: 1000,
    description: "Affectionate, energetic, and enthusiastic companions",
    petImage:
      "https://encrypted-tbn0.gstatic.com/petImages?q=tbn:ANd9GcRqtevyTOTKqvE9uNtGEMxfEUMJglnnBT0iVg&usqp=CAU",
  },
  {
    pet: "Golden Retriever",
    price: 1000,
    description: "Well-built dog with thick, beautiful coat of fur",
    petImage:
      "https://cdn.pixabay.com/photo/2019/04/17/20/18/golden-retriever-4135265_960_720.jpg",
  },
  {
    pet: "Husky",
    price: 1750,
    description: "Compact, thick-coated sled dog with exceptional endurance",
    petImage:
      "https://cdn.pixabay.com/photo/2018/07/10/15/36/dog-3528936_960_720.jpg",
  },
  {
    pet: "Pomeranian",
    price: 6000,
    description: "Elegant, fluffy double coat, foxy face, and perky ears.",
    petImage:
      "https://cdn.pixabay.com/photo/2015/12/29/20/51/dog-1113398_960_720.jpg",
  },
  {
    pet: "Chow Chow",
    price: 2500,
    description:
      "Square, strong build, and coat that is styled to resemble a lion's",
    petImage: "https://cdn.pixabay.com/photo/2022/04/13/15/00/chow-chow-7130445_960_720.jpg",
  },
  {
    pet: "Shiba Inu",
    price: 3000,
    description: "Strong prey drive and are devoted and vigilant dogs.",
    petImage:
      "https://th.bing.com/th/id/OIP.6LOFoODNAeX6OYQNa-j7YgHaE8?w=290&h=186&c=7&r=0&o=5&pid=1.7",
  },
  {
    pet: "Maltipoo",
    price: 3500,
    description:
      "A hybrid between a maltese and poodle. Gentle, playful, and highly intelligent.",
    petImage:
      "https://megamascota.hiperarticulos.com/wp-content/uploads/2016/09/Chow-Chow-2-1024x907.jpg",
  },
  {
    pet: "Pomsky",
    price: 5000,
    description:
      "A hybrid between a Siberian husky and a pomeranian. They have fluffy, triangular ears, intelligent, and very active.",
    petImage:
      "https://th.bing.com/th/id/OIP.dkcS0e6-0jq-izqmFm9tBQHaE8?w=264&h=180&c=7&r=0&o=5&pid=1.7",
  },
  {
    pet: "Cockapoo",
    price: 2500,
    description: "A hybrid between a cocker spaniel and a poodle.",
    petImage:
      "https://petImages.unsplash.com/photo-1644928873735-0e201fc9421e?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1165&q=80",
  },
  {
    pet: "Goldendoodle",
    price: 3500,
    description: "A hybrid between a golden retriever and poodle.",
    petImage:
      "https://cdn.pixabay.com/photo/2019/03/22/14/05/golden-doodle-4073353_960_720.jpg",
  },
      ],
      order: [],
      orderPrice: [],
    };
  },
  methods: {
    addPetList(index) {
      this.order.push(this.petChoices[index]);
      this.orderPrice.push(this.petChoices[index].price);
      this.subtotal = this.subtotal + this.petChoices[index].price;
    },
    removeLastItem() {
      if (this.order.length !== 0) {
        this.subtotal =
          this.subtotal - this.orderPrice[this.orderPrice.length - 1];
        this.order.pop();
        this.orderPrice.pop();
      }
    },
    removeAllItems() {
      this.order = [];
      this.orderPrice = [];
      this.subtotal = 0;
    },
  },
};
</script>

<style lang="css">
h2 {
  font-size: 20px;
}
#title {
  text-decoration: underline;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  text-align: center;
  color: #25086e;
  display: flex;
  flex-direction: row;
  background-color: #8db0f5;
}
#user-inputs {
  width: 50vw;
}
.pet-choices {
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
}
section {
  display: flex;
  align-items: center;
  flex-direction: column;
}
#order-list {
  border: 10px #09025f solid;
  border-radius: 10px;
  margin: 1rem;
  height: auto;
  background-color: #c7d9ff;
  color: #09025f;
  width: 30vw;
}
.delete-btn {
  margin-bottom: 1rem;
}
</style>