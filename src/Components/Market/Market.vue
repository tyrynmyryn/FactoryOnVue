<template>
  <section class="market">
        <div class="container">
            <div class="sidebar sidebar__market">03</div>
            <div class="market__wrapper">
                <h2 class="title market__title">Рынок комплектующих</h2>
                <div class="market__items">
                    <div class="market__item">
                        <div class="img__container"><img src="@/img/market/biomech.svg" alt="biomech" class="item__img"></div>
                        <div class="item__title">Биомеханизм</div>
                        <div class="item__cost  cost_biomech">Стоимость: <span>7 монет</span></div>
                        <div onmousedown="return false" 
                        onselectstart="return false" 
                        :class="[btn, totalCoins >= biomechCost ? active : disabled, typeOfBtn]"
                        @click="getNameOfDetail(biomechCost)"
                        >Установить</div>
                    </div>
                    <div class="market__item">
                        <div class="img__container"><img src="@/img/market/proc.svg" alt="biomech" class="item__img"></div>
                        <div class="item__title">Процессор</div>
                        <div class="item__cost cost_proc">Стоимость: <span>5 монет</span></div>
                        <div onmousedown="return false" 
                        onselectstart="return false" 
                        :class="[btn, totalCoins >= procCost ? active : disabled, typeOfBtn]"
                        @click="getNameOfDetail(procCost)"
                        >Установить</div>
                    </div>
                    <div class="market__item">
                        <div class="img__container"><img src="@/img/market/soul.svg" alt="biomech" class="item__img"></div>
                        <div class="item__title">Душа</div>
                        <div class="item__cost cost_soul">Стоимость: <span>25 монет</span></div>
                        <div 
                        onmousedown="return false" 
                        onselectstart="return false" 
                        :class="[btn, totalCoins >= soulCost ? active : disabled, typeOfBtn]"
                        @click="getNameOfDetail(soulCost)"
                        >Установить</div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import './Market.scss';
export default {
    data() {
        return {
            biomechCost: 7,
			procCost: 5,
			soulCost: 25,
            name: '',
            btn: 'btn',
            active: 'btn_main',
            disabled: 'btn_disabled',
            typeOfBtn: 'item__btn',
            btnState: false
        }
    },
    props: {
        totalCoins: {
            type: Number
        }
    },
    methods: {
        getNameOfDetail(cost) {
            if (cost === this.biomechCost) {
                this.name = 'biomech'
            } else if (cost === this.procCost) {
                this.name = 'proc'
            } else if (cost === this.soulCost) {
                this.name = 'soul'
            }
            this.$emit('buyDetail', this.name, cost)
        }
    }
}
</script>

<style>

</style>