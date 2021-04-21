<template>
    <div id="coinbase">
        <h1>Bitcoin Price Index</h1>
        <div
            v-for="currency in info" :key="currency.usd"
            class="currency"
        >
            {{ currency.description }}:
            <span class="lighten">
                <span v-html="currency.symbol"></span>{{ roundToTwoDecimals(currency.rate_float) }}
            </span>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    name: 'Coinbase',
    data() {
        return {
            info: null
        };
    },
    methods: {
        roundToTwoDecimals: function(value) {
            return value.toFixed(2);
        }
    },
    mounted() {
        axios
        .get('https://api.coindesk.com/v1/bpi/currentprice.json')
        .then(response => {
            this.info = response.data.bpi
        })
        .catch(error => {
            console.log(error);
            this.errored = true;
        })
        .finally(() => {
            this.loading = false;
        })
    }
}
</script>

<style scoped>
    #coinbase {
        color: #B3BFB8;
        margin: 0 auto;
        width: 300px;
        padding: 0 40px 40px;
        background: #2F242C;
        border-radius: 5px;
    }
    .currency {
        background: #2F242C;
    }
    .lighten {
        color: #B3BFB8;
    }

</style>