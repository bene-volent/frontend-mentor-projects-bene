<template>
    <li>
        <article class="project">


            <picture class="project__picture" @click="projectOpen()"><img class="project__img" loading="lazy" v-bind:src="imgLink" v-bind:alt="title"></picture>
            <div class="project__content">
                <h3 class="project__heading" @click="projectOpen()">{{ title }}</h3>
                <div class="project__props">
                    <span class="project__req">
                        <span class="html">HTML</span>
                        <span class="css">CSS</span>
                        <span v-if="jsReq" class="js">JS</span>
                    </span>
                    <span v-if="diff === 1" class="project__diff" v-bind:data-diff="diff">
                        <span class="diff__number">1</span>
                        <span class="diff__name">Newbie</span>
                    </span>
                    <span v-else-if="diff === 2" class="project__diff" v-bind:data-diff="diff">
                        <span class="diff__number">2</span>
                        <span class="diff__name">Junior</span>
                    </span>
                    <span v-else-if="diff === 3" class="project__diff" v-bind:data-diff="diff">
                        <span class="diff__number">3</span>
                        <span class="diff__name">Intermediate</span>
                    </span>
                    <span v-else-if="diff === 4" class="project__diff" v-bind:data-diff="diff">
                        <span class="diff__number">4</span>
                        <span class="diff__name">Advanced</span>
                    </span>
                    <span v-else-if="diff === 5" class="project__diff" v-bind:data-diff="diff">
                        <span class="diff__number">5</span>
                        <span class="diff__name">Guru</span>
                    </span>
                </div>
                <p class="project__help" @click="projectOpen()">Click on the panel for more details</p>
            </div>
        </article>
    </li>
</template>

<script setup>
const props = defineProps(
    {
        imgLink: {
            type: String,
            required: true,
        },
        title: {
            type: String,
            required: true,
        },
        jsReq: {
            type: Boolean,
            required: true
        },
        diff: {
            type: Number,
            required: true
        },
        projectOpen:{
            type:Function,
            required:true
        }

    }
)


</script>

<style lang="scss" >
.project {
    border-radius: var(--size-4);
    border: 1px solid hsl(0, 0%, 84%);
    overflow: hidden;
    height: 100%;

    display: grid;
    grid-template-rows: auto 1fr;

    cursor: pointer;

    &__picture {
        overflow: hidden;
    }

    &__img {
        object-fit: cover;
        transition: scale 350ms ease;

        &:hover {
            scale: 1.05;
        }
    }

    &__content {
        height: 100%;
        padding: var(--size-4);


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
            height: 2px;

            top: 100%;
            left: 0;
            background-color: var(--underline-color);
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

    &__req {

        font-size: var(--size-4);
        font-weight: 600;

        >*+* {
            margin-left: var(--size-2);
        }
    }

    &__diff {
        --diff-color: black;

        border: 1px solid;
        border-color: var(--diff-color);
        border-radius: var(--size-1);

        // display: flex;
        // align-items: center;

        font-size: var(--size-4);
        font-weight: 600;
        text-transform: uppercase;

        overflow: hidden;

        >* {
            padding: var(--size-2);
        }

        &[data-diff="1"] {
            --diff-color: hsl(189, 50%, 61%);
        }

        &[data-diff="2"] {
            --diff-color:
                hsl(78, 65%, 55%);

        }

        &[data-diff="3"] {
            --diff-color:
                hsl(45, 97%, 48%);

        }

        &[data-diff="4"] {
            --diff-color:
                hsl(29, 90%, 55%);
        }

        &[data-diff="5"] {
            --diff-color:
                hsl(351, 84%, 55%);

        }
    }

    &__help{

        margin-top: var(--size-1);

        opacity: 0.7;
        text-underline-offset: var(--size-1 );
        text-decoration-thickness: 4px;
        &:hover{
            text-decoration: underline;
        }
    }
}

.html {
    color: hsl(189, 50%, 61%);
}

.js {
    color: hsl(335, 53%, 60%);
}

.css {
    color: hsl(227, 45%, 44%);
}

.diff {
    &__number {
        background-color: var(--diff-color);
        color: #fff;
    }

    &__name {
        color: var(--diff-color);

    }
}

@media (width > 600px) {
    .project{
        &__content{
            padding: var(--size-6) var(--size-8);
        }
        &__heading{
            font-size: var(--size-6);
        }
        &__req{
            font-size: var(--size-5);
        }
    }
}
</style>