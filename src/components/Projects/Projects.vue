<script >
import { ref } from 'vue'
import Project from './Project.vue'
import ProjectDetails from "./ProjectDetails.vue"


export default {
    setup() {

        let currentProject = ref(null)
        let currentMax = ref(6)

        return { currentProject, currentMax }
    },
    data() {
        return {
            maxBatch: 6,
            projectsData: [],
        };
    },
    methods: {
        getProjects() {
            fetch("/projects.json").then(response => {
                return response.json();
            }).then(data => {
                this.projectsData = data.projects;
                for (let projectIndex in this.projectsData) {

                    this.projectsData[projectIndex].id = projectIndex
                }
            }).catch((error) => {
                alert("Error Occured! Kindly reload the page");
            });
        },
        openProjectDetails(projectIndex) {
            this.currentProject = projectIndex
            setTimeout(() => {
                const projectDetailsEl = document.querySelector(".projectDetails")
                projectDetailsEl.animate(
                    [
                        { scale: 0 }, { scale: 1 }
                    ],
                    { duration: 350, fill: "forwards", easing: "ease" }
                )

                document.body.style.overflowY = "hidden"
            })


        },
        closeProjectDetails(projectDetailsEl) {
            console.log(projectDetailsEl.classList)
            projectDetailsEl.animate(
                [
                    { scale: 1 }, { scale: 0 }
                ],
                { duration: 350, fill: "forwards", easing: "ease" }
            )
            setTimeout(() => {
                this.currentProject = null
                document.body.style.overflowY = "auto"

            }, 350)
        },
        readMoreProjects() {
            setTimeout(()=>{
                this.currentMax += this.maxBatch

            },200)
        }
    },
    mounted() {
        this.getProjects();

        document.body.addEventListener("keydown", (event) => {
            if (event.key === "Escape") {
                const projectDetails = document.querySelector(".projectDetails")
                if (projectDetails) {
                    this.closeProjectDetails(projectDetails)
                }
            }

        })

    },
    components: { Project, ProjectDetails },

}


</script>


<template>
    <section class="projects">
        <div class="container container--large">
            <div class="wrapper">
                <h1 class="projects__heading">All Frontend Mentor Projects</h1>
                <p class="projects__count">Current Count : <span>
                        {{ projectsData.length }}
                    </span></p>
                <ul class="projects__list">
                    <Project class="project__item"
                        v-for="( proj, index ) in projectsData.slice(0, Math.min(currentMax, projectsData.length))"
                        :imgLink="proj.img" :title="proj.title" :jsReq="proj.jsReq" :diff="proj.diff"
                        :projectOpen="() => openProjectDetails(index)"></Project>
                </ul>
            </div>
        </div>
        <button type="button" class="projects__readMore" v-if="currentMax < projectsData.length"
            @click="readMoreProjects()">Read More</button>
        <ProjectDetails v-if="currentProject != null" :project="projectsData[currentProject]"
            :closeProjectDetails="closeProjectDetails"></ProjectDetails>
    </section>
</template>


<style lang="scss" >
.projects {


    .wrapper {
        margin-block: var(--size-12);
    }

    &__heading {
        font-size: var(--size-6);
        text-align: center;
        margin-block: var(--size-8);
    }

    &__count {
        text-align: center;
        font-size: var(--size-5);
        font-weight: 500;

        span {
            font-weight: 700;
            text-decoration: underline var(--underline-color) wavy;
            text-decoration-thickness: 1px;
            text-underline-offset: 0.25ch;
        }
    }

    &__list {
        list-style: none;
        padding-left: 0;

        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(min(400px, 80vw), 1fr));
        gap: var(--size-12);

        margin-block: var(--size-12);
    }

    &__readMore {
        display: block;
        position: relative;
        margin-inline: auto;
        margin-block: -1rem var(--size-12);
        font-size: var(--size-5);
        // padding:  0;

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
            transform: scaleX(1);
            transition: transform ease 350ms;

        }

        &:hover::after {
            transform: scaleX(0);
        }
    }
}

@media (width > 768px) {
    .projects {
        &__heading {
            font-size: var(--size-8);
        }
    }
}
</style>



