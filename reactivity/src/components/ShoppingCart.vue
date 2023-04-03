<template>
    <div class="orderInfo">
    <ul class="list">
        <li class="info">{{ order }}</li>  
    </ul>
    <ul class="list">
      <li class="info">${{ price }}</li>  
    </ul>
</div>
</template>

<script>
export default {
    name: "Cart",
    props: {
        order: String,
        price: Number,
    },
    methods: {
    }
}
</script>

<style>
.hidden {
  display: none;
}
.list {
  list-style: none;
}
.orderInfo {
  display:flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}
</style>