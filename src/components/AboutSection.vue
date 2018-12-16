<template>
    <div class="text-center md:text-left">
        <svgicon :icon="icon" :color="color" height="3rem"></svgicon>
        <h3 class="py-2">{{ title }}</h3>
        <div class="py-1 flex justify-center md:justify-start">
          <span class="about-divider" :style="{'background-color': color}"></span>
        </div>
        <p class="py-2">{{ body }}</p>
    </div>
</template>
<script>
export default {

    name: 'AboutSection',

    props: ['icon', 'color', 'title', 'body']

}
</script>
<style>
.about-divider {
    width: 30px;
    height: 5px;
    display: block;
    border-radius: 5px;
}
</style>
