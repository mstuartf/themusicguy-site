<template>
    <div class="cursor-pointer" @mouseenter="mouseEnter" @mouseleave="mouseLeave">
        <a class="text-xl no-underline color-inherit"
           @click="$emit('HeaderButtonClicked')"
           :href="'#' + elementId" v-smooth-scroll="{ duration: 1000, offset: offsetPx || 0 }">

            <slot></slot>

            <span class="block h-1 line-under color-inherit" 
                  :style="underlineStyle">
            </span>

         </a>
    </div>
</template>
<script>
export default {

    name: 'HeaderButton',

    data() {
        return {
            isUnderlined: false
        }
    },

    computed: {

        underlineStyle() {
            return {
                'background-color': this.isUnderlined ? 'currentColor' : 'unset'
            }
        }

    },

    methods: {

        mouseEnter() {
            this.isUnderlined = true;
        },

        mouseLeave() {
            this.isUnderlined = false;
        }

    },

    props: {
        'elementId': String,
        'offsetPx': Number
    }

}
</script>
<style>
.line-under {
    transition: all 0.4s;
}

.color-inherit {
    color: inherit;
}
</style>