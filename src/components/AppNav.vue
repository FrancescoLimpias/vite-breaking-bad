<script>

// Store import
import { store } from "../store.js";

export default {

    // Component Name
    name: "AppNav",

    // Component Data
    data() {
        return {
            store,
        };
    },
}

</script>

<template>

    <!-- Nav Bar -->
    <div class="pager AppNav">
        <!-- Character status selector -->
        <select name="status" v-model="store.filter" @input="$emit('filterUpdate')">
            <option value="alive">Alive</option>
            <option value="dead">Dead</option>
            <option value="unknown">Unknown</option>
        </select>

        <!-- Filter tag -->
        <span v-if="store.filter" class="filterTag" @click="$emit('filterRemove')">
            {{ store.filter }} | x
        </span>
    </div>


</template>

<style lang="scss" scoped>
.AppNav {
    padding: .5rem;
    display: flex;
    align-items: baseline;
}

.filterTag {
    margin-left: .5rem;
    background-color: greenyellow;
    border-radius: 15px;
    padding: 0px 6px;
    text-transform: uppercase;

    &:hover{
        background-color: red;
        cursor: pointer;
    }
}
</style>