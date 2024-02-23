<template>
  <div class="tooltip">
      <slot></slot>
      <div class="tooltiptext">
        <img :src="imagePreview" alt="" style="width: 100%;">
        <div style="text-align: left; padding: .3em .5em;">
          <span>
            <b>
              {{title}}
            </b>
          </span>
        </div>
        <div style="text-align: left; padding: .3em .5em; font-size: 12px;">
          <span>
            {{description}}
          </span>
        </div>
      </div>
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
/* Tooltip container */
.tooltip {
  position: relative;
  display: inline-block;
}

/* Tooltip text */
.tooltip .tooltiptext {
  visibility: hidden;
  width: 300px;
  min-height: 100px;
  background-color: #fff;
  color: #555;
  text-align: center;
  padding: 5px 0;
  border-radius: 10px;

  /* Position the tooltip text */
  position: absolute;
  z-index: 1;
  bottom: 50%;
  left: 80%;
  margin-left: -60px;

  /* Fade in tooltip */
  opacity: 0;
  transition: opacity 0.3s;
}

/* Tooltip arrow */
.tooltip .tooltiptext::after {
  content: "";
  position: absolute;
  top: 100%;
  left: 20%;
  margin-left: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: #555 transparent transparent transparent;
}

/* Show the tooltip text when you mouse over the tooltip container */
.tooltip:hover .tooltiptext {
  visibility: visible;
  opacity: 1;
}
</style>
  