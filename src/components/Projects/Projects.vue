<script >
import Project from './Project.vue'
import ProjectDetails from "./ProjectDetails.vue"


export default {
    data() {
        return {
            currentProject: null,
            projectsData: []
        };
    },
    methods: {
        getProjects() {
            fetch("/projects.json").then(response => {
                return response.json();
            }).then(data => {
                this.projectsData = data.projects;
                console.log(data.projects);
            }).catch((error) => {
                alert("Error Occured! Kindly reload the page");
            });
        },
        openProjectDetails(projectIndex) {
            this.currentProject = projectIndex
            // projectDetailsEl.animate(
            //     [
            //         { scale: 0 }, { scale: 1 }
            //     ],
            //     { duration: 350, fill: "forwards", easing: "ease" }
            // )
            setTimeout(() => {
                const projectDetailsEl = document.querySelector(".projectDetails")
                projectDetailsEl.animate(
                    [
                        { scale: 0 }, { scale: 1 }
                    ],
                    { duration: 350, fill: "forwards", easing: "ease" }
                )

                document.body.style.overflowY="hidden"
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
                document.body.style.overflowY="auto"

            }, 350)
        }
    },
    mounted() {
        this.getProjects();
    },
    components: { Project, ProjectDetails }
}


</script>


<template>
    <section class="projects">
        <div class="container container--large">
            <div class="wrapper">
                <h1 class="projects__heading">All Frontend Mentor Projects</h1>
                <ul class="projects__list">
                    <Project class="project__item" v-for="( proj, index ) in projectsData" :imgLink="proj.img"
                        :title="proj.title" :jsReq="proj.jsReq" :diff="proj.diff"
                        :projectOpen="() => openProjectDetails(index)"></Project>
                </ul>
            </div>
        </div>
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

    &__list {
        list-style: none;
        padding-left: 0;

        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(min(400px, 80vw), 1fr));
        gap: var(--size-12);

        margin-block: var(--size-12);
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



