<template>
    <div id="coinDataContainer" v-if="$store.state.crypto.currencyName != ''">
       <div>
            <img :src="$store.state.crypto.logo" width="50" height="50"/>
            <h1>{{$store.state.crypto.currencyName}}</h1>
       </div>
       <candlestick  
            :labels="$store.state.crypto.chartData.labels" 
            :currency-history="$store.state.crypto.chartData.data"/>
        <currency-data-table
            :data="tableCurrencyData" />
    </div>
</template>

<style src="../css/CryptoCurrency.css"/>

<script>
    import {mapGetters} from 'vuex';
    import Candlestick from './CandlestickChart.vue';
    import CurrencyDataTable from './CurrencyDataTable.vue';

   export default {
        components: {
           Candlestick,
           CurrencyDataTable
        },
        computed:{
            ...mapGetters([
                'tableCurrencyData'
            ])
        }
    }
</script>