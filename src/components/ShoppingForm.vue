<script>
export default {
    name: 'Shopping-form',
    data() {
        return {
            Items: {  // Ensure naming consistency
                name: '',
                amount: '',
            },
        }
    },
    methods: {
        addItem() {
            this.$emit('add-item', this.Items)
            this.Items = { 
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
      <input type="text" v-model="Items.name"/>  <!-- Corrected reference -->
      <label> Item Amount </label>
      <input type="number" v-model="Items.amount"/>  <!-- Corrected reference -->
      <button> Add Item </button>
    </form>
  </div>
</template>

<style scoped>

</style>
