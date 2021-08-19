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
</template>

<script>
export default {
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
            counterSoul: 0
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
        }
    },
    methods: {
       activeDetail(e) {
           if (e.target.classList.contains(this.availableProc)) {
               e.target.classList.add(this.activeItem, this.activeProc);
               e.target.classList.remove(this.availableProc)
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
               this.installBiomech++
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
               this.installSoul++
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
    },
}
</script>

<style>

</style>