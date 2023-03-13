<template>
    <div class="container prod-table">
        <div class="row">
            <div class="col-md-4">
                <h1>Products</h1>
            </div>
            <div class="col-md-4">
                <input class="form-control search-keywords" v-model="search" placeholder="Search for keywords..."/>
            </div>
            <div class="col-md-4"></div>
        </div>
        <div class="table">
            <table class="table table-bordered">
                <thead>
                    <tr>
                        <th scope="col">Name</th>
                        <th scope="col">Price</th>
                        <th scope="col">Action</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(product, index) in filteredProducts" :key="index">
                        <td>{{ product.name }}</td>
                        <!-- <td v-if="flagUpdate"><input v-model="product.name" class="form-control" @change="updateProduct(index, product)"/></td> -->
                        <td>{{ product.price }}</td>
                        <!-- <td v-if="flagUpdate"><input v-model="product.price" class="form-control" @change="updateProduct(index, product)"></td> -->
                        <td>                            
                            <button type="button" class="btn btn-dark" @click="updateProduct(index, product, true)">Edit</button>
                            <button type="button" class="btn btn-outline-dark" @click="deleteProduct(product.id)">Delete</button>
                        </td>
                    </tr>
                </tbody>
                </table>
        </div>
    </div>
</template>
<script>
export default {
  name: 'ProductsTable',
  props: {
    products: Array
  },
  data() {
    return {
        search: '',
    }
  },
    computed: {
    filteredProducts: function () {
        var filter_search = this.search.trim();
        return this.products.filter((product) => {
            return (
                product.name.match(filter_search)
            );
        });
    },
    },
  mounted() {
  },
/* eslint-disable */
  methods: {
    deleteProduct(pId) {
        this.$emit('delete', pId);
    },
    update() {
    },
    updateProduct(Idx, product, flag) {

        this.$emit('update', Idx, product, flag);
    }


  },

}
</script>
<style scoped>

    thead {
        background: #ececec;
        text-align: center;
        border: 1px solid #000000;
    }
    td {
        text-align: center;
        border: 1px solid #000000;
    }
    .table {
        margin-top: 20px;
    }
    .search-keywords {
        border: 1px solid #000000;
        height: 50px;
    }
    .prod-table {
        margin-left: 70px;
        margin-top: 200px;
        margin-bottom: 500px;
    }
    .btn-outline-dark {
        margin-left: 5px;
    }
</style>