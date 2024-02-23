<template>
  <!-- Loader -->
  <div v-if="loading" class="loader-container">
    <div class="loader">
    </div>
  </div>

  <!-- Your main content -->
  <div v-if="!loading" class="main-content">
    <RouterView />
  </div>
</template>

<script>
import { RouterView } from 'vue-router'
import { defineComponent } from "@vue/runtime-core"
export default defineComponent({
    name: "App",
    data() {
        return {
            loading: true
        }
    },
    mounted() {
      setTimeout(() => {
        this.loading = false;
      }, 3000); 
    }
})
</script>

<style scoped>
html {
  scroll-behavior: smooth;
}
.loader-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(255, 255, 255, 0.8);
  display: flex;
  justify-content: center;
  align-items: center;
}

/* .loader {
  border: 8px solid #f3f3f3;
  border-top: 8px solid #3498db;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  animation: spin 2s linear infinite;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

.main-content {
} */
.loader {
  width: 100px;
  height: 45px;
  position: relative;
}
.loader:before,
.loader:after {
  content: "";
  position: absolute;
  inset: 0;
  background: #000;
  box-shadow: 0 0 0 50px;
  /* background-image: url('./assets/images/hw_logo.png'); */
  clip-path: polygon(-50px -20px,10% -12px,20% 0,calc(50% - 15px) 0,calc(50% - 10px) -20px,calc(50% - 8px) -15px,calc(50% + 8px) -15px,calc(50% + 10px) -20px,calc(50% + 15px) 0,80% 0,90% -12px,calc(100% + 50px) -20px,100% 80%,calc(100% + 10px) calc(100% + 10px),60% 100%,50% calc(100% + 15px),40% 100%,-10px calc(100% + 10px),0 80%);
}
.loader:after {
  animation: l9 1s infinite;
  transform: perspective(300px) translateZ(0px)
}
@keyframes l9 {
  to {transform:perspective(300px) translateZ(100px);opacity:0}
}
</style>