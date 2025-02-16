<script>
export default {
    name: 'shopping-List',
    props: {
      items: Array,
  },
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
          <td>{{item.name}}</td>
          <td>{{item.amount}}</td>
            <td>
                <button @click="$emit('delete:item', item.id)">Delete</button>
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