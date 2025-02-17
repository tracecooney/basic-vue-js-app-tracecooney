<script>
export default {
    name: 'Shopping-form',
    data() {
        return {
            item: {  // Renamed to `item` for consistency
                name: '',
                amount: '',  // amount will be treated as a string until we convert it to a number
            },
        }
    },
    methods: {
        addItem() {
            this.$emit('add-item', {
                name: this.item.name,
                amount: Number(this.item.amount) || 0,  // Ensure amount is a number
            })
            // Reset the form
            this.item = { 
                name: '',
                amount: '',
            }
        }
    }
}
</script>

<template>
  <div id="shopping-form">
    <form @submit.prevent="addItem">
      <label> Shopping Item </label>
      <input type="text" v-model="item.name"/>  <!-- Renamed reference -->
      
      <label> Item Amount </label>
      <input type="number" v-model="item.amount"/>  <!-- Renamed reference -->
      
      <button> Add Item </button>
    </form>
  </div>
</template>

<style scoped>
/* Your styling is empty but can be added here */
</style>
