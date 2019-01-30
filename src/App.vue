<template>
    <div id="app" class="w-full h-full">
        <!-- OVERLAY ON FIRST PAGE LOAD WHILE HERO IMAGE LOADS -->
        <LoadingOverlay class="bg-white" :class="{'show': underMinLoadingTime}"></LoadingOverlay>
        <FloatingHeader :break-point="200">
            <!-- DESKTOP FLOATING HEADER-->
            <div class="w-full h-full px-8 hidden md:flex justify-between items-center">
                <img src="./assets/img/icon_1.png" class="h-8"/>
                <ul class="list-reset flex">
                    <li class="mr-6">
                        <HeaderButton element-id="section-1" class="h-text">
                            {{ jsonCopy.HEADER.SECTION_1_BUTTON }}
                        </HeaderButton>
                    </li>
                    <li class="mr-6">
                        <HeaderButton element-id="section-2" class="h-text" :offset-px="-64">
                            {{ jsonCopy.HEADER.SECTION_2_BUTTON }}
                        </HeaderButton>
                    </li>
                    <li>
                        <HeaderButton element-id="section-4" class="h-text">
                            {{ jsonCopy.HEADER.SECTION_3_BUTTON }}
                        </HeaderButton>
                    </li>
                </ul>
            </div>
            <!-- MOBILE FLOATING HEADER -->
            <div class="w-full h-full px-4 flex md:hidden justify-between items-center">
                <img src="./assets/img/icon_1.png" class="h-8"/>
                <AnimatedBurger :open="showModalMenu" class="" :color="colors.darkGrey" @burger-toggle="toggled($event)">
                </AnimatedBurger>
            </div>
        </FloatingHeader>
        <!-- MOBILE MENU MODAL -->
        <div class="w-full bg-white fixed smooth-header overflow-hidden z-50" :style="{'height': dropDownHeight}">
            <!-- another burger menu overlay -->
            <div class="w-full px-4 flex justify-between items-center h-16">
                <img src="./assets/img/icon_1.png" class="h-8"/>
                <AnimatedBurger :open="showModalMenu" :color="colors.darkGrey" @burger-toggle="toggled($event)">
                </AnimatedBurger>
            </div>
            <!-- div taking up remaining screen with negative margin so we can v-center ignoring burger-->
            <div class="h-full -mt-16 flex align-center justify-center">
                <ul class="list-reset m-auto">
                    <li class="p-4 text-center">
                        <HeaderButton element-id="section-1" class="h-text" @HeaderButtonClicked="toggled(false)">
                            {{ jsonCopy.HEADER.SECTION_1_BUTTON }}
                        </HeaderButton>
                    </li>
                    <li class="p-4 text-center">
                        <HeaderButton element-id="section-2" class="h-text" :offset-px="-64" @HeaderButtonClicked="toggled(false)">
                            {{ jsonCopy.HEADER.SECTION_2_BUTTON }}
                        </HeaderButton>
                    </li>
                    <li class="p-4 text-center">
                        <HeaderButton element-id="section-4" class="h-text" :offset-px="-64" @HeaderButtonClicked="toggled(false)">
                            {{ jsonCopy.HEADER.SECTION_3_BUTTON }}
                        </HeaderButton>
                    </li>
                </ul>
            </div>
        </div>
        <!-- SECTION 1 -->
        <div id="section-1" class="w-full h-full flex flex-col">
            <!-- DESKTOP SECTION 1 HEADER -->
            <div class="h-16 px-8 hidden md:flex items-center justify-between bg-white">
                <img src="./assets/img/icon_1.png" class="h-8"/>
                <ul class="list-reset flex">
                    <li class="mr-6">
                        <HeaderButton element-id="section-1" class="h-text">
                            {{ jsonCopy.HEADER.SECTION_1_BUTTON }}
                        </HeaderButton>
                    </li>
                    <li class="mr-6">
                        <HeaderButton element-id="section-2" :offset-px="-64" class="h-text">
                            {{ jsonCopy.HEADER.SECTION_2_BUTTON }}
                        </HeaderButton>
                    </li>
                    <li>
                        <HeaderButton element-id="section-4" class="h-text">
                            {{ jsonCopy.HEADER.SECTION_3_BUTTON }}
                        </HeaderButton>
                    </li>
                </ul>
            </div>
            <!-- MOBILE SECTION 1 HEADER -->
            <div class="h-16 px-4 flex items-center justify-between md:hidden bg-white">
                <img src="./assets/img/icon_1.png" class="h-8"/>
                <AnimatedBurger :open="showModalMenu" :color="colors.darkGrey" @burger-toggle="toggled($event)">
                </AnimatedBurger>
            </div>
            <!-- SECTION 1 CONTENT -->
            <div class="flex-auto relative">
                <div class="w-full h-full absolute">
                    <div class="w-full h-full flex items-center justify-center bg-brand-black">
                        <iframe id="tmg-video" src="https://player.vimeo.com/video/293414793" width="100%" height="100%" allow="autoplay" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen>
                        </iframe>
                    </div>
                </div>
            </div>
            <div class="h-24 flex items-center justify-center p-4 pt-2">
                <div class="w-full h-full flex items-center justify-center text-center">
                    <h2>{{ jsonCopy.SECTION_1.TAGLINE }}</h2>
                </div>
            </div>
        </div>

        <!-- stretch box height to fill screen underneath header -->
        <div id="section-2" class="md:w-full md:h-full-header md:flex">
            <div class="md:flex-auto md:relative">
                <div class="md:w-full md:h-full md:absolute md:flex md:flex-col">
                    <div class="md:flex md:w-full md:h-1/2">        
                        <div class="md:h-full md:w-1/2 p-8 md:pr-4 md:flex items-center justify-end">
                            <img class="max-w-full max-h-full" src="./assets/img/about_1.png"/>
                        </div>
                        <div class="md:h-full md:w-1/2 p-8 md:pl-4 md:text-left">
                            <AspectBox>
                                <AboutSection icon="acoustic" :color="colors.green" :title="jsonCopy.SECTION_2.TITLE_1" :body="jsonCopy.SECTION_2.BLURB_1">
                                </AboutSection>
                            </AspectBox>
                        </div>
                   </div>
                    <div class="md:flex md:w-full md:h-1/2 md:flex-row-reverse">
                        <div class="md:h-full md:w-1/2 p-8 md:pl-4 md:flex items-center justify-start">
                            <img class="max-w-full max-h-full" src="./assets/img/about_2.png"/>
                        </div>
                        <div class="md:h-full md:w-1/2 p-8 md:pr-4 text-right">
                            <AspectBox>
                                <AboutSection icon="plugged-in" :color="colors.pink" :title="jsonCopy.SECTION_2.TITLE_2" :body="jsonCopy.SECTION_2.BLURB_2">
                                </AboutSection>
                            </AspectBox>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- stretch box height to fill screen underneath header -->
        <div class="md:w-full md:h-full-header md:flex">
            <div class="md:flex-auto md:relative">
                <div class="md:w-full md:h-full md:absolute md:flex md:flex-col">
                    <div class="md:flex md:w-full md:h-1/2">        
                        <div class="md:h-full md:w-1/2 p-8 md:pr-4 md:flex items-center justify-end">
                            <img class="max-w-full max-h-full" src="./assets/img/about_3.png"/>
                        </div>
                        <div class="md:h-full md:w-1/2 p-8 md:pl-4 md:text-left">
                            <AspectBox>
                                <AboutSection icon="dj" :color="colors.purple" :title="jsonCopy.SECTION_2.TITLE_3" :body="jsonCopy.SECTION_2.BLURB_3">
                                </AboutSection>
                            </AspectBox>
                        </div>
                   </div>
                    <div class="md:flex md:w-full md:h-1/2 md:flex-row-reverse">
                        <div class="md:h-full md:w-1/2 p-8 md:pl-4 md:flex items-center justify-start">
                            <img class="max-w-full max-h-full" src="./assets/img/about_4.png"/>
                        </div>
                        <div class="md:h-full md:w-1/2 p-8 md:pr-4 text-right">
                            <AspectBox>
                                <AboutSection icon="logo" :color="colors.blue" :title="jsonCopy.SECTION_2.TITLE_4" :body="jsonCopy.SECTION_2.BLURB_4">
                                </AboutSection>
                            </AspectBox>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- SECTION 4 -->
        <div id="section-4" class="w-full md:h-full-header flex flex-col">
            <div class="flex-auto relative flex flex-col">
                <table class="w-full">
                    <tr>
                        <td class="p-8 md:px-12 block w-full md:table-cell md:w-1/2 h-full align-top">
                            <div class="w-full flex justify-center md:justify-end">
                                <div class="w-full max-w-24 flex flex-col items-start">
                                    <div class="text-center md:text-left w-full">
                                        <h3 class="py-2">
                                            {{ jsonCopy.SECTION_4.TITLE }}
                                        </h3>
                                        <div class="pt-1 pb-4 flex justify-center md:justify-start">
                                            <span class="about-divider green-line"></span>
                                        </div>
                                    </div>
                                    <div class="max-w-24 pt-2 pb-4 text-center md:text-left">
                                        <p>{{ jsonCopy.SECTION_4.INFO_TEXT }}</p>
                                    </div>
                                    <div class="flex justify-center md:flex-col w-full">
                                        <!-- <div class="px-4 md:px-0 md:w-full flex items-center py-4">
                                            <a :href="'tel:' + jsonCopy.SECTION_4.INFO_NUMBER" target="_blank" class="h-8">
                                            <img src="./assets/img/icon_2.png" class="h-full" />
                                        </a>
                                            <div class="hidden md:block px-4 font-bold">
                                                <p>{{ jsonCopy.SECTION_4.INFO_NUMBER }}</p>
                                            </div>
                                        </div> -->
                                        <div class="px-4 md:px-0 md:w-full flex items-center py-4">
                                            <a :href="'mailto:' + jsonCopy.SECTION_4.INFO_EMAIL" class="h-8">
                                            <img src="./assets/img/icon_3.png" class="h-full" />
                                        </a>
                                            <div class="hidden md:block px-4 font-bold">
                                                <p>{{ jsonCopy.SECTION_4.INFO_EMAIL }}</p>
                                            </div>
                                        </div>
                                        <div class="px-4 md:px-0 md:w-full flex items-center py-4">
                                            <a :href="'https://www.instagram.com/' + jsonCopy.SECTION_4.INFO_INSTAGRAM" target="_blank" class="h-8">
                                            <img src="./assets/img/icon_5.png" class="h-full" />
                                        </a>
                                            <div class="hidden md:block px-4 font-bold">
                                                <p>{{ jsonCopy.SECTION_4.INFO_INSTAGRAM }}</p>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </td>
                        <td class="p-8 md:px-12 block w-full md:table-cell md:w-1/2 h-full align-top">
                            <MessageForm></MessageForm>
                        </td>
                    </tr>
                </table>
                <div class="h-48 md:flex-auto relative">
                    <div class="absolute h-48 md:h-32 w-full pin-t pin-l text-center pt-4 pb-24 md:pb-12">
                        <svgicon icon="logo" height="100%" :color="colors.darkGrey"></svgicon>
                    </div>
                </div>
            </div>
        </div>
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
import './assets/svg/compiled/plugged-in'
import './assets/svg/compiled/acoustic'
import './assets/svg/compiled/logo'
import './assets/css/tailwind.css'
import './assets/svg/compiled/dj'

