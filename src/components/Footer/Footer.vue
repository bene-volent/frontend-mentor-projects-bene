<template>
    <footer>
        <p>Inspiration from <a href="https://catherineisonline.github.io/frontend-mentor-challenge-solutions/" target="_blank">Ekaterine's
                Website</a></p>
        <p><a href="https://github.com/catherineisonline" target="__blank" class="github">
                <Icon icon="mdi:github"></Icon>Ekaterine (Catherine) Mitagvaria
            </a></p>
    </footer>
</template>

<script setup>
import { Icon } from '@iconify/vue';
</script>

<style lang="scss" scoped>
footer{
    background-color: rgb(228, 228, 228);
    text-align: center;
    font-size: var(--size-4);
    padding-block: var(--size-8);
    .github{
        display: flex;
        justify-content: center;
        align-items: center;
        gap: var(--size-2);

    }
    a{
        text-decoration: underline;
        text-underline-offset: 0.25em;
    }
}
</style>