<template>
  <div class="prod__descr">
        <div class="descr__type">
            <div class="descr__title">Тип биоробота:</div>
            <div class="prod__radio">
                <div class="radio">
                    <input @click="getTypeOfRobots" id="front-type" type="radio" class="radio__input" name="type">
                    <label for="front-type" class="radio__label">FrontEnd</label>
                </div>
                <div class="radio">
                    <input @click="getTypeOfRobots" id="designer-type" type="radio" class="radio__input" name="type">
                    <label for="designer-type" class="radio__label">Design</label>
                </div>
            </div>
        </div>
        <div class="descr__sex">
            <div class="descr__title">Cтабилизатор:</div>
            <div class="prod__radio">
                <div class="radio">
                    <input @click="getTypeOfRobots" id="sex-male" type="radio" class="radio__input" name="sex">
                    <label for="sex-male" class="radio__label">Male</label>
                </div>
                <div class="radio">
                    <input @click="getTypeOfRobots" id="sex-female" type="radio" class="radio__input" name="sex">
                    <label for="sex-female" class="radio__label">Female</label>
                </div>
            </div>
        </div>
        <!-- <ProductionCreate
        :installProc="installProc"
        :installBiomech="installBiomech"
        :installSoul="installSoul"
        :checkType="typeChecked"
        :checkSex="sexChecked"
        :descr="descr"
        :totalCoins="totalCoins"
        :numOfBiomech="numOfBiomech"
        :numOfProc="numOfProc"
        :numOfSoul="numOfSoul"

        /> -->
    </div>
</template>

<script>
// import ProductionCreate from './ProcutionCreate.vue'
export default {
    components: {
        // ProductionCreate
    },
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
            descr: {
                type: 'front',
                sex: 'male'
            },
            typeChecked: false,
            sexChecked: false,
        }
    },
    methods: {
        getTypeOfRobots(e) {
            if (e.target.id === 'front-type') {
                this.descr.type = 'front'
                this.typeChecked = true
            } else if (e.target.id === 'designer-type') {
                this.descr.type = 'design'
                this.typeChecked = true
            } else if (e.target.id === 'sex-male') {
                this.descr.sex = 'male' 
                this.sexChecked = true
            } else {
                this.descr.sex = 'female'
                this.sexChecked = true
            }
            this.$emit('getTypeOfRobots', this.descr, this.typeChecked, this.sexChecked)
        },
    }
}
</script>

<style>

</style>