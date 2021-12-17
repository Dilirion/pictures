<template>
    <div>
        <div class="brand" style="width: 48px;"></div>
        <div class="d-flex align-items-center">
            <div class="nav-item ms-5 myh5 p-0"><a class="nav-link p-0" v-bind:class="{'text-black-brown': isTop, 'text-darkgray': isBottom}" href="#">Каталог</a></div>
            <div class="nav-item ms-5 myh5 p-0"><a class="nav-link p-0" v-bind:class="{'text-black-brown': isTop, 'text-darkgray': isBottom}" href="#">Доставка</a></div>          
            <div class="nav-item ms-5 myh5 p-0"><a class="nav-link p-0" v-bind:class="{'text-black-brown': isTop, 'text-darkgray': isBottom}" href="#">Оплата</a></div>
            <div class="nav-item ms-5 myh5 p-0"><a class="nav-link p-0" v-bind:class="{'text-black-brown': isTop, 'text-darkgray': isBottom}" href="#">Контакты</a></div>
            <div class="nav-item ms-5 myh5 p-0"><a class="nav-link p-0" v-bind:class="{'text-black-brown': isTop, 'text-darkgray': isBottom}" href="#">О компании</a></div>
        </div>
    </div>
</template>

<script>

export default {
    props: {
        'isTop': {type: Boolean, default: true},
        'isBottom': {type: Boolean, default: false}
    },
}
</script>
