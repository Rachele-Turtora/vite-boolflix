<script>
import { store } from "../store";

export default {
    name: "SearchComponent",
    emits: ["search"],
    data() {
        return {
            store
        }
    },
    methods: {
        toggleInput() {
            this.store.displayInput = !this.store.displayInput
        }
    }
}
</script>

<template>
    <div class="search">
        <div class="input-field" :class="{ expanded: store.displayInput }">
            <i class="fa fa-search" @click="toggleInput()" aria-hidden="true"></i>
            <input type="text" placeholder="Titoli" @change="$emit('search')" v-model="store.searchKey">
        </div>
        <button @click="$emit('search')">Invio</button>
    </div>
</template>

<style scoped>
.search {
    margin: 10px;
}

.fa-search {
    color: white;
}

i {
    font-size: 25px;
}

.input-field {
    display: inline-block;
    position: relative;
    margin-right: 10px;
}

.input-field .fa-search {
    position: absolute;
    padding-left: 15px;
    font-size: 20px;
    line-height: 40px;
}

.input-field input {
    background-color: black;
    color: white;
    height: 40px;
    padding-left: 35px;
    border: none;
    transition: width 1s ease;
    width: 0;
}

.input-field.expanded input {
    width: 200px;
    border: 1px solid white;
}

.input-field input::placeholder {
    padding-left: 0;
    font-size: 16px;
}

input,
button {
    padding: 8px;
    margin-left: 5px;
}

button {
    background-color: red;
    color: white;
    font-weight: 700;
    border-radius: 5px;
    margin-left: 20px;
}
</style>