<template>
    <header class="app-header">
        <div class="app-brand">Nuxt Demo</div>
        <nav class="app-nav">
            <NuxtLink to="/" class="nav-link">Home</NuxtLink>
            <NuxtLink to="/contact" class="nav-link">Contact</NuxtLink>
            <NuxtLink to="/about" class="nav-link">About</NuxtLink>
            <NuxtLink to="/activity" class="nav-link">Practica</NuxtLink>
        </nav>
    </header>
</template>

<style scoped>
.app-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    background: #0c172a;
    color: #ffffff;
}
.app-brand {
    font-size: 1.5rem;
    font-weight: bold;
}
.app-nav {
    display: flex;
    gap: 1rem;
}
.nav-link {
    color: #ffffff;
    text-decoration: none;
}
.nav-link:hover {
    text-decoration: underline;
}

.router-link-active {
    color: #38c1d9;
}

</style>            
