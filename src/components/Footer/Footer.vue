<template>
    <footer>
        <p>Inspiration from <a href="https://catherineisonline.github.io/frontend-mentor-challenge-solutions/" target="_blank">Ekaterine's
                Website</a></p>

        <p><a href="https://github.com/catherineisonline" target="__blank" class="github">
                <Icon icon="mdi:github"></Icon>Ekaterine (Catherine) Mitagvaria
            </a></p>

            <p><a href="https://github.com/bene-volent" target="__blank" class="github">
                <Icon icon="mdi:github"></Icon>Benevolent
            </a></p>
    </footer>
</template>

<script setup>
import { Icon } from '@iconify/vue';
</script>

<style lang="scss" scoped>
footer{
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;

    background-color: #fff;
    text-align: center;
    font-size: var(--size-4);
    padding-block: var(--size-8);

    box-shadow: 0 -15px 24px -11px hsl(0deg 0% 0% / 0.15);

    
    .github{
        display: inline-flex;
        justify-content: center;
        align-items: center;
        gap: var(--size-2);

    }
    a{
        text-decoration: underline;
        text-underline-offset: 0.25em;
    }
}

@media (width > 768px) {
    footer{
        flex-direction: row;
        justify-content: space-evenly;
    }
}
</style>