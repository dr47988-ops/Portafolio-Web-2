<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
const now = ref(new Date().toLocaleTimeString());

//https://www.w3schools.com/js/js_timers.asp
onMounted(() => {
    const timer = setInterval(() => {
        now.value = new Date().toLocaleTimeString();
    }, 1000);

    onBeforeUnmount(() => {
        clearInterval(timer);
    });
});

</script>


<template>
    <article>
        <h2>Reloj</h2>
        <p>Hora actual: {{ now }}</p>
    </article> 
</template>