<template>
  <section class="section is-medium">
    <div class="container has-text-centered">
      <h1 class="title">My Projects</h1>
      <p>
        Algunos de mis proyectos de aprendizaje se pueden encontrar en <a href="https://github.com/vicentbg" target="_blank">GitHub</a>.
      </p>
    </div>
    <ul class="project-list">
      <li v-for="(project, index) in projects" :key="index">
        <div class="project">
            <h1>Descripción: 
              <span v-if="project.description">{{ project.description }}</span>
              <span v-else>Proyecto sin descripción asignada.</span>
            </h1>
            <h2>URL: {{ project.url }}</h2>
            <h3>Lenguaje: {{ project.language }}</h3>
        </div>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  data: () => {
    return {
      projects: []
    }
  },
  created() {
    fetch(`https://api.github.com/users/vicentbg/repos`)
      .then(resp => resp.json())
      .then((data) => {
        this.projects = data;
        });
  }
}
</script>

<style>
  .project-list {
    display: flex;
    flex-flow: wrap;
    list-style: none;
    margin: 0;
    padding: 0;
  }

  .project-list li {
    width: 50%;
    padding: 10px;
  }

  .project {
    padding: 5px;
    border: 1px solid #ddd;
    box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.1);
    border-radius: 5px;
  }

</style>