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
        <button > {{}} </button>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
    
  }
  /*data() {
    return {
      foodChoices: ['hamburger', 'pizza', 'fries', 'salad'],
      drinkChoices: ['water', 'soda', 'orange juice', 'coffee']
    }
  } */
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
</style>
