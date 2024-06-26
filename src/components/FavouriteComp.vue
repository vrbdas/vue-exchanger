<script setup>
    const props = defineProps(['favs', 'getFromFav']);
</script>

<template>
    <h2>favourites:</h2>
    <div v-for="(item, i) in favs" :key="i" @click="getFromFav(i)">
        <div class="favourite-item">{{ item['from'] }}-{{ item['to'] }}</div>
    </div>
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
    h2 {
        font-size: 1rem;
        font-weight: 500;
        text-transform: uppercase;
        display: flex;
        align-items: center;
    }
    .favourite-item {
        padding: 5px 10px;
        background-color: #f0f8aa;
        cursor: pointer;
        border-radius: 5px;
    }
    .favourite-item:hover {
        transition: 0.3s all;
        transform: scale(1.1);
    }
</style>