<template>
  <section id="production" class="prod">
        <div class="container">
            <div class="sidebar sidebar__prod">05</div>
            <div class="prod__wrapper">
                <h2 class="title prod__title">Производство </h2>
                <div class="prod__creation">
                    <ProductionType/>
                    <ProductionDetail @detailsAfterInstall="detailsAfterInstall"/>
                    <ProductionResult/>
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
    data() {
        return {
            counterProc: 0,
            counterBiomech: 0,
            counterSoul: 0,
            installProc: 0,
            installBiomech: 0,
            installSoul: 0
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
        }
    }
}
</script>

<style>

</style>