<template>
  <div class="modal modal_overcoin" @click="closeModalOvercoin">
        <div class="modal__wrapper">
            <div class="modal_overcoin__coin"></div>
            <div class="modal__title modal_overcoin__title">Количество монет ограничено</div>
            <div class="modal__descr modal_overcoin__descr">Вы не можете нацыганить более 100 монет biorobo</div>
            <div class="modal__close modal__close_overcoin"></div>
        </div>
    </div>

    <div class="modal modal_create" @click="closeModalCreate">
        <div class="modal__wrapper">
            <div class="modal__title modal_create__title">Биоробот произведён</div>
            <div class="modal__descr modal_create__descr">Поздравляем! <br> Вы произвели биоробота</div>
            <div class="modal__close modal__close_create"></div>
        </div>
    </div>
</template>

<script>
export default {
    methods: {
        closeModalOvercoin(e) {
            const modalOvercoin = document.querySelector('.modal_overcoin');
            if (e.target.classList.contains('modal') || e.target.classList.contains('modal__close')) {
                modalOvercoin.style.display = 'none'
            }
        },
        closeModalCreate(e) {
            const modalCreate = document.querySelector('.modal_create');
            if (e.target.classList.contains('modal') || e.target.classList.contains('modal__close')) {
                modalCreate.style.display = 'none'
            }
        }
    }
}
</script>

<style>

</style>