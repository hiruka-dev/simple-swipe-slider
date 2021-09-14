<template>
    <div class="simple-swipe-slider">
        <div>
            <div ref="imagesContainer" class="images-container">
                <div v-for="image in images" 
                    :key="image" 
                    class="image-wrapper" 
                    @touchstart.prevent="touchStart"
                    @touchmove="touchMove"
                    @touchend="touchEnd"
                >
                    <img :src="image" class="image"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SimpleSwipeSlider',
    props: [
        'images'
    ],
    data () {
        return {
            position: 0,
            startX: 0,
            moveX: 0,
            width: 0,
            currentIndex: 0
        }
    },
    methods: {
        touchStart (e) {
            this.width = this.$refs.imagesContainer.offsetWidth;
            this.startX = e.touches[0].pageX;
        },
        touchMove (e) {
            this.moveX = e.touches[0].pageX - this.startX;
            this.$refs.imagesContainer.style.transitionDuration = "0ms";
            this.$refs.imagesContainer.style.transform = `translate3d(${this.moveX + this.position}px,0,0)`;
        },
        touchEnd () {
            if (this.moveX > 50 && this.currentIndex !== 0) {
                this.position = this.position + this.width;
                this.$refs.imagesContainer.style.transitionDuration = "300ms";
                this.$refs.imagesContainer.style.transform = `translate3d(${this.position}px,0,0)`;
                this.currentIndex--;
            } else if (this.moveX < -50 && this.currentIndex !== this.images.length - 1) {
                this.position = this.position - this.width;
                this.$refs.imagesContainer.style.transitionDuration = "300ms";
                this.$refs.imagesContainer.style.transform = `translate3d(${this.position}px,0,0)`;
                this.currentIndex++;
            } else {
                this.$refs.imagesContainer.style.transitionDuration = "300ms";
                this.$refs.imagesContainer.style.transform = `translate3d(${this.position}px,0,0)`;        
            }
        }
    }

}
</script>

<style scoped lang="scss">
.simple-swipe-slider {
    overflow-x: hidden;

    .images-container {
        display: flex;

        .image-wrapper {
            flex-shrink: 0;
            width: 100%;
            height: 100%;

            .image {
                width: 100%;
                height: 100%;
            }
        }
    }
}
</style>
