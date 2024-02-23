<template>
    <div
        class="search-container"
    >
        <div class="search-content">
            <img
                src="@/assets/images/search.png"
                width="20"
                height="20"
            />
            <input class="search-item" type="text" v-model="searchQuery" @input="filterOptions" placeholder="Type to search..." @keypress="onEnter">
        </div>
        <ul v-if="filteredOptions.length > 0" class="autocomplete-list">
            <li v-for="(option, index) in filteredOptions" :key="index" @click="selectOption(option)">
                {{ option.title }}
            </li>
        </ul>
    </div>
</template>

<script>
import { defineComponent } from "@vue/runtime-core"

export default defineComponent({
    name: "Search",
    data() {
        return {
            searchQuery: '',
            options: this.data,
            filteredOptions: []
        }
    },
    props: {
        data: Array
    },
    methods: {
        filterOptions() {
            if (!this.searchQuery) {
                this.filteredOptions=[];
            } else if (this.searchQuery) {
                this.filteredOptions = this.options.filter(option =>
                    option.title.toLowerCase().includes(this.searchQuery.toLowerCase())
                );
            }
        },
        selectOption(option = '') {
            this.searchQuery = option.title || '';
            this.filteredOptions = [];
            this.searchAction(this.searchQuery);
        },
        searchAction(value) {
            this.$emit('search', value);
        },
        onEnter(e) {
            if (e.key === 'Enter') {
                this.selectOption()
            }
        }
    },
    created() {
    }
})
</script>

<style scoped>
.search-container {
    z-index: 99;
    border: 1px solid #878787;
    border-radius: 30px;
    width: 100%;
    height: 3em;
    max-width: 30em;
    margin: 0 1em;
    position: relative;
    background-color: #fff;
    display: inline-block;
}
.search-content {
    display: flex;
    align-items: center;
    gap: .3em;
    padding: 0 .5em;
    width: 100%;
    height: 100%;
}
.search-item {
    height: 100%;
    width: 100%;
    border-radius: 30px;
    border: none;
    padding: 0 1em;
    outline: none;
}

.autocomplete {
  position: relative;
  display: inline-block;
}

.autocomplete-list {
  list-style-type: none;
  padding: 0;
  margin: 0;
  background-color: #fff;
  margin-top: 1em;
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  border: 1px solid;
  width: 100%;
}

.autocomplete-list li {
  padding: 8px;
  cursor: pointer;
  padding: 1em 1em;
}

.autocomplete-list li:hover {
  background-color: #f4f4f4;
  padding: 1em 1em;
}
</style>
