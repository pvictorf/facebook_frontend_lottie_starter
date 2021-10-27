<template>
    <div class="lottie-animation">
        <lottie 
            class="anim" 
            :width="width" 
            :height="height" 
            :options="options" 
        />
    </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
    props: {
        animation: { type: String, required: true },
        width: { type: Number, default: 40 },
        height: { type: Number, default: 40 },
        speed: { type: Number, default: 1 },
        loop: { type: Boolean, default: true },
        autoplay: { type: Boolean, default: true },
    },
    data() {
        return {
            options: {
                animationData: require(`@/assets/animations/${this.animation}.json`),
                speed: this.speed,
                loop: this.loop,
                autoplay: this.autoplay

            }
        }
    }
})
</script>

<style lang="scss" scoped>
.anim {
    border-radius: 50%;
    
} 
</style>