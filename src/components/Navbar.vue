<template>
    <div class="topnav">
        <img
            src="@/assets/images/hw_logo_white.png"
            width="120"
            height="100"
            style="height: 100%;"
        />
        <span
            style="color: #fff; font-weight: 600; display: flex; align-items: center; letter-spacing: .1em; font-size: 1.4em;"
        >
            | HW Groups
        </span>
    </div>
</template>
    
<script>
  import { defineComponent } from "@vue/runtime-core"
  export default defineComponent({
      name: "Tooltip",
      data() {
          return {
          }
      },
      props: {
        imagePreview: String,
        title: String,
        description: String
      },
      methods: {
      },
      created() {
      }
  })
</script>
    
<style scoped>
.topnav {
  overflow: hidden;
  background: rgb(27,27,27);
  height: 5em;
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 999;
  display: flex;
  justify-content: start;
}

.topnav a {
  float: left;
  color: #f2f2f2;
  text-align: center;
  padding: 0 16px;
  text-decoration: none;
  font-size: 1.5em;
  height: 100%;
  display: flex;
  align-items: center;
}

.topnav a:hover {
  color: black;
}

.topnav a.active {
  color: white;
}
</style>
    