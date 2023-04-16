<template>
  <div id="app">
    <section id="user-inputs">
      <h1 id="title">Dogs:</h1>
      <h2>Click On Dog Type to Add To Cart</h2>
      <div class="dog-choices">
        <Card class="choice" v-for="(dogChoice, index) in dogChoices" @addDogList="addDogList(index)" :key="index"
          :dog="dogChoice.dog" :dogImage="dogChoice.dogImage" :description="dogChoice.description"
          :price="dogChoice.price" />
      </div>
    </section>

    <section id="order-list">
      <h1>Your Order:</h1>
      <Cart class="cart" v-for="(dogChoice, index) in order" :key="index" :order="dogChoice.dog"
        :price="dogChoice.price" />
      <h2>Subtotal: ${{ subtotal }}</h2>
      <button class="delete-btn" @click="removeLastItem()">
        Delete Last Dog
      </button>
      <button class="delete-btn" @click="removeAllItems()">
        Delete All Dogs
      </button>
    </section>
  </div>
</template>

<script>
import Card from "./components/DogCard.vue";
import Cart from "./components/DogCart.vue";
export default {
  dog: "App",
  components: {
    Card,
    Cart,
  },
  data() {
    return {
      subtotal: 0,
      selectedDog: 0,
      dogChoices: [
        {
          dog: "German Shepherd",
          price: 2000,
          description: "Large athletic, and intelligent dog with noble personalities",
          dogImage: "https://www.petplace.com/static/d9ef35df99413fbc95fa70fb5e2cb4a5/0979f/Image00077-2.jpg",
        },
        {
          dog: "Bulldog",
          price: 2500,
          description: "Stocky build and walk with a swinging gait",
          dogImage: "https://encrypted-tbn0.gstatic.com/petImages?q=tbn:ANd9GcT9dsgCBp--4TcUhn10XSbdss0915ZYlvSMmA&usqp=CAU",
        },
        {
          dog: "Labrador Retriever",
          price: 1000,
          description: "Affectionate, energetic, and enthusiastic companions",
          dogImage: "https://encrypted-tbn0.gstatic.com/petImages?q=tbn:ANd9GcRqtevyTOTKqvE9uNtGEMxfEUMJglnnBT0iVg&usqp=CAU",
        },
        {
          dog: "Golden Retriever",
          price: 1000,
          description: "Well-built dog with thick, beautiful coat of fur",
          dogImage: "https://cdn.pixabay.com/photo/2019/04/17/20/18/golden-retriever-4135265_960_720.jpg",
        },
        {
          dog: "Husky",
          price: 1750,
          description: "Compact, thick-coated sled dog with exceptional endurance",
          dogImage: "https://cdn.pixabay.com/photo/2018/07/10/15/36/dog-3528936_960_720.jpg",
        },
        {
          dog: "Pomeranian",
          price: 6000,
          description: "Elegant, fluffy double coat, foxy face, and perky ears.",
          dogImage: "https://cdn.pixabay.com/photo/2015/12/29/20/51/dog-1113398_960_720.jpg",
        },
        {
          dog: "Chow Chow",
          price: 2500,
          description: "Square, strong build, and coat that is styled to resemble a lion's",
          dogImage: "https://cdn.pixabay.com/photo/2022/04/13/15/00/chow-chow-7130445_960_720.jpg",
        },
        {
          pet: "Shiba Inu",
          price: 3000,
          description: "Strong prey drive and are devoted and vigilant dogs.",
          dogImage: "https://th.bing.com/th/id/OIP.6LOFoODNAeX6OYQNa-j7YgHaE8?w=290&h=186&c=7&r=0&o=5&pid=1.7",
        },
        {
          dog: "Maltipoo",
          price: 3500,
          description: "A hybrid between a maltese and poodle. Gentle, playful, and highly intelligent.",
          dogImage: "https://megamascota.hiperarticulos.com/wp-content/uploads/2016/09/Chow-Chow-2-1024x907.jpg",
        },
        {
          dog: "Pomsky",
          price: 5000,
          description: "A hybrid between a Siberian husky and a pomeranian. They have fluffy, triangular ears, intelligent, and very active.",
          dogImage: "https://th.bing.com/th/id/OIP.dkcS0e6-0jq-izqmFm9tBQHaE8?w=264&h=180&c=7&r=0&o=5&pid=1.7",
        },
        {
          dog: "Cockapoo",
          price: 2500,
          description: "A hybrid between a cocker spaniel and a poodle.",
          dogImage: "https://images.unsplash.com/photo-1644928873735-0e201fc9421e?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1165&q=80",
        },
        {
          dog: "Goldendoodle",
          price: 3500,
          description: "A hybrid between a golden retriever and poodle.",
          dogImage: "https://cdn.pixabay.com/photo/2019/03/22/14/05/golden-doodle-4073353_960_720.jpg",
        },
      ],
      order: [],
      orderPrice: [],
    };
  },
  methods: {
    addDogList(index) {
      this.order.push(this.dogChoices[index]);
      this.orderPrice.push(this.dogChoices[index].price);
      this.subtotal = this.subtotal + this.dogChoices[index].price;
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
#title {
  text-decoration: underline;
}

h1 {
  font-size: 30px;
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
  width: 60vw;
}

.dog-choices {
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