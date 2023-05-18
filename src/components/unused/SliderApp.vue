<template>
    <div class="slides">
        <div v-bind:style="{width: innerWidth + 'px', marginLeft: '-' + slidesInnerMarginLeft + 'px'}" class="slides-inner">
            <SlideOne v-for="slide in slides" v-bind:key="slide.id" v-bind:style="{width: singleWidth+'px'}" v-bind:slide="slide"></SlideOne>
        </div>
        <div class="navigation">
            <span v-on:click="goToPrev">Prev</span>
            <span class="nav-number" v-bind:class="[$index === currentIndex ? 'current': '']" v-on:click="goToSlideIndex" v-for="slide in slides" v-bind:key="slide.id">{{$index+1}}</span>
            <span v-on:click="goToNext">Next</span>
        </div>
    </div>
</template>
<script>
    import SlideOne from "@/components/SlideOne";
    export default {
        data() {
            return {
                slides: [
                    {id:1, src:'img/file_1.jpg'},
                    {id:2, src:'img/file_2.jpg'}
                ],
                innerWidth:0,
                singleWidth:0,
                currentIndex:0
            }
        },
        computed: {
            slidesInnerMarginLeft () {
                return this.currentIndex * this.singleWidth
            }
        },
        methods: {
            goToPrev() {
                if (this.currentIndex === 0){
                    return
                }
                this.currentIndex--
            },
            goToNext() {
                if (this.currentIndex === this.slides.length - 1){
                    return
                }
                this.currentIndex++
            },
            goToSlideIndex(index) {
                this.currentIndex = index
            }
        },
        props: {
            itemsPerSlide: {
                type: null,
                default: 2
            },
            startingIndex: {
                type: null,
                default: 0
            }
        },
        components: {
            SlideOne
        },
        attached() {
            let singleWidth = this.$el.clintWidth/this.itemsPerSlide
            this.$set('singleWidth',singleWidth)
            this.$set('currentIndex', this.$get('startingIndex'))
            this.$set('singleWidth',singleWidth)
            this.$set('innerWidth',innerWidth * this.slides.length)
        }
    }
</script>
<style scoped>
.slides {
    overflow: hidden;
    text-align: center;
}
.slider-inner {
    transition: margin 0.6s ease-out;
}
.nav-number {
    margin: 0 5px;
    background-color: grey;
    padding: 0 5px;
    border: 1px solid black;
    cursor: pointer;
}
.nav-number, current {
    color: white;
    background-color: black;
}
</style>