<template>
  <div id="app-wrapper">
    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark shadow-sm sticky-top py-3">
      <div class="container-xl">
        <a class="navbar-brand fw-bold text-white fs-4" href="#">
          <i class="bi bi-building me-1 text-primary"></i> EmpManager
        </a>
        <button class="navbar-toggler border-0" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ms-auto">
            <li class="nav-item"><a class="nav-link text-white fw-medium fs-5 px-3" href="#home">Home</a></li>
            <li class="nav-item"><a class="nav-link text-white fw-medium fs-5 px-3" href="#about">About</a></li>
            <li class="nav-item"><a class="nav-link text-white fw-medium fs-5 px-3" href="#how-it-works">How It Works</a></li>
            <li class="nav-item"><a class="nav-link text-white fw-medium fs-5 px-3" href="#tech-stack">Tech Stack</a></li>
          </ul>
        </div>
      </div>
    </nav>

    <!-- Main Content -->
    <main data-bs-spy="scroll" data-bs-target="#navbarNav" tabindex="0">
      
      <!-- Home Section -->
      <section id="home">
        <EmployeeMangement />
      </section>

      <!-- About Section -->
      <section id="about" class="container-xl py-5">
        <div class="mb-4 text-center">
          <h2 class="fw-bold text-dark mb-1">About</h2>
          <div class="mx-auto bg-primary rounded" style="width: 40px; height: 3px;"></div>
        </div>
        <div class="card border-0 shadow-sm rounded-3">
          <div class="card-body p-5 text-center">
            <i class="bi bi-info-circle display-4 text-primary mb-3 d-block opacity-75"></i>
            <p class="lead text-muted mb-0" style="max-width: 800px; margin: 0 auto;">
              The Employee Management System is a modern, lightweight application designed to simplify workforce administration. 
              By providing an intuitive interface to maintain accurate staff records, it ensures your business operations run smoothly and efficiently.
            </p>
          </div>
        </div>
      </section>

      <!-- How It Works Section -->
      <section id="how-it-works" class="container-xl py-5">
        <div class="mb-4 text-center">
          <h2 class="fw-bold text-dark mb-1">How It Works</h2>
          <div class="mx-auto bg-primary rounded" style="width: 40px; height: 3px;"></div>
        </div>
        <div class="row g-4">
          <div class="col-md-3 col-sm-6">
            <div class="card h-100 bg-white border border-success shadow-sm rounded-3">
              <div class="card-body text-center p-4">
                <i class="bi bi-plus-circle display-5 text-success mb-3 d-block"></i>
                <h5 class="fw-bold text-success">Create</h5>
                <p class="small text-muted mb-0">Add new employee records quickly via the intuitive form.</p>
              </div>
            </div>
          </div>
          <div class="col-md-3 col-sm-6">
            <div class="card h-100 bg-white border border-info shadow-sm rounded-3">
              <div class="card-body text-center p-4">
                <i class="bi bi-list-ul display-5 text-info mb-3 d-block"></i>
                <h5 class="fw-bold text-info">Read</h5>
                <p class="small text-muted mb-0">View the complete employee directory in a clean table format.</p>
              </div>
            </div>
          </div>
          <div class="col-md-3 col-sm-6">
            <div class="card h-100 bg-white border border-warning shadow-sm rounded-3">
              <div class="card-body text-center p-4">
                <i class="bi bi-pencil-square display-5 text-warning mb-3 d-block"></i>
                <h5 class="fw-bold text-warning">Update</h5>
                <p class="small text-muted mb-0">Edit details anytime to keep your staff information current.</p>
              </div>
            </div>
          </div>
          <div class="col-md-3 col-sm-6">
            <div class="card h-100 bg-white border border-danger shadow-sm rounded-3">
              <div class="card-body text-center p-4">
                <i class="bi bi-trash display-5 text-danger mb-3 d-block"></i>
                <h5 class="fw-bold text-danger">Delete</h5>
                <p class="small text-muted mb-0">Safely remove outdated or incorrect employee records.</p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Tech Stack Section -->
      <section id="tech-stack" class="container-xl py-5 mb-5">
        <div class="mb-4 text-center">
          <h2 class="fw-bold text-dark mb-1">Tech Stack</h2>
          <div class="mx-auto bg-primary rounded" style="width: 40px; height: 3px;"></div>
        </div>
        <div class="card border-0 shadow-sm rounded-3">
          <div class="card-body p-5 text-center">
            <div class="d-flex flex-wrap justify-content-center gap-3">
              <span class="badge bg-light text-dark border p-3 fs-6 rounded-pill shadow-sm"><i class="bi bi-braces text-success me-2"></i>Vue.js 3</span>
              <span class="badge bg-light text-dark border p-3 fs-6 rounded-pill shadow-sm"><i class="bi bi-bootstrap-fill text-primary me-2"></i>Bootstrap 5</span>
              <span class="badge bg-light text-dark border p-3 fs-6 rounded-pill shadow-sm"><i class="bi bi-filetype-js text-warning me-2"></i>JavaScript</span>
              <span class="badge bg-light text-dark border p-3 fs-6 rounded-pill shadow-sm"><i class="bi bi-filetype-html text-danger me-2"></i>HTML5</span>
              <span class="badge bg-light text-dark border p-3 fs-6 rounded-pill shadow-sm"><i class="bi bi-filetype-css text-info me-2"></i>CSS3</span>
            </div>
          </div>
        </div>
      </section>

    </main>
  </div>
</template>

<script>
import EmployeeMangement from "./components/EmployeeMangement.vue";

export default {
  name: "App",
  components: {
    EmployeeMangement,
  },
};
</script>

<style></style>
