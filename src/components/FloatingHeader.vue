<template>

    <div :style="{height: headerHeight}"
          class="pin-t w-full fixed bg-white smooth-header overflow-hidden z-50 shadow-md" >
  
      <slot></slot>

    </div>

</template>

<script>

export default {

  name: 'FloatingHeader',

  props: {
    breakPoint: { default: 200 }
  },

  data () {
    return {
      headerHeight: '0rem'
    }
  },

  methods: {
    updateScroll() {
      this.headerHeight = window.scrollY > this.breakPoint ? '4rem' : '0rem';
    }
  },

  mounted() {
    window.addEventListener('scroll', this.updateScroll);
  }

}

</script>

<style></style>
