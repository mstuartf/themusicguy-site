<template>

    <div id="popup-background"
         class="fixed pin z-50 bg-smoke-lighter">

      <div class="pin absolute h-full w-full z-100 flex items-center justify-center px-8">

        <div class="bg-white h-full w-full max-w-24 max-h-24 rounded shadow-lg px-8">
          
          <div class="h-1/4 w-full border-b flex items-center justify-center">

            <slot name="header"></slot>

          </div>

          <div class="h-1/2 w-full py-16 flex flex-col items-center text-xl text-grey-darker">

            <slot name="body"></slot>

          </div>

          <div class="h-1/4 w-full flex items-start justify-center">

            <slot name="footer"></slot>

          </div>
          
        </div>  

      </div>

    </div>
        
</template>

<script>

export default {
  name: 'SimplePopup',
}

</script>

<style>

  #popup-background {
    visibility: hidden;
    opacity:0;
    transition: visibility 0.5s linear, opacity 0.5s linear;
  
  }

  #popup-background.show {
    visibility: visible;
    opacity: 1;
  }

</style>

