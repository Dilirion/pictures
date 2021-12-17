<template>
    <div class="card border-1 border-gray bg-background-color" v-bind:class="{'disabled': picture.sailed}" 
    v-if="picture" @click="$emit('show', number)">
        <div id="image" class="card-img-top" v-if="picture.photos" 
            :style="{ 'background-image': 'url(' + require( `../assets/img/${picture.photos[0].img}.jpg`) + ')' }">
        </div>
        <div v-else id="image" class="card-img-top text-brown myh3 d-flex align-items-center">
            Изображение времнно отсутствует
        </div>
        <div class="card-body text-start pr-3">
            <p id="title" class="myh2 text-black-brown p-0"> &laquo;{{picture.title}}&raquo; {{picture.author}}</p>
            <!-- if picture is sailed this block will be replaced by next -->
            <div v-if="!picture.sailed" class="d-flex justify-content-start align-items-center">
                <div class="d-flex align-items-start flex-column">
                    <p v-if="picture.oldprice" class="myh6 text-light m-0">{{picture.oldprice}} $</p>
                    <p class="myh3 text-black-brown m-0">{{picture.price}} $</p>
                </div>
                <base-button id="button" value="Купить" :number="number"></base-button>
            </div>
            <div v-else class="d-flex align-items-center">
                <p id="title" class="d-flex align-items-center myh2 text-black-brown m-0 p-0">
                    Продана на аукционе
                </p>
            </div>
        </div>
    </div>
</template>

<script>
import BaseButton from './BaseButton.vue'

export default {
    props: {
        "picture": Object,
        "number": Number
    },
    components: {
        BaseButton
    }
}
</script>


<style scoped>
#image {
    
    width: 100%;
    height:160px;
}
#button {
    width: 118px;
    margin-left: 21px;
}
#title {
    margin-top: 20px;
    margin-bottom: 22px;
    width: 220px; 
    height: 54px;
}
.card{
    border-radius: 0px;
    cursor: pointer;
    
    width: 280px;
}
.card-img-top {
    border-radius: 0px;
}
.disabled {
    opacity: 40%;
    pointer-events: none;
}
</style>