<template>

  <div 
    class="rounded-circle flex-none flex items-center justify-center">
    
    <svgicon 
      :icon="svgIcon" 
      :height="iconHeight" 
      :color="iconColor">
    </svgicon>
  
  </div>

</template>

<script>

export default {

  name: 'IconDisc',

  props: ['svgIcon', 'discHeight', 'iconHeight', 'iconColor']

}

</script>

<style></style>
