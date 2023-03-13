<template>
  <div class="products">
    <div class="row">
      <div class="col-md-6">
        <div>
          <ProductsTable :products="products" @delete="deleteProduct" @update="updateProduct"/>
        </div>
      </div>
      <div class="col-md-6">
          <div>
            <ProductForm 
              @submit="submitProduct" 
            />
          </div>
      </div>
    </div>
  </div>
</template>
<script >
import ProductsTable from './components/ProductsTable.vue'
import ProductForm from './components/ProductsForm.vue'

export default {
  name: 'Products',
  components: {
    ProductsTable,
    ProductForm
  },
  data() {
    return {
      products: [
            {id: 1, name: 'Lorem ipsum 1', price: 1},
            {id: 2, name: 'Lorem ipsum 2', price: 2},
            {id: 3, name: 'Lorem ipsum 3', price: 3},
            {id: 4, name: 'Lorem ipsum 4', price: 4},
            {id: 5, name: 'Lorem ipsum 5', price: 5},
            {id: 6, name: 'Lorem ipsum 6', price: 6}
        ]
    }
  },
  mounted() {
  },

  methods: {
  /* eslint-disable */ 
    submitProduct(e) {
      this.products.push(e); // add new product
      console.log("check product to be submitted", e);
    },
    deleteProduct(pId) {
      this.products = this.products.filter((product) => product.id != pId);
    },
    updateProduct(Idx, product) {
      this.products[Idx].id = product.name;
      this.products[Idx].name = product.name;
      this.products[Idx].price = product.price;
    }
  },

}
</script>
