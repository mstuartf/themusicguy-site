<template>
    <div id="app" class="w-full h-full">
        <FloatingHeader :break-point="200">
            <!-- DESKTOP FLOATING HEADER-->
            <div class="w-full h-full px-8 hidden md:flex justify-between items-center">
                <svgicon icon="logo" height="3rem" color="#b8c2cc"></svgicon>
                <ul class="list-reset flex">
                    <li class="mr-6">
                        <HeaderButton element-id="section-1" class="text-grey-dark">
                            {{ jsonCopy.HEADER.SECTION_1_BUTTON }}
                        </HeaderButton>
                    </li>
                    <li class="mr-6">
                        <HeaderButton element-id="section-2" class="text-grey-dark">
                            {{ jsonCopy.HEADER.SECTION_2_BUTTON }}
                        </HeaderButton>
                    </li>
                    <li>
                        <HeaderButton element-id="section-3" class="text-grey-dark">
                            {{ jsonCopy.HEADER.SECTION_3_BUTTON }}
                        </HeaderButton>
                    </li>
                </ul>
            </div>
            <!-- MOBILE FLOATING HEADER -->
            <div class="w-full h-full px-4 flex md:hidden justify-between items-center">
                <svgicon icon="logo" height="3rem" color="#b8c2cc"></svgicon>
                <AnimatedBurger :open="showModalMenu" class="" color="#b8c2cc" @burger-toggle="toggled($event)">
                </AnimatedBurger>
            </div>
        </FloatingHeader>
        <!-- MOBILE MENU MODAL -->
        <div class="w-full bg-white fixed smooth-header overflow-hidden z-50" :style="{'height': dropDownHeight}">
            <!-- another burger menu overlay -->
            <div class="w-full px-4 flex justify-between items-center h-16">
                <svgicon icon="logo" height="3rem" color="#b8c2cc"></svgicon>
                <AnimatedBurger :open="showModalMenu" color="#b8c2cc" @burger-toggle="toggled($event)">
                </AnimatedBurger>
            </div>
            <!-- div taking up remaining screen with negative margin so we can v-center ignoring burger-->
            <div class="h-full -mt-16 flex align-center justify-center">
                <ul class="list-reset m-auto">
                    <li class="p-4 text-center">
                        <HeaderButton element-id="section-1" class="text-grey-dark" @HeaderButtonClicked="toggled(false)">
                            {{ jsonCopy.HEADER.SECTION_1_BUTTON }}
                        </HeaderButton>
                    </li>
                    <li class="p-4 text-center">
                        <HeaderButton element-id="section-2" class="text-grey-dark" @HeaderButtonClicked="toggled(false)">
                            {{ jsonCopy.HEADER.SECTION_2_BUTTON }}
                        </HeaderButton>
                    </li>
                    <li class="p-4 text-center">
                        <HeaderButton element-id="section-3" class="text-grey-dark" @HeaderButtonClicked="toggled(false)">
                            {{ jsonCopy.HEADER.SECTION_3_BUTTON }}
                        </HeaderButton>
                    </li>
                </ul>
            </div>
        </div>
        <!-- SECTION 1 -->
        <div id="section-1" class="w-full h-full flex flex-col">
            <!-- DESKTOP SECTION 1 HEADER -->
            <div class="h-16 px-8 hidden md:flex items-center justify-between">
                <svgicon icon="logo" height="3rem" color="#b8c2cc"></svgicon>
                <ul class="list-reset flex">
                    <li class="mr-6">
                        <HeaderButton element-id="section-1" class="text-grey-dark">
                            {{ jsonCopy.HEADER.SECTION_1_BUTTON }}
                        </HeaderButton>
                    </li>
                    <li class="mr-6">
                        <HeaderButton element-id="section-2" class="text-grey-dark">
                            {{ jsonCopy.HEADER.SECTION_2_BUTTON }}
                        </HeaderButton>
                    </li>
                    <li>
                        <HeaderButton element-id="section-3" class="text-grey-dark">
                            {{ jsonCopy.HEADER.SECTION_3_BUTTON }}
                        </HeaderButton>
                    </li>
                </ul>
            </div>
            <!-- MOBILE SECTION 1 HEADER -->
            <div class="h-16 px-4 flex items-center justify-between md:hidden">
                <svgicon icon="logo" height="3rem" color="#b8c2cc"></svgicon>
                <AnimatedBurger :open="showModalMenu" color="#b8c2cc" @burger-toggle="toggled($event)">
                </AnimatedBurger>
            </div>
            <!-- SECTION 1 CONTENT -->
            <div class="flex-auto relative">
                <div class="w-full h-full absolute px-4 py-2">
                    <div class="w-full h-full flex items-center justify-center border-4 border-orange bg-orange-lighter">
                    </div>
                </div>
            </div>
            <div class="h-24 flex items-center justify-center p-4 pt-2">
                <div class="w-full h-full flex items-center justify-center border-4 border-pink bg-pink-lighter">
                </div>
            </div>
        </div>
        <!-- SECTION 2 -->
        <SplitSection id="section-2" :flatten="true">
            <div slot="part-1" class="w-full h-full">
                <div class="h-full w-full md:flex">
                    <div class="h-1/2 w-full md:h-full md:w-1/2 p-8 pb-4 md:pr-4">
                        <div class="w-full h-full flex items-center justify-center md:justify-end">
                            <img class="max-w-full max-h-full" src="./assets/img/The Music Guy - Website R3 AW-01.png"/>
                        </div>
                        </div>
                        <div class="h-1/2 w-full md:h-full md:w-1/2 p-8 pt-4 md:pt-8 md:pb-4 md:pl-4">
                            <div class="w-full h-full text-center md:text-left">
                                <AspectBox>
                                    <AboutSection icon="acoustic" :color="brandGreen" :title="jsonCopy.SECTION_2.TITLE_1" :body="jsonCopy.SECTION_2.BLURB_1">
                                    </AboutSection>
                                </AspectBox>
                            </div>
                        </div>
                    </div>
                </div>
                <div slot="part-2" class="w-full h-full">
                    <div class="h-full w-full md:flex md:flex-row-reverse">
                        <div class="h-1/2 w-full md:h-full md:w-1/2 p-8 pb-4 md:pb-8 md:pt-4 md:pl-4">
                            <div class="w-full h-full flex items-center justify-center md:justify-start">
                                <img class="max-w-full max-h-full" src="./assets/img/The Music Guy - Website R3 AW-02.png"/>
                        </div>
                            </div>
                            <div class="h-1/2 w-full md:h-full md:w-1/2 p-8 pt-4 md:pr-4">
                                <div class="w-full h-full text-center md:text-right">
                                    <AspectBox>
                                        <AboutSection icon="plugged-in" :color="brandPink" :title="jsonCopy.SECTION_2.TITLE_2" :body="jsonCopy.SECTION_2.BLURB_2">
                                        </AboutSection>
                                    </AspectBox>
                                </div>
                            </div>
                        </div>
                    </div>
        </SplitSection>
        <!-- SECTION 3 -->
        <SplitSection id="section-3" :flatten="true">
            <div slot="part-1" class="w-full h-full">
                <div class="h-full w-full md:flex">
                    <div class="h-1/2 w-full md:h-full md:w-1/2 p-8 pb-4 md:pr-4">
                        <div class="w-full h-full flex items-center justify-center md:justify-end">
                            <img class="max-w-full max-h-full" src="./assets/img/The Music Guy - Website R3 AW-03.png"/>
                        </div>
                        </div>
                        <div class="h-1/2 w-full md:h-full md:w-1/2 p-8 pt-4 md:pt-8 md:pb-4 md:pl-4">
                            <div class="w-full h-full text-center md:text-left">
                                <AspectBox>
                                    <AboutSection icon="dj" :color="brandPurple" :title="jsonCopy.SECTION_2.TITLE_3" :body="jsonCopy.SECTION_2.BLURB_3">
                                    </AboutSection>
                                </AspectBox>
                            </div>
                        </div>
                    </div>
                </div>
                <div slot="part-2" class="w-full h-full">
                    <div class="h-full w-full md:flex md:flex-row-reverse">
                        <div class="h-1/2 w-full md:h-full md:w-1/2 p-8 pb-4 md:pb-8 md:pt-4 md:pl-4">
                            <div class="w-full h-full flex items-center justify-center md:justify-start">
                                <img class="max-w-full max-h-full" src="./assets/img/The Music Guy - Website R3 AW-04.png"/>
                        </div>
                            </div>
                            <div class="h-1/2 w-full md:h-full md:w-1/2 p-8 pt-4 md:pr-4">
                                <div class="w-full h-full text-center md:text-right">
                                    <AspectBox>
                                        <AboutSection icon="logo" :color="brandBlue" :title="jsonCopy.SECTION_2.TITLE_4" :body="jsonCopy.SECTION_2.BLURB_4">
                                        </AboutSection>
                                    </AspectBox>
                                </div>
                            </div>
                        </div>
                    </div>
        </SplitSection>
    </div>
