<template>
    <div id="container">
        <table id="products">
            <thead>
                <tr>
                <th class="text-left">
                    Name
                </th>
                <th class="text-left">
                    Description
                </th>
                <th class="text-left">
                    Price
                </th>
                <th class="text-left">
                    Category
                </th>
                </tr>
            </thead>
            <tbody>
                <tr
                v-for="item in products"
                :key="item.name"
                >
                <td>{{ item.name }}</td>
                <td>{{ item.description }}</td>
                <td>{{ item.price }}</td>
                <td>{{ item.category_id }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
const axios = require('axios')

export default {
  name: 'Table',
  data () {
    return {
      products: {}
    }
  },
  mounted () {
    axios.get('http://localhost:8000/api/products')
      .then(response => {
        console.log(response.data)
        this.products = response.data
      })
  }

}
</script>

<style scoped>
#container{
    padding:100px;
}

#products {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

#products td, #products th {
  border: 1px solid #ddd;
  padding: 8px;
}

#products tr:nth-child(even){background-color: #f2f2f2;}

#products tr:hover {background-color: #ddd;}

#products th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background-color: #04AA6D;
  color: white;
}
</style>
