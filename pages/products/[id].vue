<template>
    <main>
        <h1>Product #{{ id }}</h1>
        <nav>
            <nuxt-link to="/">Homepage</nuxt-link>
            <nuxt-link to="/about">About</nuxt-link>
            <nuxt-link to="/contact">Contact</nuxt-link>
        </nav>
    </main>
</template>

<script setup>
const route = useRoute()

const {id} = route.params;
</script>