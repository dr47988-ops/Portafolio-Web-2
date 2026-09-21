<template>
    <section class="page">
        <h1>Inicio</h1>
        <p>Esta es la página de inicio</p>
        <div class="grid">
            <CounterDemo />
            <ClockDemo />
        </div>
    </section>
</template>
<style>
.page {
    display: grid;
    padding: 2rem;
}
.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1rem;
}
</style>
