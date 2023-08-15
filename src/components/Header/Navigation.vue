<template>
    <nav class="header__nav">
        <ul class="nav__list">
            <li class="nav__item"><a class="nav__link" href="http://github.com/bene-volent" target="_blank">
                    <Icon class="icon" icon="mdi:github"></Icon>
                    <span class="nav__text">Github</span>
                </a></li>
            <li class="nav__item">
                <a class="nav__link" href="http://linkedin.com/in/raghv-r" target="_blank">
                    <Icon class="icon" icon="mdi:linkedin"></Icon>

                    <span class="nav__text">LinkedIn</span>
                </a>
            </li>
            <li><a href="https://www.frontendmentor.io/profile/bene-volent" target="_blank" class="nav__link nav__portfolio">
                    <p class="sr-only">Bene's Frontend Mentor Profile</p>
                    <img src="../../assets/logo.png" alt="Bene Logo">
                </a>
            </li>
        </ul>
    </nav>
</template>

<script setup>
import { Icon } from "@iconify/vue"
</script>

<style lang="scss">
.icon {
    font-size: var(--size-8);
}

.nav__ {
    &list {
        list-style: none;
        padding-left: 0;
        display: flex;
        gap: var(--size-2);
        align-items: center;
    }

    &link {
        display: flex;
        align-items: center;
        gap: var(--size-1);
        position: relative;
        padding: var(--size-2);

        &::after {
            content: "";
            display: inline-block;
            position: absolute;
            width: 100%;
            height: 2px;

            top: 100%;
            left: 0;
            background-color: var(--underline-color);
            // display;
            transform-origin: center center;
            transform: scaleX(0);
            transition: transform ease 350ms;

        }
        &:focus{
        outline: 1px solid black;

        }

        &:hover::after,&:focus::after {
            transform: scaleX(1);
        }

    }
    &text{
        display: none;
    }

    &portfolio {
        &::after {
            content: none;
        }

        img {
            width: 60px;
            border-radius: 50%;
        }

    }

}

@media (width > 600px) {
    .nav{
        &__text{
            display: block;
        }
    }
}
</style>