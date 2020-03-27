<template>
    <div class="app-master-container flex-help">

        <navbar></navbar>

        <buttonholder></buttonholder>

        <transition name="slide-fade" mode="out-in">
            <adurotoast
                v-if="showToast"
                v-bind="{ text, textColor, bgColor, timeToLive }"
            ></adurotoast>
        </transition>

    </div>
</template>

<script>
import { EventBus, MESSAGES } from './EventBus.js'
import adurotoast from './components/adurotoast'
import buttonholder from './components/buttonholder'
import navbar from './components/navbar'
export default {
    name: 'App',
    components: {
        adurotoast,
        buttonholder,
        navbar,
    },
    data() {
        return {
            showToast: false,
            text: '',
            bgColor: '',
            textColor: '',
            timeToLive: 0
        }
    },
    mounted() {
        EventBus.$on(MESSAGES, (payload) => {
            this.showToast = payload.show
            this.text = payload.text || ''
            this.bgColor = payload.bgColor || ''
            this.textColor = payload.textColor || ''
            this.timeToLive = payload.timeToLive || 0
        })
    }
}
</script>

<style lang="scss" scoped>
.flex-help {
    display: flex;
    align-items: center;
    justify-content: center;
}
.app-master-container {
    height: 100vh;
    width: 100%;
    flex-direction: column;
}
</style>

<style>

</style>
