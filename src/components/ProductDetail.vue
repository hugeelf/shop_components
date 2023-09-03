<template>
    <div>
        <h3>{{ product.name }}</h3>
        <button v-for="currency in money" :key="currency.id" @click="setCurrency(currency)"> {{ currency }}</button>
        <br>
        <p v-if="selectedCurrency === 'RUB'">
            {{ formattedPriceRub }}
        </p>
        <p v-else>
            {{ formattedPriceUsd }}
        </p>
        <p v-if="product.available">
            Available
        </p>
        <p v-else>
            Our of stock
        </p>
    </div>
</template>

<script>
export default {
    name: 'ProductDetail',

    data() {
        return {
            product: {
                name: 'Product name here',
                price: 99.99,
                available: true,
            },
            money:['RUB', 'USD'],   
            selectedCurrency: 'USD', 
            rubCourse: 96,
        };
    },

    mounted() {
        
    },

    methods: {
        setCurrency(currency){
            this.selectedCurrency = currency;
        }
    },
    computed: {
        formattedPriceUsd() {
            return `$ ${this.product.price}`;
        },
        formattedPriceRub(){
            return `${parseFloat(this.product.price * this.rubCourse).toFixed(2)} RUB`
        }
    },
};
</script>

<style lang="scss" scoped>

</style>