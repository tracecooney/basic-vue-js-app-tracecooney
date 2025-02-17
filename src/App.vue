<script>
import shoppingList from './components/shoppingList.vue'
import shoppingForm from './components/ShoppingForm.vue'

export default {
  name: 'App',
  components: {
    shoppingList,
    shoppingForm'l,v
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
      // Find the highest id and increment
      const newId = Math.max(...this.shoppingItems.map(i => i.id), 0) + 1;
      
      this.shoppingItems.push({
        id: newId,
        name: item.name,
        amount: item.amount,
      });
    },
    deleteItem(id) {
      this.shoppingItems = this.shoppingItems.filter(item => item.id !== id);
    },
    editItem(updatedItem) {
      const index = this.shoppingItems.findIndex(item => item.id === updatedItem.id);
      if (index !== -1) {
        this.shoppingItems[index] = updatedItem;
      }
    },
  },
}
</script>

<template>
<div id="app" class="small-container">
  <h2>Shopping List</h2>
  <shoppingList :items="shoppingItems" @delete:item="deleteItem" @edit:item="editItem"/>
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
