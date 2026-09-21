<script setup>

import { ref } from "vue";
const items = ref(["Item 1", "Item 2", "Item 3"]);
</script>
<template>
    <div class="list">
        <ul>
            <li v-for="(item, index) in items" :key="index">{{ item }}</li>
        </ul>
    </div> 
</template>