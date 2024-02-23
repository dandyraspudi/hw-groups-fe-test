<template>
    <div class="container">
        <div class="carousel">
            <input type="radio" name="slides" checked="checked" id="slide-1">
            <input type="radio" name="slides" id="slide-2">
            <input type="radio" name="slides" id="slide-3">
            <input type="radio" name="slides" id="slide-4">
            <input type="radio" name="slides" id="slide-5">
            <input type="radio" name="slides" id="slide-6">
            <ul class="carousel__slides">
                <li class="carousel__slide">
                    <div>
                        <img src="https://via.placeholder.com/640x480.png/002288?text=Bali" alt="">
                    </div>
                </li>
                <li class="carousel__slide">
                    <div>
                        <img src="https://via.placeholder.com/640x480.png/002299?text=Lombok" alt="">
                    </div>
                </li>
                <li class="carousel__slide">
                    <div>
                        <img src="https://via.placeholder.com/640x480.png/0055ff?text=Jakarta" alt="">
                    </div>
                </li>
                <li class="carousel__slide">
                    <div>
                        <img src="https://via.placeholder.com/640x480.png/0011aa?text=Yogyakarta" alt="">
                    </div>
                </li>
                <li class="carousel__slide">
                    <div>
                        <img src="https://via.placeholder.com/640x480.png/00dd11?text=Papua" alt="">
                    </div>
                </li>
                <li class="carousel__slide">
                    <div>
                        <img src="https://via.placeholder.com/640x480.png/0033aa?text=Bangka+Belitung" alt="">
                    </div>
                </li>
            </ul>    
            <ul class="carousel__thumbnails">
                <li>
                    <label for="slide-1">
                        <tooltip
                            imagePreview="https://via.placeholder.com/640x480.png/002288?text=Bali"
                            title="Bali"
                            description="Discover the enchanting beauty of Bali with our exquisite product. Inspired by the vibrant culture and breathtaking landscapes of this Indonesian paradise, our product captures the essence of Bali's charm."
                        >
                            <img src="https://via.placeholder.com/640x480.png/002288?text=Bali" alt="">
                        </tooltip>
                    </label>
                </li>
                <li>
                    <label for="slide-2">
                        <tooltip
                            imagePreview="https://via.placeholder.com/640x480.png/002299?text=Lombok"
                            title="Lombok"
                            description="Experience the elegance and sophistication of Lombok today."
                        >
                            <img src="https://via.placeholder.com/640x480.png/002299?text=Lombok" alt="">
                        </tooltip>
                    </label>
                </li>
                <li>
                    <label for="slide-3">
                        <tooltip
                            imagePreview="https://via.placeholder.com/640x480.png/0055ff?text=Jakarta"
                            title="Jakarta"
                            description="Discover the vibrant and bustling city of Jakarta with our comprehensive travel guide."
                        >
                            <img src="https://via.placeholder.com/640x480.png/0055ff?text=Jakarta" alt="">
                        </tooltip>
                    </label>
                </li>
                <li>
                    <label for="slide-4">
                        <tooltip
                            imagePreview="https://via.placeholder.com/640x480.png/0011aa?text=Yogyakarta"
                            title="Yogyakarta"
                            description="This vibrant city is home to numerous ancient temples, including the famous Borobudur and Prambanan temples, which attract tourists from around the world."
                        >
                            <img src="https://via.placeholder.com/640x480.png/0011aa?text=Yogyakarta" alt="">
                        </tooltip>
                    </label>
                </li>
                <li>
                    <label for="slide-5">
                        <tooltip
                            imagePreview="https://via.placeholder.com/640x480.png/00dd11?text=Papua"
                            title="Papua"
                            description="Discover the untouched beauty of Papua with our exclusive vacation package. Immerse yourself in the rich culture and stunning landscapes of this remote destination, where crystal-clear waters meet lush rainforests."
                        >
                            <img src="https://via.placeholder.com/640x480.png/00dd11?text=Papua" alt="">
                        </tooltip>
                    </label>
                </li>
                <li>
                    <label for="slide-6">
                        <tooltip
                            imagePreview="https://via.placeholder.com/640x480.png/0033aa?text=Bangka+Belitung"
                            title="Bangka Belitung"
                            description="Immerse yourself in the crystal-clear waters, white sandy beaches, and unique rock formations that make this destination a true paradise."
                        >
                            <img src="https://via.placeholder.com/640x480.png/0033aa?text=Bangka+Belitung" alt="">
                        </tooltip>
                    </label>
                </li>
            </ul>
        </div>
    </div>
</template>
  
