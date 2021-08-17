<template>
  <section class="pocket">
        <div class="container">
            <div class="sidebar sidebar__pocket">02</div>
            <div class="pocket__wrapper">
                <h2 class="title pocket__title">Кошелёк криптовалют</h2>
                <div class="pocket__coins">
                <div class="pocket__coin" v-for="(coin, idx) in arrayOfCoins" :key="idx" :style="{left: idx * 9 + 'px'}"></div>
                </div>
                <div class="pocket__total"><span>{{totalCoinsMain}}</span> biorobo монет</div>
                <div class="pocket__farm">
                    <div onmousedown="return false"
                    onselectstart="return false"
                    class="pocket__run"
                    @click="farmCoin"
                    >Нацыганить</div>
                    <div class="checkbox">
                        <input 
                        id="run-5" 
                        type="checkbox" 
                        class="run"
                        @change="$emit('changeCheckboxState', checked)"
                        v-model="checked"
                        >
                        <label
                        onmousedown="return false"
                        onselectstart="return false" 
                        for="run-5" 
                        class="run-5-text"
                        >Цыганить по 5 монет</label>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    props: {
        totalCoinsMain: {
            type: Number
        },
        arrayOfCoins: {
            type: Array
        },
        farmCoin: {
            type: Function
        }
    },
    data() {
        return {
            checked: false
        }
    },
    methods: {

    }
}
</script>

<style>

</style>