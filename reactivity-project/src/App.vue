<template>
  <div id="app">

      <section id="user-inputs">

        <div id="form-section">
        <form class="name-form" @submit.prevent="nameSubmitted">
          <label>Enter your name:</label>
          <p>
            <input v-model="name" id="name">
            <input type="submit" value="Enter">
          </p>
        </form>
      </div>

      <div id="choices-section" :class="{ hidden: !formSubmitted}">
        <h2>Hello {{ name }}, what would you like to order?</h2>
        <div id="food-choices">
          <div class="choice" v-for="foodChoice in foodChoices" :key="foodChoice">
            <button> {{ foodChoice.food }} </button>
            <img class="image" v-bind:src="foodChoice.foodImage">
          </div>
        </div>

        <div id="drink-choices">
          <div class="choice" v-for="drinkChoice in drinkChoices" :key="drinkChoice">
            <button> {{ drinkChoice.drink }} </button>
            <img class="image" v-bind:src="drinkChoice.drinkImage">
          </div>
        </div>
      </div>

    </section>

    <section id="order-list">
      <h2>Your Order:</h2>
      <ul id="list">
        <li class="orders">testing</li>  
      </ul>
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
      nameForm: [],
      blankField: [],
    }
  },
  method: {
    nameSubmitted() {
      if (this.name) {
        this.nameForm.push(this.name)
        console.log(this.name)
      } else {
      if(!this.name) this.fieldBlank.push("Please enter a name.")
    }
    },
    formSubmitted() {
      return this.nameForm.length;
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
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

#order-list {
  border: 1px black solid;
  margin: 5rem;
  height: auto;
}

.hidden {
  display: none;
}
</style>