<template>
  <div class="create">
        <div
        @click="createRobot"
        onmousedown="return false" 
        onselectstart="return false" 
        class="btn-create-robot btn"
        :class="totalCoins >= 10 && checkType && checkSex && installProc + installBiomech + installSoul === 9 ? btnActive : btnDisabled"
        >Произвести за 10 монет
        </div>
        <div class="create__descr" v-if="biomech && proc && soul && money">
            Для производства биоробота не хватает
            {{biomech}},
            {{proc}},
            {{soul}} и
            {{money}}
        </div>
        <div class="create__descr" v-else-if="!biomech && proc && soul && money">
            Для производства биоробота не хватает
            {{proc}},
            {{soul}} и
            {{money}}
        </div>
        <div class="create__descr" v-else-if="!biomech && proc && soul && !money">
            Для производства биоробота не хватает
            {{proc}} и
            {{soul}}
        </div>
        <div class="create__descr" v-else-if="biomech && !proc && soul && !money">
            Для производства биоробота не хватает
            {{biomech}} и
            {{soul}}
        </div>
        <div class="create__descr" v-else-if="biomech && proc && !soul && !money">
            Для производства биоробота не хватает
            {{biomech}} и
            {{proc}}
        </div>
        <div class="create__descr" v-else-if="!biomech && !proc && soul && !money">
            Для производства биоробота не хватает
            {{soul}}
        </div>
        <div class="create__descr" v-else-if="!biomech && proc && !soul && !money">
            Для производства биоробота не хватает
            {{proc}}
        </div>
        <div class="create__descr" v-else-if="biomech && !proc && !soul && !money">
            Для производства биоробота не хватает
            {{biomech}}
        </div>

        <div class="create__descr" v-else-if="!biomech && !proc && soul && money">
            Для производства биоробота не хватает
            {{soul}} и
            {{money}}
        </div>
        <div class="create__descr" v-else-if="!biomech && proc && !soul && money">
            Для производства биоробота не хватает
            {{proc}} и
            {{money}}
        </div>
        <div class="create__descr" v-else-if="biomech && !proc && !soul && money">
            Для производства биоробота не хватает
            {{biomech}} и
            {{money}}
        </div>
        <div class="create__descr" v-else-if="biomech && !proc && soul && money">
            Для производства биоробота не хватает
            {{biomech}},
            {{soul}} и
            {{money}}
        </div>
        <div class="create__descr" v-else-if="biomech && proc && !soul && money">
            Для производства биоробота не хватает
            {{biomech}},
            {{proc}} и
            {{money}}
        </div>
        <div class="create__descr" v-else-if="!biomech && !proc && !soul && money">
            Для производства биоробота не хватает
            {{money}}
        </div>
        <div class="create__descr" v-else-if="biomech && proc && soul && !money">
            Для производства биоробота не хватает
            {{biomech}},
            {{proc}} и
            {{soul}}
        </div>
        <div class="create__descr" v-else-if="!biomech && !proc && !soul && !money">
            
        </div>
    </div>
</template>

<script>
export default {
    props: {
        installProc: {
            type: Number
        },
        installBiomech: {
            type: Number
        },
        installSoul: {
            type: Number
        },
        checkType: {
            type: Boolean
        },
        checkSex: {
            type: Boolean
        },
        descr: {
            type: Object
        },
        totalCoins: {
            type: Number
        },
        numOfBiomech: {
            type: Number
        },
        numOfProc: {
            type: Number
        },
        numOfSoul: {
            type: Number
        }
    },
    data() {
        return {
            btnActive: 'btn_prod',
            btnDisabled: 'btn_prod_disabled',
            creationCost: -10,
        }
    },
    methods: {
        createRobot(e) {
            let {type, sex} = this.descr
            let container = document.querySelector('.prod__result')
            if (e.target.classList.contains(this.btnActive)) {
                if (type === 'front' && sex === "male") {
                    container.innerHTML = '<div class="robot front-male_ready"></div>'
                } else if (type === 'front' && sex === "female") {
                    container.innerHTML = '<div class="robot front-female_ready"></div>'
                } else if (type === 'design' && sex === "male") {
                    container.innerHTML = '<div class="robot design-male_ready"></div>'
                } else {
                    container.innerHTML = '<div class="robot design-female_ready"></div>'
                }
                let procContainer = document.querySelectorAll('.prod__proc')
                let biomechContainer = document.querySelectorAll('.prod__biomech')
                let soulContainer = document.querySelectorAll('.prod__soul')

                for (let i = 0; i < 4; i++) {
                    procContainer[i].classList.remove('prod__proc_active', 'prod__item_active')
                    procContainer[i].classList.add('prod__proc_none')
                    if (this.numOfProc <= 4) {
                       for (let i = 0; i < this.numOfProc; i++) {
                        procContainer[i].classList.add('prod__proc_available')
                        } 
                    } else {
                        for (let i = 0; i < 4; i++) {
                        procContainer[i].classList.add('prod__proc_available')
                        } 
                    }
                }
                for (let i = 0; i < 4; i++) {
                    biomechContainer[i].classList.remove('prod__biomech_active', 'prod__item_active')
                    biomechContainer[i].classList.add('prod__biomech_none')
                    if (this.numOfBiomech <= 4) {
                        for (let i = 0; i < this.numOfBiomech; i++) {
                        biomechContainer[i].classList.add('prod__biomech_available')
                        }
                    } else {
                        for (let i = 0; i < 4; i++) {
                        biomechContainer[i].classList.add('prod__biomech_available')
                        }
                    }
                }
                for (let i = 0; i < 1; i++) {
                    soulContainer[i].classList.remove('prod__soul_active', 'prod__item_active')
                    soulContainer[i].classList.add('prod__soul_none')
                    if (this.numOfSoul <= 1) {
                    for (let i = 0; i < this.numOfSoul; i++) {
                            soulContainer[i].classList.add('prod__soul_available')
                        } 
                    } else {
                        for (let i = 0; i < 1; i++) {
                            soulContainer[i].classList.add('prod__soul_available')
                        }
                    }
                }
                e.target.classList.remove(this.btnActive);
                    e.target.classList.add(this.btnDisabled);
                this.$emit('resetActiveDetails', this.creationCost)
            }
            const modalCreate = document.querySelector('.modal_create')
            modalCreate.style.display = 'block';
        },
    },
    computed: {
        biomech() {
            return 4 - this.installBiomech === 4 ? 'биомеханизмов' : (4 - this.installBiomech != 0 ? 4 - this.installBiomech + ' биомеханизма' : '')
        },
        proc() {
            return 4 - this.installProc === 4 ? 'процессоров' : (4 - this.installProc != 0 ? 4 - this.installProc + ' процессора' : '')
        },
        soul() {
            return 1 - this.installSoul === 1 ? 'души' : ''
        },
        money() {
            return this.totalCoins >=10 ? '' : 'денег'
        }
    }
}
</script>

<style>

</style>