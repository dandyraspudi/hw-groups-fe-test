<template>
    <div>
        <div
            class="responsive"
            v-for="(item, idx) in data"
            :key="idx"
        >
            <div class="gallery">
                <a target="_blank" :href="item.image_url">
                <img :src="item.image_url" alt="Cinque Terre" width="600" height="400">
                </a>
                <div class="desc">
                    <div>
                        {{ item.title }}
                    </div>
                    <div
                        style="display: flex; justify-content: center; margin: 1em 0;"
                    >
                        <Rating
                            :rate="item.rating"
                            @re-rating="toggleReRate"
                        />
                    </div>
                </div>
            </div>
        </div>

        <!-- <div class="responsive">
            <div class="gallery">
                <a target="_blank" href="https://picsum.photos/id/1043/800/450">
                    <img src="https://picsum.photos/id/1043/800/450" alt="Forest" width="600" height="400">
                </a>
                <div class="desc">Add a description of the image here</div>
            </div>
        </div>

        <div class="responsive">
            <div class="gallery">
                <a target="_blank" href="https://picsum.photos/id/1044/800/450">
                    <img src="https://picsum.photos/id/1044/800/450" alt="Northern Lights" width="600" height="400">
                </a>
                <div class="desc">Add a description of the image here</div>
            </div>
        </div>

        <div class="responsive">
            <div class="gallery">
                <a target="_blank" href="https://picsum.photos/id/1045/800/450">
                    <img src="https://picsum.photos/id/1045/800/450" alt="Mountains" width="600" height="400">
                </a>
                <div class="desc">Add a description of the image here</div>
            </div>
        </div>
        
        <div class="responsive">
            <div class="gallery">
                <a target="_blank" href="https://picsum.photos/id/1041/800/450">
                <img src="https://picsum.photos/id/1041/800/450" alt="Cinque Terre" width="600" height="400">
                </a>
                <div class="desc">Add a description of the image here</div>
            </div>
        </div>

        <div class="responsive">
            <div class="gallery">
                <a target="_blank" href="https://picsum.photos/id/1043/800/450">
                    <img src="https://picsum.photos/id/1043/800/450" alt="Forest" width="600" height="400">
                </a>
                <div class="desc">Add a description of the image here</div>
            </div>
        </div>

        <div class="responsive">
            <div class="gallery">
                <a target="_blank" href="https://picsum.photos/id/1044/800/450">
                    <img src="https://picsum.photos/id/1044/800/450" alt="Northern Lights" width="600" height="400">
                </a>
                <div class="desc">Add a description of the image here</div>
            </div>
        </div>

        <div class="responsive">
            <div class="gallery">
                <a target="_blank" href="https://picsum.photos/id/1045/800/450">
                    <img src="https://picsum.photos/id/1045/800/450" alt="Mountains" width="600" height="400">
                </a>
                <div class="desc">Add a description of the image here</div>
            </div>
        </div> -->

        <div class="clearfix"></div>
    </div>
</template>
  
<script>
import { defineComponent } from "@vue/runtime-core"
import Rating from './Rating.vue';
export default defineComponent({
    name: "Photo Gallery",
    data() {
        return {
        }
    },
    components: {
        Rating
    },
    props: {
        data: Array
    },
    methods: {
        toggleReRate(value) {
        }
    }
})
</script>

<style scoped>
div.gallery {
  border: 1px solid #ccc;
}

div.gallery:hover {
  border: 1px solid #777;
}

div.gallery img {
  width: 100%;
  height: auto;
}

div.desc {
  padding: 15px;
  text-align: center;
  min-height: 5em;
}

* {
  box-sizing: border-box;
}

.responsive {
  padding: 0 6px;
  float: left;
  width: 24.99999%;
  margin: .5em 0;
}

@media only screen and (max-width: 700px) {
  .responsive {
    width: 49.99999%;
    margin: 6px 0;
  }
}

@media only screen and (max-width: 500px) {
  .responsive {
    width: 100%;
  }
}

.clearfix:after {
  content: "";
  display: table;
  clear: both;
}
</style>
  