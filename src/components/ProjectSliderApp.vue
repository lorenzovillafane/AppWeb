<template>
  <header>
    <div id="logoHeader">
      <img src="../assets/logolv2.png" alt="logo" />
    </div>
    <div id="socialHeader">
      <a href="https://www.linkedin.com/in/lorenzo-villafane" target="_blank"
        ><img src="../assets/icons8-linkedin-64.png" alt="linkedin"
      /></a>
      <a href="https://walink.co/012810" target="_blank"
        ><img src="../assets/icons8-whatsapp-64.png" alt="wpp"
      /></a>
      <a href="https://www.instagram.com/lorenvillafane/" target="_blank"
        ><img src="../assets/icons8-instagram-64.png" alt="instagram"
      /></a>
      <a href="https://github.com/lorenzovillafane" target="_blank"
        ><img src="../assets/icons8-github-64.png" alt="github"
      /></a>
      <a
        href="https://www.dropbox.com/scl/fo/exigpgsrqw662weid64p9/AOSWVbZizU2TidJE_jwzuWk?rlkey=iwmcq29j6tkkeenwe11d998mk&st=sby6usjs&dl=0"
        target="_blank"
        ><img src="../assets/icons8-cv-64.png" alt="cv"
      /></a>
    </div>
  </header>
  <main>
    <div class="project-list">
      <section
        v-for="(project, index) in projects"
        :key="index"
        class="project-card"
        @click="toggleCard(index)"
        :class="{ expanded: project.expanded }"
      >
        <h2>{{ project.title }}</h2>
        <div v-if="project.expanded" class="project-content">
          <div class="image-wrapper">
            <img :src="project.image" alt="Project Image" class="project-image" />
          </div>
          <div class="text-content">
            <p>{{ project.description }}</p>
            <!-- Enlace para ir al sitio -->
            <a :href="project.siteUrl" target="_blank" class="btn">Ir al sitio</a>
          </div>
        </div>
      </section>
    </div>
  </main>
</template>

<script>
export default {
  name: "ProjectList",
  data() {
    return {
      projects: [
        {
          title: "TaskApp",
          description: "Una app para gestionar tareas diarias, ideal para organizar tu día a día.",
          image: "src/assets/Taskapp.png",
          siteUrl: "https://task-app2-taupe.vercel.app/",
          expanded: false,
        },
        {
          title: "Task-V",
          description: "Un clon de Trello para organizar y gestionar proyectos fácilmente.",
          image: "src/assets/taskV.png",
          siteUrl: "https://task-v-swart.vercel.app/",
          expanded: false,
        },
        {
          title: "Picboard",
          description: "Un muro virtual para colgar fotos y recuerdos especiales.",
          image: "src/assets/picboard.png",
          siteUrl: "https://picboard-chi.vercel.app/",
          expanded: false,
        },
      ],
    };
  },
  methods: {
    toggleCard(index) {
      this.projects = this.projects.map((project, i) => ({
        ...project,
        expanded: i === index ? !project.expanded : false,
      }));
    },
  },
};
</script>

<style scoped>
/* Base Styles */
html{background-color: #F1DEC6;}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  overflow-x: hidden; 
  background-color: #f1dec6; 
}

header {
  background-color: #1746A2; 
  padding: 10px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

#socialHeader img {
  width: 48px;
  margin: 0 5px;
  transition: transform 0.3s ease;
}

#socialHeader img:hover {
  transform: scale(1.1);
}

#logoHeader img {
  width: 150px;
}

.main-title {
  text-align: center;
  font-size: 5rem;
  font-weight: 400;
  color: white; 
  margin: 20px 0;
}

.project-list {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 50px;
  margin-top:100px;
  margin-bottom: 100px;
  padding: 0 20px;
}

.project-card {
  width: 100%;
  max-width: 1200px;
  padding: 20px;
  border-radius: 10px;
  text-align: center;
  background-color: #1746A2; 
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  overflow: hidden;
  color: white;
  cursor: pointer;
}

.project-card h2 {
  font-size: 6rem;
  font-weight: 400;
}

.project-card.expanded {
  transform: scale(1.05);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}

.project-content {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 20px;
}

.image-wrapper {
  flex: 1 1 40%;
}

.project-image {
  width: 100%;
  height: auto;
  border-radius: 10px;
}

.text-content {
  flex: 1 1 50%;
}

.text-content p {
  margin-bottom: 20px;
  font-size: 2.8rem;
}

.btn {
  display: inline-block;
  padding: 10px 20px;
  background-color: #FF8343; 
  color: white;
  text-decoration: none;
  border-radius: 5px;
  font-size: 2rem;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: #ffe156;
}
@media (max-width: 1280px) {

  .project-card.expanded {
  transform: scale(1);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}

}
/* Responsivity */
@media (max-width: 768px) {
  .project-list {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 50px;
  margin-top:60px;
  margin-bottom: 100px;
  padding: 0 20px;
}

  #logoHeader img {
    width: 120px;
  }

  #socialHeader img {
    width: 36px; 
  }

  .main-title {
    font-size: 1.5rem;
  }

  .project-card h2 {
    font-size: 3rem;
  }

  .project-content {
    flex-direction: column;
  }

  .image-wrapper {
    flex: 1 1 100%;
  }

  .text-content {
    flex: 1 1 100%;
  }
  .text-content p {
  margin-bottom: 20px;
  font-size: 1.5rem;
}
}
@media (max-width: 450px) {
  header {
  background-color: #1746A2; 
  padding: 10px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
}
#logoHeader img {
 
margin: 20px;
}

}

</style>
