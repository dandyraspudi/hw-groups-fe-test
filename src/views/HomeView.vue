<template>
  <div style="scroll-behavior: smooth;">
    <!-- navbar -->
    <Navbar/>

    <!-- carousel -->
    <div id="top">
      <Image-Carousel
        :data="listDataCarousel"
      />
    </div>

    <Tooltip/>

    <!-- search -->
    <div
      style="display: flex; justify-content: center; padding: 3em 0; margin-top: 4em;"
    >
      <Search
        @search="onSearch"
        :data="listData"
      />
    </div>

    <!-- list gallery -->
    <div>
      <Photo-Gallery
        v-if="reRender"
        :data="listData"
      />
      <div
        v-if="loading"
        style="margin: 3em 0; display: flex; justify-content: center;"
      >
        <Loader/>
      </div>
    </div>

    <!-- nav -->
    <div
      class="nav"
    >
      <a href="#top" class="nav-item">
        Top
      </a>
    </div>

    <!-- footer -->
    <div>
      <Footer/>
    </div>
  </div>
</template>

<script>
import { defineComponent } from "@vue/runtime-core"
import Search from '@/components/Search.vue';
import PhotoGallery from '@/components/PhotoGallery.vue';
import ImageCarousel from '@/components/ImageCarousel.vue';
import Tooltip from '@/components/Tooltip.vue';
import imageData from '../data/images.json';
import Loader from '@/components/Loader.vue';
import Footer from '@/components/Footer.vue';
import Navbar from "@/components/Navbar.vue";

export default defineComponent({
    name: "HomeLayout",
    data() {
        return {
          listData: [],
          loading: false,
          listDataCarousel: [],
          reRender: true
        }
    },
    components: {
      Search,
      PhotoGallery,
      ImageCarousel,
      Tooltip,
      Loader,
      Footer,
      Navbar
    },
    created() {
      imageData.map((item, idx) => {
        if (idx <= 10) {
          this.listData.push(item);
        }

        if (idx <= 3) {
          this.listDataCarousel.push(item);
        }
      });
    },
    mounted() {
      window.addEventListener('scroll', this.handleScroll);
    },
    destroyed() {
      window.removeEventListener('scroll', this.handleScroll);
    },
    methods: {
      handleScroll() {
        // Check if user has scrolled to the bottom of the page
        if ((window.innerHeight + window.scrollY + 100) >= document.body.offsetHeight) {
          console.log(window.innerHeight + window.scrollY, " <<window.innerHeight")
          console.log(document.body.offsetHeight, " <<document.body.offsetHeight")
          // User has scrolled to the bottom of the page
          this.loadMoreContent();
        }
      },
      loadMoreContent() {
        // Your logic to load more content when user reaches bottom of the page
        this.loading=true;
        setTimeout(() => {
          imageData.map((item, idx) => {
            if (idx <= 10) {
              this.listData.push(item);
            }
            this.loading=false;
          })
        }, 3000); 
      },
      onSearch(value) {
        this.reRender=false;
        this.loading=true;

        setTimeout(() => {
          this.listData.map((item, idx) => {
            if (item.title === value) {
              this.listData = [item];
            } else if (value === '') {

              this.loading=true;
              setTimeout(() => {
                if (idx <= 10) {
                  this.listData.push(item);
                }
                this.loading=false;
              }, 2000); 

            }
          })
        }, 1500); 

        this.loading=false;
        this.reRender=true;
      }
    }
})
</script>

<style scoped>
.nav {
  position: -webkit-sticky;
  position: sticky;
  bottom: 2.5em;
  right: auto;
  scroll-behavior: smooth;
  display: flex;
  justify-content: end;
  padding-right: 2em;
}

.nav-item {
  text-decoration: none;
  padding: 1em;
  background-color: rgb(27,27,27);
  color: #fff;
  font-weight: #fff;
  border-radius: 5px;
}
</style>