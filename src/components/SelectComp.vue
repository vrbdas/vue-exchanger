<script setup>
const props = defineProps(['setCrypto']);
</script>

<template>
  <ul>
    <li @click="selectItem('Bitcoin')" :class="(current == 'Bitcoin') ? 'active': ''">Bitcoin</li>
    <li @click="selectItem('ETH')" :class="(current == 'ETH') ? 'active': ''">ETH</li>
    <li @click="selectItem('USDT')" :class="(current == 'USDT') ? 'active': ''">USDT</li>
  </ul>
</template>

<script>

export default {
    data() {
        return {
            current: '',
        }
    },
    methods: {
        selectItem(val) {
            this.setCrypto(val);
            this.current = val;
        },
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