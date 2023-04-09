<template>
  <div>
    <button @click="toggle">Open Modal</button>
    <teleport to="#app">
      <transition name="fade">
        <div v-if="show" class="modal">
          <div class="modal-box">
            <h1>Este es el contenido del modal</h1>
            <p>
              Este es el texto del modal Lorem ipsum dolor sit amet consectetur
              adipisicing elit. Fuga neque similique sequi doloribus officiis
              odio accusamus. Quod vel, necessitatibus, molestias vitae tempore
              assumenda odit nihil repudiandae, officia eos vero aspernatur.
            </p>
            <button @click="toggle" class="modal-button__close">
              Cerrar modal
            </button>
          </div>
        </div>
      </transition>
    </teleport>
  </div>
</template>

<script>
export default {
  name: "Modal",
  data() {
    return {
      show: false,
    };
  },
  methods: {
    toggle() {
      this.show = !this.show;
    },
  },
};
</script>

<style>
button {
  background-color: #42b983;
  color: white;
  border: none;
  height: 50px;
  width: 150px;
  border-radius: 50px;
  cursor: pointer;
  margin: 50px;
}

.modal {
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.336);
}

.modal-box {
  display: flex;
  flex-direction: column;
  align-items: center;

  padding: 20px;
  background-color: #fff;
  box-shadow: 10px 10px 33px 0px rgba(207, 207, 207, 1);
  width: 500px;
  border-radius: 20px;
}

.modal-button__close {
  background-color: #c45858;
  margin: 10px;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-leave-active,
.fade-enter-active {
  transition: opacity 0.5s ease;
}
</style>
