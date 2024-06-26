<script setup>
    import axios from 'axios';
    import FavouriteComp from './components/FavouriteComp.vue';
    import InputComp from './components/InputComp.vue';
    import SelectComp from './components/SelectComp.vue';
</script>

<template>
    <main>
        <h1>crypto</h1>
        <div class="inputs">
            <InputComp :changeAmount="changeAmount" :convert="convert" :setError="setError" :favourite="favourite"/>
            <div class="error">{{ error }}</div>
            <div class="output">{{ output }}</div>
            <button @click="favourite">favourite</button>
        </div>
        <div class="selects">
            <SelectComp :setCrypto="setCryptoFirst" :crypto="cryptoFirst" />
            <SelectComp :setCrypto="setCryptoSecond" :crypto="cryptoSecond" />
        </div>
        <div class="favourite">
            <FavouriteComp v-if="favs.length > 0" :favourite="favourite" :favs="favs" :getFromFav="getFromFav" />
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
                favs: [],
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
                } else {
                    axios.get(`https://api.coinconvert.net/convert/${this.cryptoFirst}/${this.cryptoSecond}?amount=${this.amount}`).then(
                        value => {
                            this.output = +value['data'][(this.cryptoSecond)].toFixed(4);
                            this.setError('');
                        },
                        error => {
                            this.setError('Network error');
                        }
                    )
                }
            },
            setError(val) {
                this.error = val;
            },
            favourite() {
                if (this.cryptoFirst == '' || this.cryptoSecond == '') {
                    this.setError('Select cryptos');
                    return;
                } else if (this.cryptoFirst == this.cryptoSecond) {
                    this.setError('Select different cryptos');
                    return;
                } else {
                    this.favs.push({
                        from: this.cryptoFirst, 
                        to: this.cryptoSecond,
                    });
                }
            },
            getFromFav(index) {
                this.cryptoFirst = this.favs[index]['from'];
                this.cryptoSecond = this.favs[index]['to'];
            }
        },
        computed: {

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
    .favourite {
        display: flex;
        gap: 20px;
    }
    button {
        width: 100%;
        height: 40px;
        text-transform: uppercase;
        border: none;
        border-radius: 5px;
        background-color: #f0f8aa;
        cursor: pointer;
        padding: 5px 10px;
    }
</style>

