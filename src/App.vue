<template>
  <div id="app">
      <top-navbar @search="search" @submit="onsearch"></top-navbar>
      <div id="container">
        <p id="header" class="text-start myh1 text-black-brown">{{header}}</p>              
        <div class="d-flex justify-content-center" v-if="showedData">          
            <base-card v-for="(item, id) in showedData" :key="id" :picture="item" :number="id" 
              id="pictures" @show="showModal"></base-card>
        </div>        
      </div>              
      <bottom-navbar id="bottomnavbar"></bottom-navbar>
      <base-modal-window v-if="modalVisibility" :picture="modalPicture" @close="closeModal"></base-modal-window>
  </div>
</template>

<script>
import TopNavbar from './components/TheTopNavbar.vue'
import BaseCard from './components/BaseCard.vue'
import BottomNavbar from './components/TheBottomNavbar.vue'
import BaseModalWindow from './components/BaseModalWindow.vue'

export default {
  components: {
      TopNavbar, BaseCard, BottomNavbar, BaseModalWindow
  },
  data() {
    return {
      myData: [],
      showedData: [],
      header: "Картины эпохи возраждения",
      modalVisibility: true,
      modalPicture: null
    };
  },
  mounted() {
    fetch('http://localhost:3000/data')
    .then(res => res.json())
    .then(data => {this.myData = data, this.showedData = data})    
    .catch(err => console.log(err.message))
  },
  methods: {
    // search when user typing the word
    search(str) {
      this.header = "Картины эпохи возраждения"
      this.showedData = []
      this.myData.forEach(picture => {
        if (picture.title.toUpperCase().includes(str.toUpperCase())) {
          this.showedData.push(picture) 
        }
      });
    },
    // preventing page reloading after search form was submitted
    onsearch(e,str) {
      e.preventDefault()
      if(str) this.header = "Результаты поиска для запроса " + str
      else {
        this.header = "Картины эпохи возраждения"
        this.showedData = this.myData
      }
    },
    // closing the picture modal element
    closeModal() {
      this.modalVisibility = false
      console.log(this.modalVisibility)
    },
    // closing the picture modal element
    showModal(number) {
      this.modalPicture = JSON.parse(JSON.stringify(this.showedData[number]))
      this.modalVisibility = true
    }
  }
};
</script>

<style>
#header {
  margin-top: 45px;
}
#container {
  width: 63.3%;
  margin-left: auto;
  margin-right: auto;
}
#bottomnavbar {
  position: absolute;
  bottom: 0px;
}
#pictures {
  margin-top: 39px;
  margin-right: 32px;
}
</style>