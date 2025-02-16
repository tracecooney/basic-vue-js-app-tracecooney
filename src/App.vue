<script>
import shoppingList from './components/shoppingList.vue'
import shoppingForm from './components/ShoppingForm.vue'

export default {
  name: 'App',
  components: {
    shoppingList,
    shoppingForm
  },
  data() {
    return {
      shoppingItems: [
        { 
          id: 1,
          name: 'Jelly',
          amount: 1,
        },
        { 
          id: 2,
          name: 'Peanut Butter',
          amount: 2,
        },
        { 
          id: 3,
          name: 'Bread',
          amount: 1,
        },
      ],
    }
  },
  methods: {
    addItem(item) {
      this.shoppingItems.push({
        id: this.shoppingItems.length + 1,
        name: item.name,
        amount: item.amount,
      })
    },
    deleteItem(id) {
      this.shoppingItems = this.shoppingItems.filter(item => item.id !== id)
    },
  },
}
</script>

<template>
<div id="app" class="small-container">
  <h2>Shopping List</h2>
  <shoppingList :items="shoppingItems" @delete:item="deleteItem"/>
  <shoppingForm @add-item="addItem"/>
</div>
</template>

<style scoped>
.small-container {
  max-width: 400px;
  margin: 20px auto;
  padding: 20px;
  background: #f9f9f9;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  text-align: center;
}
</style>