</template>
<script>
import Vue from 'vue'

import vueSmoothScroll from 'vue2-smooth-scroll'
Vue.use(vueSmoothScroll)

import Vue2TouchEvents from 'vue2-touch-events'
Vue.use(Vue2TouchEvents)

import VueSVGIcon from 'vue-svgicon'
Vue.use(VueSVGIcon)

import VueResource from 'vue-resource'
Vue.use(VueResource)

import copy from './assets/i8n/copy.json'
import './assets/svg/compiled/dj'
import './assets/svg/compiled/logo'
import './assets/svg/compiled/acoustic'
import './assets/svg/compiled/plugged-in'
import './assets/css/tailwind.css'

import FloatingHeader from './components/FloatingHeader.vue'
import HeaderButton from './components/HeaderButton.vue'
import AnimatedBurger from './components/AnimatedBurger.vue'
import SplitSection from './components/SplitSection.vue'
import AboutSection from './components/AboutSection.vue'
import AspectBox from './components/AspectBox.vue'


export default {

    name: 'app',

    components: {
        FloatingHeader,
        HeaderButton,
        AnimatedBurger,
        SplitSection,
        AboutSection,
        AspectBox
    },

    data() {
        return {
            jsonCopy: copy,
            showModalMenu: false,
            dropDownHeight: '0rem',
            brandPink: '#e79e99',
            brandGreen: '#569089',
            brandPurple: '#9493b1',
            brandBlue: '#547692'
        }
    },

    methods: {

        toggled(event) {
            this.showModalMenu = event;
            this.dropDownHeight = this.showModalMenu ? '100%' : '0rem';
        }

    }

}
</script>
<style>
body {
    font-family: "Century Gothic", CenturyGothic, AppleGothic, sans-serif;
}

.smooth-header {
    transition: height 0.4s;
}
</style>