<template>
    <div class="rate">
        <input type="radio" id="star5" name="rate" value="5" @click="rated(5)" />
        <label for="star5" title="text" :style="rateData>=5 ? 'color: #ffc700;' : ''">5 stars</label>
        <input type="radio" id="star4" name="rate" value="4" @click="rated(4)" />
        <label for="star4" title="text" :style="rateData>=4 ? 'color: #ffc700;' : ''">4 stars</label>
        <input type="radio" id="star3" name="rate" value="3" @click="rated(3)" />
        <label for="star3" title="text" :style="rateData>=3 ? 'color: #ffc700;' : ''">3 stars</label>
        <input type="radio" id="star2" name="rate" value="2" @click="rated(2)" />
        <label for="star2" title="text" :style="rateData>=2 ? 'color: #ffc700;' : ''">2 stars</label>
        <input type="radio" id="star1" name="rate" value="1" @click="rated(1)" />
        <label for="star1" title="text" :style="rateData>=1 ? 'color: #ffc700;' : ''">1 star</label>
    </div>
</template>
  
<script>
import { defineComponent } from "@vue/runtime-core"
export default defineComponent({
    name: "Rating",
    data() {
        return {
            rateData: this.rate
        }
    },
    props: {
        rate: Number
    },
    methods: {
        rated(value) {
            this.$emit('re-rating', value)
        }
    }
})
</script>
  
<style scoped>
.rate {
    float: left;
    height: 1em;
    padding: 0 10px;
}
.rate:not(:checked) > input {
    position:absolute;
    top:-9999px;
}
.rate:not(:checked) > label {
    float:right;
    width:1em;
    overflow:hidden;
    white-space:nowrap;
    cursor:pointer;
    font-size:1em;
    color:#ccc;
}
.rate:not(:checked) > label:before {
    content: '★ ';
}
.rate > input:checked ~ label {
    color: #ffc700;    
}
.rate:not(:checked) > label:hover,
.rate:not(:checked) > label:hover ~ label {
    color: #deb217;  
}
.rate > input:checked + label:hover,
.rate > input:checked + label:hover ~ label,
.rate > input:checked ~ label:hover,
.rate > input:checked ~ label:hover ~ label,
.rate > label:hover ~ input:checked ~ label {
    color: #c59b08;
}
</style>
  