<template>
  <div class="header border-bottom border-gray border-1 d-flex align-items-center">
    <nav class="navbar navbar-expand-lg">
      <div class="collapse navbar-collapse">
        <base-menu isTop:false isBottom:true></base-menu>
        <div class="ms-auto">
            <div class="d-flex">
                <p class="myh5 text-darkgray m-0">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-telephone-fill" viewBox="0 0 16 16">
                      <path fill-rule="evenodd" d="M1.885.511a1.745 1.745 0 0 1 2.61.163L6.29 2.98c.329.423.445.974.315 1.494l-.547 2.19a.678.678 0 0 0 .178.643l2.457 2.457a.678.678 0 0 0 .644.178l2.189-.547a1.745 1.745 0 0 1 1.494.315l2.306 1.794c.829.645.905 1.87.163 2.611l-1.034 1.034c-.74.74-1.846 1.065-2.877.702a18.634 18.634 0 0 1-7.01-4.42 18.634 18.634 0 0 1-4.42-7.009c-.362-1.03-.037-2.137.703-2.877L1.885.511z"/>
                    </svg>
                    +7 (812) 555-55-55
                </p>
                <p id="geo" class="myh5 text-darkgray">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-geo-alt-fill" viewBox="0 0 16 16">
                      <path d="M8 16s6-5.686 6-10A6 6 0 0 0 2 6c0 4.314 6 10 6 10zm0-7a3 3 0 1 1 0-6 3 3 0 0 1 0 6z"/>
                    </svg>
                    г. Санкт-Петербург, ул. Ефимова, 3
                </p>
            </div>
        </div>
      </div>
    </nav>
  </div>  
</template>

<script>
import BaseMenu from './BaseNavbarMenu.vue'

export default {
  components: {
    BaseMenu
  }
}
</script>

<style scoped>
.header {
  width: 100%;
  height: 96px;
  border: none;
  background-color: #ECEAEA;
}
.navbar{
  width: 65.78%;
  margin-left: 18.33%;
  margin-right: 15.89%;
}
#geo {
    margin:0px;
    margin-left: 54px;
}
</style>