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
            <div class="container prod-form">
              <div class="form">
                  <div class="form-group">
                      <div class="title">
                          <h3 class="text-center">Header Text</h3>
                      </div>
                      <div class="">
                          <p class="desc-text">Lorem ipsum dolor sit amet, consectetur adipicsing elit ut</p>
                      </div>
                      <div>
                          <input class="form-control name-form" v-model="product.name" placeholder="Name"/>

                      </div>
                      <div class="price-form-parent">
                          <input class="form-control price-form" v-model="product.price" placeholder="Price"/>
                      </div>
                      <div class="prod-button d-grid gap-2">
                          <button type="button" class="btn btn-dark" @click="submit" v-if="!flagUpdate">Create</button>
                          <button type="button" class="btn btn-dark" @click="update" v-if="flagUpdate">Update</button>

                      </div>
                  </div>
              </div>
            </div>
          </div>
      </div>
    </div>
  </div>
</template>
<style scoped>
    .description {
        width: 100%;
        border: 1px solid;
    }
    .desc-text {
        padding: 20px;
        text-align: center;
        color: #636262;
    }

    .form-group {
        padding: 50px;
    }

    .name-form {
        border: none;
        height: 50px;
    }
    .btn-dark {
        height: 50px;
        margin-top: 30px;
    }

    .price-form-parent {
        margin-top: 30px;
    }
    .price-form {
        border: none;
        height: 50px;
    }

    ::placeholder {
        color: #636262;
    }
    .text-header {
        margin-top: 20px;
    }
    .form-head {
    margin-top: 20px; 
    }
    .form {
        background: #ececec;
        height: 500px;
        width: 500px;
    }
    .prod-form {
        margin-left: 70px;
        margin-top: 275px;
        margin-bottom: 500px;
    }
</style>
<script >
import ProductsTable from './components/ProductsTable.vue'

export default {
  name: 'Products',
  components: {
    ProductsTable,
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
        ],
        product: {
            id: '',
            name: '',
            price: ''
        },
        flagUpdate: false,
        index: ''
    }
  },
  mounted() {
  },

  methods: {
    /* eslint-disable */ 
    submit() {

      this.product = {
            'id': Math.floor(Math.random() * 100),
            'name': this.product.name,
            'price': this.product.price
        }

      this.products.push(this.product); // add new product
      this.product = {}; // reset products
    },
    deleteProduct(pId) {
      this.products = this.products.filter((product) => product.id != pId);
    },
    updateProduct(Idx, product, flag) {
      this.flagUpdate = flag;
      this.index = Idx;
      this.product.id = product.id
      this.product.name = product.name;
      this.product.price = product.price;
    },
    update() {
      this.products[this.index].id = this.product.name;
      this.products[this.index].name = this.product.name;
      this.products[this.index].price = this.product.price;

      this.product = {} // reset form
      this.flagUpdate = false // back to create
    }
  },

}
</script>

