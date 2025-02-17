<script>
export default {
    name: 'shopping-List',
    props: {
      items: Array
  },
  data() {
    return {
        editting: null
    }
  },
  methods: {
    editMode(id) {
        this.editting = id;
    },
    editItem(item) {
        this.$emit('edit:item', item);
        this.editting = null;
    }

  }
}
</script>

<template>
  <div id="shoppingList-table">
    <table>
      <thead>
        <tr>
          <th>Item</th>
          <th>Amount</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" :key="item.id">
          <!-- This should be inside the correct conditional structure -->
          <td>{{ item.amount }}</td>
          
          <!-- Edit Mode (when editting is active) -->
          <td v-if="editting === item.id">
            <button @click="editItem(item)"> Save </button>
            <button class="muted-button" @click="editting = null"> Cancel </button>
          </td>

          <!-- Default (when not in edit mode) -->
          <td v-else>
            <button @click="editMode(item.id)"> Edit </button>
            <button @click="$emit('delete:item', item.id)"> Delete </button>
          </td>
        </tr>
      </tbody>
    </table>
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

h2 {
  color: #333;
  font-family: Arial, sans-serif;
}
</style>
