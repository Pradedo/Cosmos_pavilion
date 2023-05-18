<template>
    <div class="slide">
        <img v-bind:src="slide.src" alt="">
    </div>
</template>

<script>
    export default {
        data () {
            return {}
        },
        props: {
            slide: {
                slide: ['slide']
            }
        }
    }
</script>
<style scoped>
    img {
        width: inherit;
        height: inherit;
    }
    .slide {
        display: inline;
    }
</style>