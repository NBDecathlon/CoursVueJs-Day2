<template>
    <div class="table-container">
      <table border="1">
        <thead>
          <tr>
            <th>ID</th>
            <th>Label</th>
            <th>Description</th>
            <th>Statut</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="product in products" :key="product.id">
            <td>{{ product.id }}</td>
            <td>{{ product.label }}</td>
            <td>{{ product.description }}</td>
            <td>{{ product.qte > 0 ? 'Disponible' : 'Indisponible' }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ProductList',
    props: {
      products: {
        type: Array,
        required: true,
      },
    },
  };
  </script>
  
<style>
  .table-container {
    display: flex;
    justify-content: center;
    align-items: flex-start;
    height: 100vh;
    padding-top: 20px;
    box-sizing: border-box;
  }
  
  table {
    border-collapse: collapse;
    width: auto;
  }
  
  th,
  td {
    padding: 8px;
    text-align: left;
    border: 1px solid #ccc;
  }
  
  th {
    background-color: #f4f4f4;
  }
</style>
  