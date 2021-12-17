<template>
  <div class="header border-bottom border-gray border-1 d-flex align-items-center">
    <nav class="navbar navbar-expand-lg">
      <div class="collapse navbar-collapse">
        <base-menu></base-menu>
        <div class="ms-auto">
          <form class="d-flex m-0" @submit="submitForm">
            <input id="input" class="myh5" type="text" placeholder="Поиск по названию картины" 
              v-model="search_str" @input="$emit('search', $event.target.value)">
            <base-button id="button" type="submit" value="Найти"></base-button>
          </form>
        </div>
      </div>
    </nav>
  </div>  
</template>

<script>
import BaseButton from './BaseButton.vue'
import BaseMenu from './BaseNavbarMenu.vue'

export default {
  data: function() {
    return {
      search_str: ""
    }
  },
  methods: {
    submitForm(e) {
      this.$emit('submit', e, this.search_str)      
      this.search_str = ""
    }
  },
  components: {
    BaseButton, BaseMenu
  }
}
</script>


<style scoped>
#input {
  height: 48px;
  width: 294px;
  background-color: #F6F3F3;
  border: 1px solid #E1E1E1;
  border-radius: 0px;
  padding-left: 16px;
  padding-top: 13px;
  padding-bottom: 14px;
}
#input:focus {
  border: 1px solid #B5B5B5;;
  border-radius: 0px;
  box-shadow: 0px;
  outline: 0px;
}
#button {
  width: 122px;
}
.header {
  width: 100%;
  height: 97px;
  margin-top: -1px;
  border: solid;
}
.navbar{
  width:63%;
  margin-left: auto;
  margin-right: auto;
}
</style>
