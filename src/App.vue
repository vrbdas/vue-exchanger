<script setup>
    import InputComp from './components/InputComp.vue';
    import SelectComp from './components/SelectComp.vue';
</script>

<template>
    <main>
        <h1>crypto</h1>
        <InputComp :changeAmount="changeAmount" />
        <div class="selects">
            <SelectComp/>
            <SelectComp/>
        </div>
        {{ amount }}
    </main>
</template>

<script>
    export default {
        data() {
            return {
                amount: 0,
            }
        },
        methods: {
            changeAmount(val) {
                this.amount = val;
            }
        }
    }

</script>

<style scoped>
   main {
    padding: 50px;
    display: flex;
    flex-direction: column;
    gap: 20px;
    max-width: 500px;
   }
    h1 {
        text-transform: uppercase;
        font-weight: 900;
        font-size: 2rem;
        text-align: center;
    }
    .selects {
        display: flex;
        justify-content: space-between;
    }
</style>
