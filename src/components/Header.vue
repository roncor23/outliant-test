<template>
    <nav class="navbar fixed-top navbar-expand-lg">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Logo</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="d-flex justify-content-center">

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
              <li class="nav-item">
                <router-link class="nav-link" to="/">Home</router-link>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">About</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">Services</a>
              </li>
              <li class="nav-item">
                <router-link class="nav-link" to="/products">Products</router-link>
              </li>
            </ul>
        </div>

        </div>
        <form class="d-flex" role="search">
            <button class="btn btn-dark calltoAction" type="submit">Call to action</button>
          </form>
      </div>
    </nav>
</template>
<style scoped>
    .nav-item .nav-link {
    margin-left: 30px;
    padding: 20px;
    }
    .navbar-brand {
    margin-left: 70px;
    }
    .calltoAction {
    margin-right: 70px;
    }
</style>