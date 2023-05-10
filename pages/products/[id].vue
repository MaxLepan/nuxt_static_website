<template>
    <main>
        <h1>Product #{{ id }}</h1>
        <nav>
            <ul>
                <li>
                    <nuxt-link to="/">Homepage</nuxt-link>
                </li>
                <li>
                    <nuxt-link to="/about">About</nuxt-link>
                </li>
                <li>
                    <nuxt-link to="/contact">Contact</nuxt-link>
                </li>
            </ul>
        </nav>
    </main>
</template>

<script setup>
const route = useRoute()

const {id} = route.params;
</script>