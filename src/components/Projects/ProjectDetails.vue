<template>
    <div ref="projectDetails" class="projectDetails">
        <button class="projectDetails__close" type="button" @click="closeProjectDetails(this.$refs.projectDetails)">
            <Icon icon="mdi:close"></Icon>
        </button>
        <div class="projectDetails__container">
            <article class="projectDetails__project">
                <picture class="projectDetails__picture"><img v-bind:src="project.img" v-bind:alt="project.title"></picture>
                <div class="projectDetails__content">
                    <h3 class="projectDetails__heading">{{ project.title }}</h3>
                    <div class="projectDetails__props">
                        <span class="project__req">
                            <span class="html">HTML</span>
                            <span class="css">CSS</span>
                            <span v-if="project.jsReq" class="js">JS</span>
                        </span>
                        <span v-if="project.diff === 1" class="project__diff" v-bind:data-diff="project.diff">
                            <span class="diff__number">1</span>
                            <span class="diff__name">Newbie</span>
                        </span>
                        <span v-else-if="project.diff === 2" class="project__diff" v-bind:data-diff="project.diff">
                            <span class="diff__number">2</span>
                            <span class="diff__name">Junior</span>
                        </span>
                        <span v-else-if="project.diff === 3" class="project__diff" v-bind:data-diff="project.diff">
                            <span class="diff__number">3</span>
                            <span class="diff__name">Intermediate</span>
                        </span>
                        <span v-else-if="project.diff === 4" class="project__diff" v-bind:data-diff="project.diff">
                            <span class="diff__number">4</span>
                            <span class="diff__name">Advanced</span>
                        </span>
                        <span v-else-if="project.diff === 5" class="project__diff" v-bind:data-diff="project.diff">
                            <span class="diff__number">5</span>
                            <span class="diff__name">Guru</span>
                        </span>
                    </div>
                    <p class="projectDetails__desc">{{ project.desc }}</p>
                    <ul class="link__list">
                        <li class="link__item"><a v-bind:href="project.live" class="link__link" target="_blank"
                                v-bind:data-type="live">Live</a></li>
                        <li class="link__item"><a v-bind:href="project.repo" class="link__link" target="_blank"
                                v-bind:data-type="repo">Repo</a></li>
                        <li class="link__item"><a v-bind:href="project.challenge" class="link__link" target="_blank"
                                v-bind:data-type="challenge">Try it</a></li>
                    </ul>
                </div>
            </article>
        </div>
    </div>
</template>

<script >
import { Icon } from "@iconify/vue"


export default {
    methods: {
        getSelf() {
            console.log(this.$refs.projectDetails)
        }
    },
    props: {
        project: {
            type: Object,
            required: true
        },
        closeProjectDetails: {
            type: Function,
            required: true
        }
    },

    components: {
        Icon,
    }
}



</script>

<style lang="scss" >
.projectDetails {
    position: fixed;
    inset: 0;
    overflow: scroll;
    backdrop-filter: blur(4px);
    background-color: rgba(204, 204, 204, 0.113);
    scale: 0;
    display: grid;
    grid-template-rows: auto 1fr;

    isolation: isolate;
    z-index: 10;




    &__close {
        margin: var(--size-4);
        margin-left: auto;
        padding: var(--size-2);
        border-radius: 50%;

        width: fit-content;

        font-size: var(--size-6);

        color: #101010;

        background-color: #fefefe;

        border: 1px solid rgb(175, 175, 175);

        &:focus {
            outline: 1px solid black;
        }
    }

    &__container {
        display: grid;
        place-content: center;

        // margin-top: -4rem;

    }

    &__project {
        display: grid;
        align-content: center;

        border-radius: var(--size-1);
        overflow: hidden;



        width: min(calc(100% - 3rem), 1140px);
        margin-inline: auto;

        background-color: #fff;

        border: 1px solid #ccc;
    }

    &__content {
        padding: var(--size-8) var(--size-5);

        >*+* {
            margin-top: var(--size-4);
        }
    }

    &__heading {
        position: relative;

        font-size: var(--size-5);
        font-weight: 500;

        width: fit-content;

        &::after {
            content: "";
            display: inline-block;
            position: absolute;
            width: 100%;
            height: 3px;

            top: 100%;
            left: 0;
            // background-color: black;
            // display;
            transform-origin: right;
            transform: scaleX(0);
            transition: transform ease 350ms;

        }

        &:hover::after {
            transform: scaleX(1);
            transform-origin: left;
        }
    }

    &__props {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }


}

.link {
    &__list {
        list-style: none;
        padding-left: 0;
        display: flex;
        gap: var(--size-4);
    }

    &__link {
        position: relative;
        padding: var(--size-2);

        &::after {
            content: "";
            display: inline-block;
            position: absolute;
            width: 100%;
            height: 3px;

            top: 100%;
            left: 0;
            background-color: black;
            // display;
            transform-origin: center center;
            transform: scaleX(0);
            transition: transform ease 150ms;

        }

        &:focus {
            outline: 1px solid black;

        }

        &:hover::after,
        &:focus::after {
            transform: scaleX(1);
        }

    }
}

@media (width > 600px) {
    .projectDetails {
        &__close {
            margin: var(--size-8);
            margin-left: auto;
            padding: var(--size-4);
            font-size: var(--size-8);

        }

        &__content {
            padding: var(--size-6) var(--size-8);

            >*+* {
                margin-top: var(--size-6);
            }
        }

        &__heading {
            font-size: var(--size-6);
        }

        &__req {
            font-size: var(--size-5);
        }
    }
}

@media (width > 900px) {

    .projectDetails {

        &__project {
            grid-template-rows: none;
            grid-template-columns: auto 400px;
        }

        &__content {
            margin-block: auto;

            >*+* {
                margin-top: var(--size-8);
            }
        }

    }
}</style>