<script setup>
    import InputComp from './components/InputComp.vue';
    import SelectComp from './components/SelectComp.vue';
</script>

<template>
    <main>
        <h1>crypto</h1>
        <div class="inputs">
            <InputComp :changeAmount="changeAmount" :convert="convert" :setError="setError"/>
            <div class="error">{{ error }}</div>
            <div class="output">{{ output }}</div>
        </div>
        <div class="selects">
            <SelectComp :setCrypto="setCryptoFirst" />
            <SelectComp :setCrypto="setCryptoSecond" />
        </div>
    </main>
</template>

<script>
    export default {
        data() {
            return {
                amount: '',
                cryptoFirst: '',
                cryptoSecond: '',
                error: '',
                output: '',
            }
        },
        methods: {
            changeAmount(val) {
                this.amount = val;
            },
            setCryptoFirst(val) {
                this.cryptoFirst = val;
            },
            setCryptoSecond(val) {
                this.cryptoSecond = val;
            },
            convert() {
                if (this.amount == '') {
                    this.setError('Input number');
                } else if (this.cryptoFirst == '' || this.cryptoSecond == '') {
                    this.setError('Select cryptos');
                    return;
                } else if (this.cryptoFirst == this.cryptoSecond) {
                    this.setError('Select different cryptos');
                    return;
                }
                this.output = this.amount;
            },
            setError(val) {
                this.error = val;
            }
        }
    }

</script>

<style scoped>
   main {
    padding: 50px;
    display: flex;
    flex-direction: column;
    gap: 40px;
    max-width: 500px;
   }
    h1 {
        text-transform: uppercase;
        font-weight: 900;
        font-size: 2rem;
        text-align: center;
    }
    .inputs {
        display: flex;
        justify-content: space-between;
        gap: 40px;
        position: relative;
    }
    .selects {
        display: flex;
        gap: 40px;
        justify-content: space-between;
    }
    .error {
        color: red;
        position: absolute;
        top: 50px;
        left: 10px;
    }
    .output {
        width: 100%;
        border-radius: 5px;
        border: none;
        height: 30px;
        background-color: #d7f5ff;
        outline: none;
        font-size: 1rem;
        padding: 5px 10px;
        display: flex;
        align-items: center;
    }
</style>
