<template>
    <main>
        <h1>Homepage</h1>
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
        <h2>Products</h2>
        <ul>
            <li>
                <nuxt-link to="/products/1">Product #1</nuxt-link>
            </li>
            <li>
                <nuxt-link to="/products/2">Product #2</nuxt-link>
            </li>
            <li>
                <nuxt-link to="/products/3">Product #3</nuxt-link>
            </li>
        </ul>
    </main>
</template>
<script lang="ts" setup>
</script>