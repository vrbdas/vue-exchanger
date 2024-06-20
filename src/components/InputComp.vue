<script setup>
    const props = defineProps(['changeAmount']);
</script>

<template>
    <input v-model="input" id="input" type="text" @input="inputCheck($event.target.value)" autocomplete="off">
    <label class="error" v-show="inputCheckValue" for="input">You can input only numbers</label>
</template>

<script>

export default {
    data() {
        return {
            inputCheckValue: false,
        }
    },
    methods: {
        inputCheck(input) {
            if (!/^\d+$/.test(input) && input.length !== 0) {
                this.inputCheckValue = true;
            } else {
                this.inputCheckValue = false;
                this.changeAmount(input);
            }
        }
    }
}

</script>

<style scoped>
    input {
        border-radius: 5px;
        border: none;
        min-height: 30px;
        background-color: #d7f5ff;
        outline: none;
        padding: 5px 10px;
        font-size: 1rem;
    }
    .error {
        color: red;
    }
    button {
        width: 100px;
        height: 50px;
        text-transform: uppercase;
        border: none;
        border-radius: 5px;
    }
</style>