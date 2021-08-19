<template>
  <div class="prod__descr">
        <div class="descr__type">
            <div class="descr__title">Тип биоробота:</div>
            <div class="prod__radio">
                <div class="radio">
                    <input id="front-type" type="radio" class="radio__input" name="type">
                    <label for="front-type" class="radio__label">FrontEnd</label>
                </div>
                <div class="radio">
                    <input id="designer-type" type="radio" class="radio__input" name="type">
                    <label for="designer-type" class="radio__label">Design</label>
                </div>
            </div>
        </div>
        <div class="descr__sex">
            <div class="descr__title">Cтабилизатор:</div>
            <div class="prod__radio">
                <div class="radio">
                    <input id="sex-male" type="radio" class="radio__input" name="sex">
                    <label for="sex-male" class="radio__label">Male</label>
                </div>
                <div class="radio">
                    <input id="sex-female" type="radio" class="radio__input" name="sex">
                    <label for="sex-female" class="radio__label">Female</label>
                </div>
            </div>
        </div>

        <div class="create">
            <div 
            onmousedown="return false" 
            onselectstart="return false" 
            class="btn-create-robot btn btn_prod_disabled">Произвести за 10 монет</div>
            <div class="create__descr">
                Для производства биоробота не хватает 4 биомеханизма,
                4 процессора, денег и души
            </div>
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style>

</style>