import FloatingHeader from './components/FloatingHeader.vue'
import AnimatedBurger from './components/AnimatedBurger.vue'
import LoadingOverlay from './components/LoadingOverlay.vue'
import HeaderButton from './components/HeaderButton.vue'
import SplitSection from './components/SplitSection.vue'
import AboutSection from './components/AboutSection.vue'
import MessageForm from './components/MessageForm.vue'
import AspectBox from './components/AspectBox.vue'


export default {

    name: 'app',

    components: {
        FloatingHeader,
        HeaderButton,
        AnimatedBurger,
        SplitSection,
        AboutSection,
        MessageForm,
        LoadingOverlay,
        AspectBox
    },

    data() {
        return {
            jsonCopy: copy,
            showModalMenu: false,
            dropDownHeight: '0rem',
            underMinLoadingTime: true,
            colors: {
                pink: '#e79e99',
                green: '#569089',
                purple: '#9493b1',
                blue: '#547692',
                black: '#090D14',
                grey: '#505050',
                darkGrey: '#3A3A39',
            }
        }
    },

    methods: {

        toggled(event) {
            this.showModalMenu = event;
            this.dropDownHeight = this.showModalMenu ? '100%' : '0rem';
        },

        minLoadingTime() {
            setTimeout(() => {
                this.underMinLoadingTime = false;
            }, 3000)
        },

    },

    mounted() {
        this.minLoadingTime();
    }

}
</script>
<style>
body {
    background-image: url('./assets/img/texture.png');
}

h1,
h2,
h3,
.h-text {
    font-family: 'Josefin Sans', sans-serif;
    color: #3A3A39;
}

p,
.p-text {
    font-family: 'Open Sans', sans-serif;
    color: #505050;
    line-height: 1.7;
}

.bg-brand-black {
    background-color: #090D14;
}

.smooth-header {
    transition: height 0.4s;
}

.pink-line {
    background-color: #e79e99;
}

.green-line {
    background-color: #569089;
}
</style>