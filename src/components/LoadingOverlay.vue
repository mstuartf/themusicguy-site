<template>
  
  <!-- for some reason this needs a border to work on safari! -->
  <div 
    id="loading-overlay" 
    class="fixed pin z-50 flex items-center justify-center border">

    <div 
      id='iconSpinner' 
      class="relative h-24 w-24">

      <icon-disc 
        class="absolute pin bg-brand-pink shadow-lg" 
        svg-icon="acoustic" 
        icon-height="50%" 
        icon-color="white">
      </icon-disc>

      <icon-disc 
        class="absolute pin bg-brand-green shadow-lg" 
        svg-icon="plugged-in" 
        icon-height="50%" 
        icon-color="white">
      </icon-disc>

      <icon-disc 
        class="absolute pin bg-brand-purple shadow-lg" 
        svg-icon="dj" 
        icon-height="50%" 
        icon-color="white">
      </icon-disc>

    </div>

  </div>    
        
</template>

<script>

  import iconDisc from './iconDisc.vue'

export default {

  name: 'LoadingOverlay',

  components: {iconDisc}

}

</script>

<style>

  /* Assign the rotation function / loop / timer to each div (for each browser) */
  #iconSpinner div {

    /* All elements need to start rotated 90deg */
    transform: rotateY(-90deg);
    
    /* Firefox */
    -moz-animation-name: rotateIcon;
    -moz-animation-timing-function: linear;
    -moz-animation-iteration-count: infinite;
    -moz-animation-duration: 3s;
    
    /* Safari and Chrome */
    -webkit-animation-name: rotateIcon;
    -webkit-animation-timing-function: linear;
    -webkit-animation-iteration-count: infinite;
    -webkit-animation-duration: 3s;
    
    /* Safari and Chrome */
    -o-animation-name: rotateIcon;
    -o-animation-timing-function: linear;
    -o-animation-iteration-count: infinite;
    -o-animation-duration: 3s;

    /* Opera */
    animation-name: rotateIcon;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
    animation-duration: 3s;
    
  }

  /* Delay the animation for the second child by 1 second */
  #iconSpinner div:nth-child(2) {
    animation-delay: 1s;
  }

  /* Delay the animation for the third child by 2 seconds */
  #iconSpinner div:nth-child(3) {
    animation-delay: 2s;
  }

  /* Define the rotation function for each browser */
  @-webkit-keyframes rotateIcon {
    0% {-webkit-transform: rotateY(-90deg);}
    16.66% {-webkit-transform: rotateY(0deg);}
    33.33% {-webkit-transform: rotateY(90deg);}
    100% {-webkit-transform: rotateY(90deg);}
  }
  @-moz-keyframes rotateIcon {
    0% {-moz-transform: rotateY(-90deg);}
    16.66% {-moz-transform: rotateY(0deg);}
    33.33% {-moz-transform: rotateY(90deg);}
    100% {-moz-transform: rotateY(90deg);}
  }
  @-o-keyframes rotateIcon {
    0% {-o-transform: rotateY(-90deg);}
    16.66% {-o-transform: rotateY(0deg);}
    33.33% {-o-transform: rotateY(90deg);}
    100% {-o-transform: rotateY(90deg);}
  }
  @keyframes rotateIcon {
    0% {transform: rotateY(-90deg);}
    16.66% {transform: rotateY(0deg);}
    33.33% {transform: rotateY(90deg);}
    100% {transform: rotateY(90deg);}
  }


  #loading-overlay {
    visibility: hidden;
    opacity: 0;
    transition: visibility 0.5s linear, opacity 0.5s linear;
  
  }

  #loading-overlay.show {
    visibility: visible;
    opacity: 1;
  }

  
</style>

