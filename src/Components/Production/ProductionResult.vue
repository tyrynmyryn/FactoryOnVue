<template>
    <div class="prod__result" v-if="descr.type === 'front' && descr.sex === 'male'">
        <div class="robot" :class="this.installProc + this.installBiomech + this.installSoul === 9 ? 'front-male_available' : 'front-male_none'"></div>
    </div>
    <div class="prod__result" v-else-if="descr.type === 'front' && descr.sex === 'female'">
        <div class="robot" :class="this.installProc + this.installBiomech + this.installSoul === 9 ? 'front-female_available' : 'front-female_none'"></div>
    </div>
    <div class="prod__result" v-else-if="descr.type === 'design' && descr.sex === 'male'">
        <div class="robot" :class="this.installProc + this.installBiomech + this.installSoul === 9 ? 'design-male_available' : 'design-male_none'"></div>
    </div>
    <div class="prod__result" v-else-if="descr.type === 'design' && descr.sex === 'female'">
        <div class="robot" :class="this.installProc + this.installBiomech + this.installSoul === 9 ? 'design-female_available' : 'design-female_none'"></div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            
        }
    },
    props: {
        descr: {
            type: Object
        },
        installProc: {
            type: Number,
            default: 0
        },
        installBiomech: {
            type: Number,
            default: 0
        },
        installSoul: {
            type: Number,
            default: 0
        },
    },
    methods: {
        
    }
}
</script>

<style>

</style>