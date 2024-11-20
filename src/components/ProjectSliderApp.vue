<template>
  <header>
    <div id="logoHeader">
      <img src="../assets/logolv2.png" alt="logo">
    </div>
    <div id="socialHeader">
      <a href="https://www.linkedin.com/in/lorenzo-villafane" target="_blank"><img src="../assets/icons8-linkedin-64.png" alt="linkedin"></a>
      <a href="https://walink.co/012810" target="_blank"><img src="../assets/icons8-whatsapp-64.png" alt="wpp"></a>
      <a href="https://www.instagram.com/lorenvillafane/" target="_blank"><img src="../assets/icons8-instagram-64.png" alt="instagram"></a>
      <a href="https://github.com/lorenzovillafane" target="_blank"><img src="../assets/icons8-github-64.png" alt=""></a>
      <a href="https://www.dropbox.com/scl/fo/exigpgsrqw662weid64p9/AOSWVbZizU2TidJE_jwzuWk?rlkey=iwmcq29j6tkkeenwe11d998mk&st=tpi1clac&dl=0" target="_blank"><img src="../assets/icons8-cv-64.png" alt="cv"></a>
    </div>
  </header>
  <div class="project-list">
    <section
      v-for="(project, index) in projects"
      :key="index"
      :style="{ backgroundColor: colors[index % colors.length] }"
      class="project-section"
    >
      <div class="project-content">
        <div class="text-content">
          <h2>{{ project.title }}</h2>
          <p>{{ project.description }}</p>
          <a :href="project.link" target="_blank">Ir al sitio</a>
        </div>
        <img :src="project.image" alt="Project Image" class="project-image" />
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "ProjectList",
  data() {
    return {
      projects: [
        { title: "Task-V", description: "Con esta App puedes gestionar las tareas de tu proyecto. (Clon de Trello)", image: "src/assets/taskV.png", link: "https://task-v-swart.vercel.app/" },
        { title: "TaskApp", description: "Anota tus tareas diarias (To-Do app)", image: "src/assets/Taskapp.png", link: "https://task-app2-taupe.vercel.app/" },
        { title: "PICBOARD", description: "Cuelga tus fotos o imágenes favoritas", image: "src/assets/picboard.png", link: "https://picboard-chi.vercel.app/" },
      ],
      colors: ["#F1DEC6", "#179BAE", "#F1DEC6", "#F3FF33"],
    };
  },
};
</script>

<style scoped>
 header {
  background-color: #179BAE;
  padding: 2px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

#socialHeader img {
  width: 48px;
}

#socialHeader {
  position: absolute;
  top: 5%;
  left: 3%;
}

#logoHeader img {
  width: 150px;
  margin-bottom: 0px;
  padding: 1%;
}

#logoHeader {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.text-content a{
  color: #1B262C;
  text-decoration: none;
  font-size: 25px;

  border-radius: 15px;
  padding: 10px;
  background-color: #FF8343;

}




  
.project-list {
  display: flex;
  flex-direction: column;
  width: 100%;
  justify-content:center;
}

.project-section {
  padding: 0px;
  min-height: 60vh; /* Altura mínima para cada sección */
  display: flex;
  align-items: center;
  justify-content: center;
}

.project-content {
  display: flex;
  flex-direction:row;
  justify-content:space-around;
  align-items: center;
  width: 100%;
  flex-wrap: nowrap;
}
.text-content{width: 30%;}
.text-content h2{
  font-size: 120px;
  font-weight: 400;
  margin:0px;
  color: #1B262C;
}
.text-content p{
  font-size: 30px;
  margin:0%;
  font-weight: 100;
 margin-bottom: 20px;
  color: #1B262C;
}
.project-image {
  flex: 1 1 300px;
  max-width: 900px;
  object-fit: cover;
  border-radius: 8px;
}

/* Responsividad */
@media (max-width: 768px) {
  .project-content {
    flex-direction: column;
    text-align: center;
  }

  .project-image {
    width: 80%;
  }
}
</style>
