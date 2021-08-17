<template>
  <section class="store">
        <div class="container">
            <div class="sidebar sidebar__store">04</div>
            <div class="store__wrapper">
                <h2 class="title store__title">Склад</h2>
                <div class="store__items">
                    <div class="store__item">
                        <div class="item__title">Биомеханизм</div>
                        <div class="item__cost sell-cost_biomech">Стоимость: <span>{{biomechSellCost}} монет</span></div>
                        <div class="item__amount item__amount_biomech">{{numOfBiomech}} шт</div>
                        <div 
                        onmousedown="return false" 
                        onselectstart="return false" 
                        :class="[btn, numOfBiomech > 0 ? active : disabled, typeOfBtn]"
                        @click="getNameOfDetail(biomechSellCost)"
                        >Продать</div>
                    </div>
                    <div class="store__item">
                        <div class="item__title">Процессор</div>
                        <div class="item__cost sell-cost_proc">Стоимость: <span>{{procSellCost}} монет</span></div>
                        <div class="item__amount item__amount_proc">{{numOfProc}} шт</div>
                        <div 
                        onmousedown="return false" 
                        onselectstart="return false" 
                        :class="[btn, numOfProc > 0 ? active : disabled, typeOfBtn]"
                        @click="getNameOfDetail(procSellCost)"
                        >Продать</div>
                    </div>
                    <div class="store__item">
                        <div class="item__title">Душа</div>
                        <div class="item__cost sell-cost_soul">Стоимость: <span>{{soulSellCost}} монет</span></div>
                        <div class="item__amount item__amount_soul">{{numOfSoul}} шт</div>
                        <div 
                        onmousedown="return false" 
                        onselectstart="return false" 
                        :class="[btn, numOfSoul > 0 ? active : disabled, typeOfBtn]"
                        @click="getNameOfDetail(soulSellCost)"
                        >Продать</div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    props: {
        numOfBiomech: {
            type: Number,
            default: 0
        }, 
        numOfProc: {
            type: Number,
            default: 0
        },
        numOfSoul: {
            type: Number,
            default: 0
        },
    },
    data() {
        return {
            biomechSellCost: 5,
            procSellCost: 3,
            soulSellCost: 15,
            name: '',
            btn: 'btn',
            disabled: 'btn_store_disabled',
            active: 'btn_store',
            typeOfBtn: 'item__btn'
        }
    },
    methods: {
        getNameOfDetail(cost) {
            if (cost === this.biomechSellCost) {
                this.name = 'biomech'
            } else if (cost === this.procSellCost) {
                this.name = 'proc'
            } else if (cost === this.soulSellCost) {
                this.name = 'soul'
            }
            this.$emit('sellDetail', this.name, cost)
        }
    }
}
</script>

<style>

</style>