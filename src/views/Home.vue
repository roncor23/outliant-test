<template>
  <div id="app">
    <div class="container-fluid body1">
      <div class="row firstRow">
        <div class="col-md-6 ">
          <div class="lorem">
            <h1>Lorem ipsum</h1>
            <h1>dolor sit amet</h1>
            <h1>consectetur</h1>
          </div>
          <p class="sub-title">Lorem ipsum dolor sit amet, consectetur adipiscing elit ut aliquam, purus sit amet luctus venenatis, lectus</p>
            <button type="button" class="btn btn-dark">Call to Action</button>
            <button type="button" class="btn btn-outline-dark">See Workspace</button>
        </div>
        <div class="col-md-6 d-flex justify-content-center">
          <div class="backBox ">
          </div>
          <div class="frontBox"></div>
        </div>
      </div>
      <div class="row secondRow">
        <div class="col-md-4">
          <h5>Header Text</h5>
          <p class="s-description">Lorem ipsum dolor sit amet, consectetur adipiscing elit ut aliquam, purus sit amet luctus venenatis, lextus magna fringilla urna, porttitor rhoncus dolor purus non enim dolor.</p>
        </div>
        <div class="col-md-4">
          <div class="s-box"></div>
        </div>
        <div class="col-md-4">
          <div class="s-description-r">
            <h5>Header Text</h5>
            <p class="s-description">Lorem ipsum dolor sit amet, consectetur adipiscing elit ut aliquam, purus sit amet luctus venenatis, lextus magna fringilla urna, porttitor rhoncus dolor purus non enim dolor.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Home',
  components: {
  },
  data() {
    return {

    }
  },
  mounted() {
  },

  methods: {


  },

}
</script>

<style scoped>

.s-description-r {
  margin-top: 320px;
}
.btn-outline-dark {
  margin-left: 5px;
}
.s-box {
  width: 450px;
  height: 500px;
  background: #c4c4c4;
}
.sub-title {
  width: 450px;
  color: #636262;
}
.s-description {
  width: 250px;
  color: #636262;
}
.frontBox {
  background: #9d9d9d;
  height: 230px;
  width: 230px;
  position: absolute;
  margin-right: -450px !important;
  
}
.backBox {
  background: #c4c4c4;
  height: 450px;
  width: 450px;
  margin-top: 65px;
}
.lorem {
  margin-top: 65px;
}
h1 {
  font-size: 66px;
}
.firstRow {
  padding: 50px;
  height: 700px;
}
.secondRow {
  padding: 50px;
  height: 700px;
}

.body1 {
  margin-top: 100px;
  padding: 20px;
}


</style>