<script>
import { defineComponent } from "@vue/runtime-core"
import Tooltip from '@/components/Tooltip.vue';
export default defineComponent({
    name: "Image Carousel",
    data() {
        return {
            listData: this.data
        }
    },
    props: {
        data: Array
    },
    components: {
        Tooltip
    }
})
</script>

<style scoped>
@mixin aspect-ratio($width, $height) {
  position: relative;
    
  &:before {
    display: block;
    content: "";
    width: 100%;
    padding-top: ($height / $width) * 100%;
  }
    
  > img {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        width: 100%;
        height: 100%;
  }
}

.container {
    margin: 0 auto;
    overflow-y: hidden;
}

.carousel {
    display: block;
    text-align: left;
    position: relative;
    margin-bottom: 22px;
    width: 100%;
    
    > input {
        clip: rect(1px, 1px, 1px, 1px);
        clip-path: inset(50%);
        height: 1px;
        width: 1px;
        margin: -1px;
        overflow: hidden;
        padding: 0;
        position: absolute;
        
        &:nth-of-type(6):checked ~ .carousel__slides .carousel__slide:first-of-type { margin-left: -500%; }
        &:nth-of-type(5):checked ~ .carousel__slides .carousel__slide:first-of-type { margin-left: -400%; }
        &:nth-of-type(4):checked ~ .carousel__slides .carousel__slide:first-of-type { margin-left: -300%; }
        &:nth-of-type(3):checked ~ .carousel__slides .carousel__slide:first-of-type { margin-left: -200%; }
        &:nth-of-type(2):checked ~ .carousel__slides .carousel__slide:first-of-type { margin-left: -100%; }
        &:nth-of-type(1):checked ~ .carousel__slides .carousel__slide:first-of-type { margin-left: 0%; }
        
        &:nth-of-type(1):checked ~ .carousel__thumbnails li:nth-of-type(1) { box-shadow: 0px 0px 0px 5px rgba(0,0,255,0.5); }
        &:nth-of-type(2):checked ~ .carousel__thumbnails li:nth-of-type(2) { box-shadow: 0px 0px 0px 5px rgba(0,0,255,0.5); }
        &:nth-of-type(3):checked ~ .carousel__thumbnails li:nth-of-type(3) { box-shadow: 0px 0px 0px 5px rgba(0,0,255,0.5); }
        &:nth-of-type(4):checked ~ .carousel__thumbnails li:nth-of-type(4) { box-shadow: 0px 0px 0px 5px rgba(0,0,255,0.5); }
        &:nth-of-type(5):checked ~ .carousel__thumbnails li:nth-of-type(5) { box-shadow: 0px 0px 0px 5px rgba(0,0,255,0.5); }
        &:nth-of-type(6):checked ~ .carousel__thumbnails li:nth-of-type(6) { box-shadow: 0px 0px 0px 5px rgba(0,0,255,0.5); }
    }
}

.carousel__slides {
    position: relative;
    z-index: 1;
    padding: 0;
    margin: 0;
    overflow: hidden;
    white-space: nowrap;
    box-sizing: border-box;
    display: flex;
    border-image: fill 0 linear-gradient(#0001, #000);
}

.carousel__slide {
    position: relative;
    display: block;
    flex: 1 0 100%;
    width: 100%;
    height: 100%;
    overflow: hidden;
    transition: all 300ms ease-out;
    vertical-align: top;
    box-sizing: border-box;
    white-space: normal;
    border-image: fill 0 linear-gradient(#0001, #000);
    
    div {
        width: 100%;
    }
    
    img {
        display: block;
        flex: 1 1 auto;
        object-fit: cover;
        width: 100%;
        height: 80vh !important;
        border-image: fill 0 linear-gradient(#0001, #000);
    }
    
    .credit {
        margin-top: 1rem;
        color: rgba(0, 0, 0, 0.5);
        display: block;        
    }
    
    &.scrollable {
        overflow-y: scroll;
    }
}

.carousel__thumbnails {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    margin: 0 -10px;
    padding: 0 3em;
    
    .carousel__slides + & {
        margin-top: 20px;
    }
    
    li {        
        flex: 1 1 auto;
        max-width: calc((100% / 6) - 20px);  
        margin: 0 10px;
        transition: all 300ms ease-in-out;
    }
    
    label {
        display: block;
        @include aspect-ratio(1,1);
        
                  
        &:hover,
        &:focus {
            cursor: pointer;
            
            img {
                box-shadow: 0px 0px 0px 1px rgba(0,0,0,0.25);
                transition: all 300ms ease-in-out;
            }
        }
    }
    
    img {
        display: block;
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
}
</style>
  