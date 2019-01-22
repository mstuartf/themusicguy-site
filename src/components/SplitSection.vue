<template>
    <div class="w-full h-2/1-header md:h-full-header flex flex-col">
        <div class="flex-auto relative">
            <div class="w-full h-full absolute">
                <div id="123" class="w-full h-full flex flex-col" :class="{'md:flex-row': !flatten}">
                    <div id="456" class="flex flex-col w-full h-1/2" :class="{'md:w-1/2 md:h-full': !flatten}">
                        <div class="flex-auto relative">
                            <div class="w-full h-full absolute">
                                <slot name="part-1"></slot>
                            </div>
                        </div>
                    </div>
                    <div id="456" class="flex flex-col w-full h-1/2" :class="{'md:w-1/2 md:h-full': !flatten}">
                        <div class="flex-auto relative">
                            <div class="w-full h-full absolute">
                                <slot name="part-2"></slot>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {

    name: 'SplitSection',

    props: ['flatten']

}
</script>
<style>

</style>