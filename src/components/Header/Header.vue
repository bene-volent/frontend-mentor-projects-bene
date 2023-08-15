<template>
    <header class="header">
        <div class="container">
            <div class="wrapper">
                <a href="/" class="header__logo">
                    <img class="header__logo_img" src="../../assets/fm-logo.png" alt="Frontend Mentor">
                    <h2 class="header__logo_title">Frontend Mentor Projects</h2>
                </a>
                <Navigation></Navigation>

            </div>
        </div>

    </header>
</template>

<script setup>
import Navigation from './Navigation.vue';


</script>

<style lang="scss">
.header {
    box-shadow: 0 10px 24px -11px hsl(0deg 0% 0% / 0.15);

    .wrapper {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding-block: var(--size-8);
    }

    &__logo {
        display: flex;
        gap: var(--size-6);

        >*+* {
            flex: 1 0 auto;
        }

        &_img {
            width: var(--size-12);
            aspect-ratio: 1;
            border-radius: 50%;
        }



        &_title {
            display: none;
            font-weight: 400;
        }
        &:focus{
            outline: rgb(104, 190, 205) dotted 3px;
            outline-offset: 4px;
        }

    }
}

@media (width > 600px) {
    .header {
        &__logo_title {
            display: block;
            translate: 0 0.5em;
            font-size: var(--size-4);
        }
    }
}

@media (width > 768px) {
    .header {
        &__logo_title {
            translate: 0 0;

            font-size: var(--size-6);
        }
    }
}
</style>