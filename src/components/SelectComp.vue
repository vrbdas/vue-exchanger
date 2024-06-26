<script setup>
const props = defineProps(['setCrypto', 'crypto']);
</script>

<template>
  <ul>
    <li @click="setCrypto('BTC')" :class="(crypto == 'BTC') ? 'active' : ''">BTC</li>
    <li @click="setCrypto('ETH')" :class="(crypto == 'ETH') ? 'active' : ''">ETH</li>
    <li @click="setCrypto('USDT')" :class="(crypto == 'USDT') ? 'active' : ''">USDT</li>
  </ul>
</template>

<script>

export default {
    data() {
        return {
            
        }
    },
    methods: {

    },
}

</script>

<style scoped>
    ul {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 10px;
        border-radius: 5px;
        padding: 5px 10px;
        font-size: 1rem;
        width: 100%;
    }
    li {
        list-style: none;
        background-color: #e3e3e3;
        padding: 5px 10px;
        cursor: pointer;
        width: 100%;
    }
    li:hover {
        transition: 0.3s all;
        transform: translateX(10px);
    }
    .active {
        background-color: coral;
    }
</style>