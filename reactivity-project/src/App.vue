<template>
  <div id="app">

    <form class="name-form" @submit.prevent="onSubmit">
      <label>Enter your name:</label>
      <p>
        <input id="name-info">
        <input type="submit" value="Enter">
      </p>
    </form>

    <div class="food-choices">
      <ul>
        <button v-for="foodChoice in foodChoices" :key="foodChoice"> {{ foodChoice.food }} </button>
        <img class="image" v-for="foodChoice in foodChoices" :key="foodChoice" v-bind:src="foodChoice.foodImage">
      </ul>
    </div>

    <div class="drink-choices">
      <ul>
        <div class="drink">
          <button v-for="drinkChoice in drinkChoices" :key="drinkChoice"> {{ drinkChoice.drink }} </button>
          <img class="image" v-for="drinkChoice in drinkChoices" :key="drinkChoice" v-bind:src="drinkChoice.drinkImage">
        </div>
      </ul>
    </div>

  </div>

</template>

<script>

export default {
  name: 'App',
  components: {
    
  },
  data() {
    return {
      foodChoices: [ 
        {
          food: "Hamburger",
          foodImage: require("./assets/hamburger.jpg"),
          price: 0,
        },
        {
          food: "Pizza",
          foodImage: require("./assets/pizza.jpg"),
          price: 0,
        },
        {
          food: "Fries",
          foodImage: require("./assets/fries.jpg"),
          price: 0,
        },
        {
          food: "Salad",
          foodImage: require("./assets/salad.jpg"),
          price: 0,
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
          price: 0,
        },
        {
          drink: "Orange Juice",
          drinkImage: require("./assets/orange.jpg"),
          price: 0,
        },
        {
          drink: "Coffee",
          drinkImage: require("./assets/coffee.jpg"),
          price: 0,
        },
      ],
    }
  } 
} 
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
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
</style>
