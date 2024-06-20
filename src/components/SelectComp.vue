<script setup>

</script>

<template>
  <ul>
    <li>Bitcoin</li>
    <li>ETH</li>
    <li>USDT</li>
  </ul>
</template>

<script>

export default {
    data() {
        return {

        }
    },
    methods: {

    }
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
        background-color: #c9f2ff;
        min-width: 200px;
    }
    li {
        list-style: none;
    }
</style>