<template>
    <div>
        <div class="w-full h-full flex flex-col justify-between">
            <!-- HEADER -->
            <div class="text-center md:text-left">
                <h3 class="py-2">{{ jsonCopy.CONTACT_FORM.TITLE }}</h3>
                <div class="pt-1 pb-4 flex justify-center md:justify-start">
                    <span class="about-divider pink-line"></span>
                </div>
            </div>
            <!-- BODY -->
            <div class="w-full flex justify-center md:justify-start">
                <div class="w-full max-w-24 flex flex-col items-center">
                    <input id="name-input" type="text" v-model="inputName" :placeholder="jsonCopy.CONTACT_FORM.NAME_LABEL" class="mb-3 text-base lg:text-lg appearance-none input-border w-full py-2 px-3 focus:outline-none p-text">
                    <input id="email-input" type="text" v-model="inputEmail" :placeholder="jsonCopy.CONTACT_FORM.EMAIL_LABEL" class="mb-3 text-base lg:text-lg appearance-none input-border w-full py-2 px-3 focus:outline-none p-text">
                    <textarea id="message-input" :placeholder="jsonCopy.CONTACT_FORM.MESSAGE_LABEL" rows="7" v-model="inputMessage" class="mb-3 text-base lg:text-lg appearance-none input-border w-full py-2 px-3 focus:outline-none p-text noresize"></textarea>
                </div>
            </div>
            <!-- FOOTER -->
            <div class="w-full flex justify-center md:justify-start">
                <button class="px-3 py-2 bg-white input-border p-text" @click="sendMessage">
                    {{ jsonCopy.CONTACT_FORM.SEND_BUTTON }}
                </button>
            </div>
        </div>
        <!-- LOADING SPINNER -->
        <LoadingOverlay class="bg-smoke-lighter" :class="{'show': sendingMessage}"></LoadingOverlay>
        <!-- SUCCESS POPUP -->
        <simple-popup :class="{'show': showPopup}">
            <h1 slot="header">
          {{ popupTitle }}
      </h1>
            <div slot="body" class="h-full w-full flex flex-col">
                <div class="flex-auto text-center">
                    <p>
                        {{ popupMessage }}
                    </p>
                </div>
            </div>
            <button slot="footer" class="popup-button px-3 py-2 bg-white input-border p-text" @click="togglePopup">
                {{ popupButton }}
            </button>
        </simple-popup>
    </div>
</template>
<script>
import copy from '../assets/i8n/copy.json'

import SimplePopup from './SimplePopup.vue'
import LoadingOverlay from './LoadingOverlay.vue'

export default {

    name: 'MessageForm',

    components: { SimplePopup, LoadingOverlay },

    data() {
        return {
            sendingMessage: false,
            showPopup: false,
            inputName: '',
            inputEmail: '',
            inputMessage: '',
            jsonCopy: copy,
            popupTitle: null,
            popupMessage: null,
            popupButton: null
        }
    },

    methods: {

        sendMessage() {

            if (!this.inputName || !this.inputEmail || !this.inputMessage) return;

            if (!this.validateEmailAddress(this.inputEmail))
                return this.emailInvalidPopup();

            this.sendingMessage = true;

            var payload = {
                name: this.inputName,
                message: this.inputMessage,
                email_address: this.inputEmail
            }

            this.postMessage(payload).then(

                response => {
                    console.log(response);
                    this.sendingMessage = false;
                    this.inputName = '';
                    this.inputEmail = '';
                    this.inputMessage = '';
                    this.messageSentPopup();
                },

                response => {
                    console.log(response);
                    this.sendingMessage = false;
                    this.messageFailedPopup();
                });

        },

        togglePopup() {
            this.showPopup = !this.showPopup;
        },

        postMessage(payload) {
            return this.$http.post('https://a4caqrhhjb.execute-api.eu-west-2.amazonaws.com/prod/send_message', payload)
        },

        messageSentPopup() {
            this.popupTitle = this.jsonCopy.CONTACT_FORM.POPUP_HEADER;
            this.popupMessage = this.jsonCopy.CONTACT_FORM.POPUP_MESSAGE;
            this.popupButton = this.jsonCopy.CONTACT_FORM.POPUP_BUTTON;
            this.togglePopup();
        },

        messageFailedPopup() {
            this.popupTitle = this.jsonCopy.CONTACT_FORM.POPUP_ERROR_HEADER;
            this.popupMessage = this.jsonCopy.CONTACT_FORM.POPUP_ERROR_MESSAGE;
            this.popupButton = this.jsonCopy.CONTACT_FORM.POPUP_ERROR_BUTTON;
            this.togglePopup();
        },

        emailInvalidPopup() {
            this.popupTitle = this.jsonCopy.CONTACT_FORM.POPUP_INVALID_HEADER;
            this.popupMessage = this.jsonCopy.CONTACT_FORM.POPUP_INVALID_MESSAGE;
            this.popupButton = this.jsonCopy.CONTACT_FORM.POPUP_INVALID_BUTTON;
            this.togglePopup();
        },

        validateEmailAddress(email) {
            var re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
            return re.test(String(email).toLowerCase());
        }

    }

}
</script>
<style>
#popup-background {
    visibility: hidden;
    opacity: 0;
    transition: visibility 0.5s linear, opacity 0.5s linear;
}

#popup-background.loaded {
    visibility: visible;
    opacity: 1;
}

.noresize {
    resize: none;
}

.input-border {
    border: 1px solid #505050;
}

input::placeholder,
textarea::placeholder {
    color: #505050;
    opacity: 1;
}

.popup-button {
    min-width: 4rem;
}
</style>