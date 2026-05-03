<template>
  <div id="app-wrapper" class="pb-5">
    <!-- Dark Header Band -->
    <header class="bg-dark text-white py-4 shadow-sm mb-4">
      <div class="container-xl text-center">
        <h1 class="fw-bold mb-0">
          <i class="bi bi-people-fill text-primary me-2"></i>Employee Management
        </h1>
      </div>
    </header>

    <div class="container-xl">
      <!-- Description Card: Explains the project's purpose -->
      <div class="card border-0 shadow-sm rounded-3 mb-4">
        <div class="card-body p-4 text-center">
          <p
            class="text-muted lead mb-0"
            style="max-width: 1000px; margin: 0 auto"
          >
            This project demonstrates CRUD operations in Vue 3 using standard
            form inputs and dynamic table rendering. Employee records are
            fetched asynchronously from a mock API using Axios and managed
            securely within local component state. The user interface updates
            live to reflect state changes—such as adding or removing a
            record—without requiring page reloads.
          </p>
        </div>
      </div>

      <!-- Main Content: Where the CRUD components are rendered -->
      <main>
        <EmployeeMangement />
      </main>
    </div>
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
