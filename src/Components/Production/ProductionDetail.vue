<template>
   <div class="prod__parts">
        <div class="prod__biomechs">
            <div v-for="(detail, idx) in 4"
            :key="idx" 
            class="prod__item prod__biomech prod__biomech_none"
            @click="activeDetail"/>
        </div>
        <div class="prod__procs">
            <div v-for="(detail, idx) in 4"
            :key="idx + 5"
            class="prod__item prod__proc prod__proc_none"
            @click="activeDetail"
            />
        </div>
        <div class="prod__souls">
            <div
            class="prod__item prod__soul prod__soul_none"
            @click="activeDetail"
            />
        </div>
    </div>
    <ProductionCreate
        :descr="descr"
        :installProc="installProc"
        :installBiomech="installBiomech"
        :installSoul="installSoul"
        :checkType="checkType"
        :checkSex="checkSex"
        :totalCoins="totalCoins"
        :numOfBiomech="numOfBiomech"
        :numOfProc="numOfProc"
        :numOfSoul="numOfSoul"
        @resetActiveDetails="resetActiveDetails"
    />
</template>

<script>
import ProductionCreate from './ProcutionCreate.vue'
export default {
    components: {
        ProductionCreate
    },
    data() {
        return {
            item: 'prod__item',
            disabledItem: 'prod__item',
            activeItem: 'prod__item_active',
            biomechItem: 'prod__biomech',
            procItem: 'prod__proc',
            soulItem: 'prod__soul',

            noneBiomech: 'prod__biomech_none',
            availableBiomech: 'prod__biomech_available',
            activeBiomech: 'prod__biomech_active',

            noneProc: 'prod__proc_none',
            availableProc: 'prod__proc_available',
            activeProc: 'prod__proc_active',

            noneSoul: 'prod__soul_none',
            availableSoul: 'prod__soul_available',
            activeSoul: 'prod__soul_active',

            arrayForFourDetails: [0, 1, 2, 3],
            nameOfDetail: '',
            rightClassArray: [],

            installBiomech: 0,
            installProc: 0,
            installSoul: 0,

            counterBiomech: 0,
            counterProc: 0,
            counterSoul: 0,

            creationCost: 0
        }
    },
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
        checkType: {
            type: Boolean
        },
        checkSex: {
            type: Boolean
        },
        totalCoins: {
            type: Number
        },
        descr: {
            type: Object
        },
    },
    methods: {
       activeDetail(e) {
           if (e.target.classList.contains(this.availableProc)) {
               e.target.classList.add(this.activeItem, this.activeProc);
               e.target.classList.remove(this.availableProc, this.noneProc)
               if (this.installProc === 4) {
                   this.installProc = 0
                   this.installProc++
               }
               this.installProc++
               this.counterProc = -1
               this.counterBiomech = 0
               this.counterSoul = 0
           } else if (e.target.classList.contains(this.activeProc)){
                e.target.classList.add(this.availableProc);
                e.target.classList.remove(this.activeItem, this.activeProc)
                this.installProc--
                this.counterProc = 1
                this.counterBiomech = 0
                this.counterSoul = 0
           } else if (e.target.classList.contains(this.noneProc)) {
               this.counterBiomech = 0
               this.counterProc = 0
               this.counterSoul = 0
           }
           if (e.target.classList.contains(this.availableBiomech)) {
               e.target.classList.add(this.activeItem, this.activeBiomech);
               e.target.classList.remove(this.availableBiomech)
               if (this.installBiomech === 4) {
                   this.installBiomech = 0
                   this.installBiomech++
               } else {
                   this.installBiomech++
               }
               this.counterBiomech = -1
                this.counterProc = 0
                this.counterSoul = 0
           } else if (e.target.classList.contains(this.activeBiomech)){
                e.target.classList.add(this.availableBiomech);
                e.target.classList.remove(this.activeItem, this.activeBiomech)
                this.installBiomech--
                this.counterBiomech = 1
                this.counterProc = 0
                this.counterSoul = 0
           } else if (e.target.classList.contains(this.noneBiomech)) {
               this.counterBiomech = 0
               this.counterProc = 0
               this.counterSoul = 0
           }
           if (e.target.classList.contains(this.availableSoul)) {
               e.target.classList.add(this.activeItem, this.activeSoul);
               e.target.classList.remove(this.availableSoul)
                if (this.installSoul === 1) {
                   this.installSoul = 0
                   this.installSoul++
               } else {
                   this.installSoul++
               }
               this.counterSoul = -1
               this.counterBiomech = 0
               this.counterProc = 0
           } else if (e.target.classList.contains(this.activeSoul)){
                e.target.classList.add(this.availableSoul);
                e.target.classList.remove(this.activeItem, this.activeSoul)
                this.installSoul--
                this.counterSoul = 1
                this.counterBiomech = 0
                this.counterProc = 0
           } else if (e.target.classList.contains(this.noneSoul)) {
               this.counterBiomech = 0
               this.counterSoul = 0
               this.counterProc = 0
           }
            this.$emit('detailsAfterInstall', this.counterProc, this.counterBiomech, this.counterSoul, this.installProc, this.installBiomech, this.installSoul)
       },
       resetActiveDetails(creationCost) {
           this.installBiomech = 0
            this.installProc = 0
           this.installSoul = 0
           this.creationCost = creationCost
           this.$emit('resetActiveDetails', this.creationCost)
       }
    },
}
</script>

<style>

</style>