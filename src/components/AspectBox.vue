<template>
    <div class="image-container">
        <img src="../assets/img/aspect.png"/>
        <div class="duration flex items-center">
            <slot></slot>
        </div>
    </div>
</template>
<script>
export default {

    name: 'AspectBox'

}
</script>
<style>

.image-container {
    position: relative;
    display: inline-block;
    /* inline-table works too if you  images in cells and row to center here*/
    vertical-align: middle;
    height: 100%;
}

.image-container img {
    display: block;
    max-width: 100%;
    max-height: 100%;
}

.duration {
    position: absolute;
    right: 0;
    bottom: 0;
    left: 0;
    top: 0;

}
</style>