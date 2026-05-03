<template>
  <div id="app-wrapper">
    <!-- Navbar -->
    <nav
      class="navbar navbar-expand-lg navbar-dark bg-dark shadow-sm sticky-top py-3"
    >
      <div class="container-xl">
        <a class="navbar-brand fw-bold text-white fs-4" href="#">
          <i class="bi bi-building me-1 text-primary"></i> EmpManager
        </a>
        <button
          class="navbar-toggler border-0"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNav"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ms-auto">
            <li class="nav-item">
              <a class="nav-link text-white fw-medium fs-5 px-3" href="#home"
                >Home</a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link text-white fw-medium fs-5 px-3" href="#about"
                >About</a
              >
            </li>
            <li class="nav-item">
              <a
                class="nav-link text-white fw-medium fs-5 px-3"
                href="#how-it-works"
                >How It Works</a
              >
            </li>
            <li class="nav-item">
              <a
                class="nav-link text-white fw-medium fs-5 px-3"
                href="#tech-stack"
                >Tech Stack</a
              >
            </li>
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
      <section id="about" class="bg-light py-5 border-top">
        <div class="container-xl">
          <div class="mb-4 text-center">
            <h2 class="fw-bold text-dark mb-1">About</h2>
            <div
              class="mx-auto bg-primary rounded"
              style="width: 40px; height: 3px"
            ></div>
          </div>
          <div class="card border-0 shadow-sm rounded-3">
            <div class="card-body p-5 text-center">
              <i
                class="bi bi-info-circle display-4 text-primary mb-3 d-block opacity-75"
              ></i>
              <p
                class="lead text-muted mb-0"
                style="max-width: 800px; margin: 0 auto"
              >
                This project demonstrates CRUD operations in Vue 3 using
                standard form inputs and dynamic table rendering. Employee
                records are fetched asynchronously from a mock API using Axios
                and managed securely within local component state. The user
                interface updates live to reflect state changes—such as adding
                or removing a record—without requiring page reloads.
              </p>
            </div>
          </div>
        </div>
      </section>

      <!-- How It Works Section -->
      <section id="how-it-works" class="bg-white py-5 border-top">
        <div class="container-xl">
          <div class="mb-4 text-center">
            <h2 class="fw-bold text-dark mb-1">How It Works</h2>
            <div
              class="mx-auto bg-primary rounded"
              style="width: 40px; height: 3px"
            ></div>
          </div>
          <div class="row g-4">
            <div class="col-md-3 col-sm-6">
              <div
                class="card h-100 bg-white border border-success shadow-sm rounded-3"
              >
                <div class="card-body text-center p-4">
                  <i
                    class="bi bi-plus-circle display-5 text-success mb-3 d-block"
                  ></i>
                  <h5 class="fw-bold text-success">Create</h5>
                  <p class="small text-muted mb-3">
                    Add records via
                    <code class="text-dark bg-light px-1 rounded"
                      >@click="handleSubmit"</code
                    >
                    syncing inputs with
                    <code class="text-dark bg-light px-1 rounded">v-model</code
                    >.
                  </p>
                  <div class="bg-light p-2 rounded text-start">
                    <code class="small text-success">handleAdd(formData)</code
                    ><br /><code class="small text-muted"
                      >axios.post(url, data)</code
                    >
                  </div>
                </div>
              </div>
            </div>
            <div class="col-md-3 col-sm-6">
              <div
                class="card h-100 bg-white border border-info shadow-sm rounded-3"
              >
                <div class="card-body text-center p-4">
                  <i class="bi bi-list-ul display-5 text-info mb-3 d-block"></i>
                  <h5 class="fw-bold text-info">Read</h5>
                  <p class="small text-muted mb-3">
                    Fetch on
                    <code class="text-dark bg-light px-1 rounded"
                      >mounted()</code
                    >
                    and display iterating with
                    <code class="text-dark bg-light px-1 rounded">v-for</code>.
                  </p>
                  <div class="bg-light p-2 rounded text-start">
                    <code class="small text-info">fetchEmployees()</code
                    ><br /><code class="small text-muted">axios.get(url)</code>
                  </div>
                </div>
              </div>
            </div>
            <div class="col-md-3 col-sm-6">
              <div
                class="card h-100 bg-white border border-warning shadow-sm rounded-3"
              >
                <div class="card-body text-center p-4">
                  <i
                    class="bi bi-pencil-square display-5 text-warning mb-3 d-block"
                  ></i>
                  <h5 class="fw-bold text-warning">Update</h5>
                  <p class="small text-muted mb-3">
                    Load data into form, edit, and apply changes dynamically.
                  </p>
                  <div class="bg-light p-2 rounded text-start">
                    <code class="small text-warning">handleUpdate(data)</code
                    ><br /><code class="small text-muted"
                      >axios.put(url/id, data)</code
                    >
                  </div>
                </div>
              </div>
            </div>
            <div class="col-md-3 col-sm-6">
              <div
                class="card h-100 bg-white border border-danger shadow-sm rounded-3"
              >
                <div class="card-body text-center p-4">
                  <i class="bi bi-trash display-5 text-danger mb-3 d-block"></i>
                  <h5 class="fw-bold text-danger">Delete</h5>
                  <p class="small text-muted mb-3">
                    Trigger modal and remove state record by matching
                    <code class="text-dark bg-light px-1 rounded">id</code>.
                  </p>
                  <div class="bg-light p-2 rounded text-start">
                    <code class="small text-danger">executeDelete()</code
                    ><br /><code class="small text-muted"
                      >axios.delete(url/id)</code
                    >
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Tech Stack Section -->
      <section id="tech-stack" class="bg-light py-5 border-top">
        <div class="container-xl">
          <div class="mb-4 text-center">
            <h2 class="fw-bold text-dark mb-1">Tech Stack</h2>
            <div
              class="mx-auto bg-primary rounded"
              style="width: 40px; height: 3px"
            ></div>
          </div>
          <div class="d-flex flex-wrap justify-content-center gap-3 mt-5">
            <span
              class="badge bg-white text-dark border p-3 fs-6 rounded-pill shadow-sm"
              ><i class="bi bi-braces text-success me-2"></i>Vue.js 3</span
            >
            <span
              class="badge bg-white text-dark border p-3 fs-6 rounded-pill shadow-sm"
              ><i class="bi bi-bootstrap-fill text-primary me-2"></i>Bootstrap
              5</span
            >
            <span
              class="badge bg-white text-dark border p-3 fs-6 rounded-pill shadow-sm"
              ><i class="bi bi-filetype-js text-warning me-2"></i
              >JavaScript</span
            >
            <span
              class="badge bg-white text-dark border p-3 fs-6 rounded-pill shadow-sm"
              ><i class="bi bi-filetype-html text-danger me-2"></i>HTML5</span
            >
            <span
              class="badge bg-white text-dark border p-3 fs-6 rounded-pill shadow-sm"
              ><i class="bi bi-filetype-css text-info me-2"></i>CSS3</span
            >
            <span
              class="badge bg-white text-dark border p-3 fs-6 rounded-pill shadow-sm"
              ><i class="bi bi-server text-secondary me-2"></i>Axios</span
            >
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
