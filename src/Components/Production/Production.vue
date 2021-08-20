<template>
  <section id="production" class="prod">
        <div class="container">
            <div class="sidebar sidebar__prod">05</div>
            <div class="prod__wrapper">
                <h2 class="title prod__title">Производство </h2>
                <div class="prod__creation">
                    <ProductionType 
                    @getTypeOfRobots="getTypeOfRobots"

                    :installProc="installProc" 
                    :installBiomech="installBiomech" 
                    :installSoul="installSoul"
                    :totalCoins="totalCoins"
                    :numOfBiomech="numOfBiomech"
                    :numOfProc="numOfProc"
                    :numOfSoul="numOfSoul"
                    />
                    <ProductionDetail 
                    @resetActiveDetails="resetActiveDetails"
                    :descr="descr"
                    @detailsAfterInstall="detailsAfterInstall" 
                    :checkType="typeChecked" 
                    :checkSex="sexChecked" 
                    :totalCoins="totalCoins"
                    :numOfBiomech="numOfBiomech"
                    :numOfProc="numOfProc"
                    :numOfSoul="numOfSoul"
                    />
                    <ProductionResult  :typeChecked="typeChecked" :sexChecked="sexChecked" :descr="descr" :installProc="installProc" :installBiomech="installBiomech" :installSoul="installSoul"/>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import ProductionType from './ProductionType.vue'
import ProductionDetail from './ProductionDetail.vue'
import ProductionResult from './ProductionResult.vue'
export default {
    props: {
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
            counterProc: 0,
            counterBiomech: 0,
            counterSoul: 0,
            installProc: 0,
            installBiomech: 0,
            installSoul: 0,

            creationCost: 0,

            typeChecked: false,
            sexChecked: false,
            descr: {
                type: 'front',
                sex: 'male'
            }
        }
    },
    components: {
        ProductionType, ProductionDetail, ProductionResult
    },
    methods: {
        detailsAfterInstall(proc, biomech, soul, installProc, installBiomech, installSoul) {
            this.counterProc = proc;
            this.counterBiomech = biomech;
            this.counterSoul = soul

            this.installProc = installProc
			this.installBiomech = installBiomech
            this.installSoul = installSoul

            this.$emit('detailsAfterInstall', this.counterProc, this.counterBiomech, this.counterSoul, this.installProc, this.installBiomech, this.installSoul)
        },
        getTypeOfRobots(descr, type, sex) {
            this.descr = descr
            this.typeChecked = type,
            this.sexChecked = sex
        },
        resetActiveDetails(creationCost) {
            this.installProc = 0
			this.installBiomech = 0
            this.installSoul = 0,
            this.creationCost = creationCost
            this.$emit('resetActiveDetails', this.creationCost)
        }
    },
}
</script>

<style>

</style>