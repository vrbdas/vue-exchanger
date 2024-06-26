<script setup>
    const props = defineProps(['changeAmount', 'convert', 'setError']);
</script>

<template>
    <input v-model="input" type="text" @input="inputCheck($event.target.value)" autocomplete="off">
    <button @click="convert">convert</button>
</template>

<script>

export default {
    data() {
        return {

        }
    },
    methods: {
        inputCheck(input) {
            if (!/^\d+$/.test(input) && input.length !== 0) {
                this.setError('You can input only numbers');
            } else {
                this.setError('');
                this.changeAmount(input);
            }
        },
    }
}

</script>

<style scoped>
    input {
        width: 100%;
        border-radius: 5px;
        border: none;
        height: 30px;
        background-color: #d7f5ff;
        outline: none;
        font-size: 1rem;
        padding: 5px 10px;
    }
    .input-wrapper {
        width: 100%;
        position: relative;
    }
    button {
        width: 100%;
        height: 40px;
        text-transform: uppercase;
        border: none;
        border-radius: 5px;
        background-color: #6eb8f9;
        cursor: pointer;
        padding: 5px 10px;
    }
</style>