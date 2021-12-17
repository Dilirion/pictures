<template>
    <button id="button" :disabled="clicked" @click.stop="loadState" :class="{'active': bought}" 
        class="myh4 text-white d-flex justify-content-center align-items-center">
        <!-- visual reperesentation of loading state -->
        <div class="spinner-border p-0 m-0" v-if="clicked" role="status"></div>
        <!-- visual reperesentation of shop state -->
        <svg v-if="bought" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-check2 me-1" viewBox="0 0 16 16">
            <path d="M13.854 3.646a.5.5 0 0 1 0 .708l-7 7a.5.5 0 0 1-.708 0l-3.5-3.5a.5.5 0 1 1 .708-.708L6.5 10.293l6.646-6.647a.5.5 0 0 1 .708 0z"/>
        </svg>
        {{button_value}}</button>
</template>

<script>
export default ({
    data() {
        return {
            clicked: false,
            bought: false,
            button_value: this.value,
            button_number: this.number
        }
    },
    props: {
       "value": String,
       "number": Number
    },
    mounted() {
        // checking if button state is shop
        if (localStorage.getItem(`${this.button_number}`)) {
            try {
                this.bought = JSON.parse(localStorage.getItem(`${this.button_number}`));
                this.button_value = "В корзине"
            } catch(e) {
                localStorage.removeItem(`${this.button_number}`);
            }
        }
    },
    methods: {
        // changing state for load
        loadState () {
            if (this.button_value == "Купить") {
                this.button_value = '',
                this.clicked = true,
                setTimeout(this.shop, 2000)                
            }
        },
        //changing state for shop
        shop() {
            this.clicked = false,
            this.bought = true,
            localStorage.setItem(`${this.button_number}`, JSON.stringify(this.bought))
            this.button_value = "В корзине"  
        }
    }
})
</script>


<style scoped>
#button {
    background-color: #403432;
    height: 48px;
    padding-top: 13px;
    padding-bottom: 14px;
    border: none;
}
#button:hover {
    background-color: #776763;
}
#button:disabled {
    background-color: #C1B4B1;
}
#button.active {
    background-color: #5B3A32;
}
</style>