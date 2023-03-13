<template>
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
                    <button type="button" class="btn btn-dark" @click="submitCallToAction">Call to Action</button>
                </div>

            </div>
        </div>

    </div>
</template>
<script>
export default {
  name: 'ProductsForm',
  data() {
    return {
        product: {
            id: '',
            name: '',
            price: ''
        }
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

  methods: {
    submitCallToAction() {
        this.$emit('submit', this.product = {
            'id': Math.floor(Math.random() * 100),
            'name': this.product.name,
            'price': this.product.price
        });
        this.product = {};
    }

  },

}
</script>
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