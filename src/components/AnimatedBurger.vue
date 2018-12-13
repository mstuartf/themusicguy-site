<template>

<div @click="toggleOpen" 
     class="burger-menu"
     :class="{'open': open}">

  <span :style="{ 'background-color': color }"></span>
  <span :style="{ 'background-color': color }"></span>
  <span :style="{ 'background-color': color }"></span>

</div>
        
</template>

<script>

export default {

  name: 'AnimatedBurger',

  props: {
    open: {},
    color: { default: 'red' }
  },

  methods: {
    toggleOpen () {
      this.$emit('burger-toggle', !this.open);
    }
  }

}

</script>

<style>

  .burger-menu {
    width: 40px;
    height: 30px;
    -webkit-transform: rotate(0deg);
    -moz-transform: rotate(0deg);
    -o-transform: rotate(0deg);
    transform: rotate(0deg);
    -webkit-transition: .5s ease-in-out;
    -moz-transition: .5s ease-in-out;
    -o-transition: .5s ease-in-out;
    transition: .5s ease-in-out;
    cursor: pointer;
  }

  .burger-menu span {
    display: block;
    position: absolute;
    height: 6px;
    width: 100%;
    opacity: 1;
    left: 0;
    -webkit-transform: rotate(0deg);
    -moz-transform: rotate(0deg);
    -o-transform: rotate(0deg);
    transform: rotate(0deg);
    -webkit-transition: .25s ease-in-out;
    -moz-transition: .25s ease-in-out;
    -o-transition: .25s ease-in-out;
    transition: .25s ease-in-out;
  }

  .burger-menu span:nth-child(1) {
    top: 0px;
  }

  .burger-menu span:nth-child(2) {
    top: 12px;
  }

  .burger-menu span:nth-child(3) {
    top: 24px;
  }

  .burger-menu.open span:nth-child(1) {
    top: 12px;
    -webkit-transform: rotate(135deg);
    -moz-transform: rotate(135deg);
    -o-transform: rotate(135deg);
    transform: rotate(135deg);
  }

  .burger-menu.open span:nth-child(2) {
    opacity: 0;
    left: -60px;
  }

  .burger-menu.open span:nth-child(3) {
    top: 12px;
    -webkit-transform: rotate(-135deg);
    -moz-transform: rotate(-135deg);
    -o-transform: rotate(-135deg);
    transform: rotate(-135deg);
  }


</style>

