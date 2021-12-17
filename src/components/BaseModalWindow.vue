<template>
    <transition name="modal-fade">
        <div v-if="picture" class="h-100 w-100 position-absolute top-0 start-0 bottom-0 end-0 
            d-flex justify-content-center align-items-center" style="background: rgba(85, 85, 85, 0.7)">
            <div class="card border-1 border-gray rounded-0 bg-background-color p-3" style="max-width: 600px">
                <div class="w-100 text-align-end">
                    <button type="button" class="btn-close position-absolute top-0 end-0 text-brown"
                        @click="$emit('close')"></button>
                </div>
                <div class="d-flex align-items-center flex-column" 
                    style="width: 100px, height: 200px">
                    <p id="title" class="myh1 text-black-brown p-0 mb-0"> &laquo;{{picture.title}}&raquo;</p>
                    <p id="title" class="myh3 text-black-brown p-0"> {{picture.author}}</p>
                    <!-- image slider -->
                    <div class="d-flex flex-coloumn align-items-center" style="width:500px">
                        <transition-group class='d-flex justify-content-center align-items-center overflow-hidden' 
                            style="width: 24em, min-height: 25em;" tag="div">  
                            <div class="slide" v-for="photo in picture.photos" :key="photo.id">                                  
                                <img  :src="require( `../assets/img/${photo.img}.jpg`)" 
                                    :alt="picture.title">                        
                            </div>                               
                        </transition-group>
                    </div>
                    <div v-if="picture.photos" class="mt-1">
                        <button class='p-0 me-1 border-0' @click="previous">
                            <span class="carousel-control-prev-icon bg-brown m-0 p-0 border-0" aria-hidden="true"></span>
                        </button> 
                        <button class='p-0 border-0' @click="next">
                            <span class="carousel-control-next-icon bg-brown m-0 p-0" aria-hidden="true"></span>
                        </button>
                    </div>
                    <div class="d-flex align-items-start flex-column">
                        <div v-if="picture.description">
                            <p class="myh2 text-black-brown"> Описание:</p>
                            <p class="myh5 text-black-brown" cols="40">{{picture.description}}</p>
                        </div>
                        <div class="d-flex align-items-start flex-column">
                            <p class="myh2 text-black-brown" style=""> Цена:</p>
                            <p v-if="picture.oldprice" class="myh6 text-light m-0">{{picture.oldprice}} $</p>
                            <p class="myh3 text-black-brown m-0 display-6">{{picture.price}} $</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </transition>
</template>

<script>

export default {
    
    props: {
        "picture": Object
    },
    methods: {
        next () {
            const first = this.picture.photos.shift()
            this.picture.photos = this.picture.photos.concat(first)
        },
        previous () {
            const last = this.picture.photos.pop()
            this.picture.photos = [last].concat(this.picture.photos)
        }
    }
}

</script>

<style scoped>
.slide {
  flex: 0 0 20em;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: transform 0.3s ease-in-out;
  width: 300px
  
}
.slide:first-of-type {
  opacity: 0;
}
.slide:last-of-type {
  opacity: 0;
}
.modal-fade-enter,
.modal-fade-leave-to {
    opacity: 0;
}

.modal-fade-enter-active,
.modal-fade-leave-active {
    transition: opacity .5s ease;
}
</style>
