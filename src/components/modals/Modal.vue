<template>
  <transition name="modal">
    <!-- close on clicks outside the modal -->
    <div class="modal-mask" @click="close" v-show="value">
      <!-- don't bubble inside clicks to the mask -->
      <div class="modal-container"
        @click.stop
        @close="close"
      >
        <button class="closer" @click.stop="close">
          <svg viewBox="0 0 18 18">
            <line x2="19.799" transform="translate(2 2) rotate(45)"/>
            <line y2="19.799" transform="translate(16 2) rotate(45)"/>
          </svg>
        </button>
        <slot>
        </slot>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  props:[
    'value'
  ],
  methods: {
    close(){
      this.$emit('input', false)
    }
  },
  watch:{
    value(val){
      if(val)
        document.body.classList.add('modal-open')
      else
        document.body.classList.remove('modal-open')

    }
  }

}
</script>

<style lang="scss">
body.modal-open{
  overflow: hidden;
}
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .5);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: opacity .3s ease;
}

.modal-container {
  flex-grow: 1;
  background-color: #fff;
  height: 100%;
  position: relative;

  @media (min-width: 680px) {
    max-width: 900px;
    max-height: 90vh;
    margin: 0px 20px;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
    transition: all .3s ease;
  }
}
button.closer {
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
  background: white;
  border-radius: 50%;
  border: none;
  float: right;
  padding: 0.75rem;

  line-height: 0;
  color:var(--bg-dark);

  @media (min-width: 680px) {
    top: 0.5rem;
    right: 0.5rem;
    &:hover, &:active{
      box-shadow: var(--hard-shadow);
    }
  }

  &:hover{
    color: var(--accent);
  }
  &:active{
    color:var(--theme);
  }
  svg{
    width: 16px;
    height: 16px;
    fill: none;
    stroke: currentColor;
    stroke-linecap: round;
    stroke-width: 3px;
  }
}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(0.9);
  transform: scale(0.9);
}

</style>
