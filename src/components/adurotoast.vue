<template>
    <div
        class="aduro-toast-container"
        :class="bgColor"
        :style="{ 'color': textColor }"
    >{{ text }}
    </div>
</template>
  
<script>
import { EventBus, MESSAGES } from '../EventBus.js'
export default {
    name: 'AduroToast',
    props: {
        text: {
            type: String
        },
        bgColor: {
            type: String,
            validator: (value) => {
                return ['aduro-red', 'aduro-blue', 'aduro-green', ''].indexOf(value) !== -1
            }
        },
        textColor: {
            type: String
        },
        timeToLive: {
            type: Number,
            required: false,
            default: 5000
        }
    },
    mounted() {
        setTimeout(() => {
            EventBus.$emit(MESSAGES, { show: false })
        }, this.timeToLive)
    }
}
</script>

<style lang="scss" scoped>
.aduro-toast-container {
    position: absolute;
    top: 20px;
    right: 20px;
    padding: 20px;
    border-radius: 3px;
    font-family: $heading-font;
    display: flex;
    flex-direction: column;
    &:after {
        content: "";
        height: 4px;
        background: black;
        opacity: 0.2;
        width: calc(100% + 40px);
        position: relative;
        top: 20px;
        right: 20px;
        animation: move 6.5s linear infinite;
    }
}
@keyframes move {
  0% {
    width: calc(100% + 40px);
  }
  100% {
    width: 0;
  }
}
.aduro-red {
    background-color: $a-red;
}
.aduro-blue {
    background-color: $a-blue;
}
.aduro-green {
    background-color: $a-green;
}
</style>