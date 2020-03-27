<template>
    <span class="button-container">
        <button class="button" @click="doSomething">Do Something</button>
        <button class="button" @click="doSomethingElse">Do Something Else</button>
        <button class="button" @click="doNothingAtAll">Another Thing</button>
    </span>
</template>

<script>
import { EventBus, MESSAGES } from '../EventBus.js'
const FIVE_SECONDS = 5000
// const TEN_SECONDS = 10000
export default {
    name: 'ButtonHolder',
    methods: {
        doSomething() {
            EventBus.$emit(MESSAGES, {
                show: true,
                text: 'Hey! Thanks man, you just did something :)',
                bgColor: 'aduro-red',
                textColor: 'white',
                timeToLive: FIVE_SECONDS,
            })

        },
        doSomethingElse() {
            EventBus.$emit(MESSAGES, {
                show: true,
                text: 'Hey! Thanks dude you just did something else :)',
                bgColor: 'aduro-blue',
                textColor: 'white',
                timeToLive: FIVE_SECONDS,
            })
        },
        doNothingAtAll() {
            EventBus.$emit(MESSAGES, {
                show: true,
                text: 'Yo thanks bro! you just did another thing :)',
                bgColor: 'aduro-green',
                textColor: 'white',
                timeToLive: FIVE_SECONDS,
            })
        }
    }
}
</script>

<style lang="scss" scoped>
.button {
    margin: 20px;
}
.button-container {
    width: 100%;
    flex-direction: row;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
}
</style>