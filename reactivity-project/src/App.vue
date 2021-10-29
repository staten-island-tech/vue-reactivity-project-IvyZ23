<template>
  <div id="app">

      <section id="user-inputs">

      <h1>The Menu:</h1>

      <div id="choices-section">
        <div id="food-choices">
          <div class="choice" v-for="(foodChoice, index) in foodChoices" :key="index">
            <button @click="updateFoodList(index)"> {{ foodChoice.food }} </button>
            <img class="image" :src="foodChoice.foodImage">
            <p>${{ foodChoice.price }}</p>
          </div>
        </div>

        <div id="drink-choices">
          <div class="choice" v-for="(drinkChoice, index) in drinkChoices" :key="index">
            <button @click="updateDrinkList(index)"> {{ drinkChoice.drink }} </button>
            <img class="image" :src="drinkChoice.drinkImage">
            <p>${{ drinkChoice.price }}</p>
          </div>
        </div>
      </div>

    </section>

    <section id="order-list">
      <h2>Your Order:</h2>
      <div id="orderInfo">
        <ul class="list">
          <li class="info" v-for="order in order" :key="order">{{ order }}</li>  
        </ul>
        <ul class="list">
          
          <li class="info" v-for="price in orderPrice" :key="price">${{ price }}</li>  
        </ul>
      </div>
      <h3>Subtotal: ${{ subtotal }}</h3>
      <button class="delete-btn" @click="removeLastItem()">Delete previous order.</button>
      <button class="delete-btn" @click="removeAllItems()">Delete all orders.</button>
    </section>

  </div>

</template>

<script>
export default {
  name: 'App',
  components: {
    
  },
  data() {
    return {
      subtotal: 0,
      selectedFood: 0,
      selectedDrink: 0,
      foodChoices: [ 
        {
          food: "Hamburger",
          foodImage: require("./assets/hamburger.jpg"),
          price: 3,
        },
        {
          food: "Pizza",
          foodImage: require("./assets/pizza.jpg"),
          price: 2,
        },
        {
          food: "Fries",
          foodImage: require("./assets/fries.jpg"),
          price: 1.5,
        },
        {
          food: "Salad",
          foodImage: require("./assets/salad.jpg"),
          price: 2.00,
        },
      ],
      drinkChoices: [ 
        {
          drink: "Water",
          drinkImage: require("./assets/water.jpg"),
          price: 0,
        },
        {
          drink: "Soda",
          drinkImage: require("./assets/soda.jpg"),
          price: 1,
        },
        {
          drink: "Orange Juice",
          drinkImage: require("./assets/orange.jpg"),
          price: 1,
        },
        {
          drink: "Coffee",
          drinkImage: require("./assets/coffee.jpg"),
          price: 3,
        },
      ],
      order: [],
      orderPrice: [],
    }
  },
  methods: {
    updateFoodList(index) {
      this.order.push(this.foodChoices[index].food)
      this.orderPrice.push(this.foodChoices[index].price)
      this.subtotal = this.subtotal + this.foodChoices[index].price
    },
    updateDrinkList(index) {
      this.order.push(this.drinkChoices[index].drink)
      this.orderPrice.push(this.drinkChoices[index].price)
      this.subtotal = this.subtotal + this.drinkChoices[index].price
    },
    removeLastItem(){
      if (this.order.length !== 0) {
        this.subtotal = this.subtotal - this.orderPrice[this.orderPrice.length - 1]
        this.order.pop()
        this.orderPrice.pop()
      }
    },
    removeAllItems() {
      this.order = []
      this.orderPrice = []
      this.subtotal = 0
    }
  },
} 
</script>

<style lang="css">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: row;
}
.name-form {
  display: flex;
  flex-direction: column;
  width: 30vw;
}
.image {
  height: 6rem;
  width: 6rem;
  object-fit: cover;
}
.choice {
  display:flex;
  flex-direction: column;
}
#drink-choices,
#food-choices{
  display: flex;
  flex-direction: row;
  margin: 2rem;
}
section {
  width: 50vw;
  display: flex;
  align-items: center;
  flex-direction: column;
}
#order-list {
  border: 1px black solid;
  margin: 1rem 5rem;
  height: auto;
}
.hidden {
  display: none;
}

.list {
  list-style: none;
}

#orderInfo {
  display:flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.delete-btn {
  margin-bottom: 1rem;
}
</style>