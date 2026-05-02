<template>
  <div class="container-xl py-5">
    <!-- DELETE MODAL -->
    <DeleteEmployee
      :show="showDeleteModal"
      @confirm="executeDelete"
      @cancel="closeDeleteModal"
    />

    <div class="mb-5 text-center">
      <span class="badge bg-primary px-3 py-2 rounded-pill mb-3 shadow-sm">Admin Dashboard</span>
      <h1 class="display-5 fw-bold text-dark mb-2">
        <i class="bi bi-people-fill text-primary"></i> Employee Management
      </h1>
      <p class="text-muted lead">Streamline your workforce operations with ease</p>
    </div>



    <div class="row g-4">
      <div class="col-lg-4">
        <!-- Swapping between Add and Update components -->
        <UpdateEmployee
          v-if="isEditing"
          :employee="currentEmployee"
          @update="handleUpdate"
          @cancel="resetForm"
        />
        <AddEmployee
          v-else
          @add="handleAdd"
        />
      </div>

      <div class="col-lg-8">
        <EmployeeList
          :employees="employees"
          :loading="loading"
          @edit="handleEdit"
          @delete="confirmDelete"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import AddEmployee from "./AddEmployee.vue";
import UpdateEmployee from "./UpdateEmployee.vue";
import DeleteEmployee from "./DeleteEmployee.vue";
import EmployeeList from "./EmployeeList.vue";

export default {
  name: "EmployeeManagement",
  components: {
    AddEmployee,
    UpdateEmployee,
    DeleteEmployee,
    EmployeeList
  },
  data() {
    return {
      apiUrl: "https://69e856172f51b534be5fead9.mockapi.io/api/employees",
      employees: [],
      loading: false,
      isEditing: false,
      editId: null,
      currentEmployee: null,
      showDeleteModal: false,
      deleteId: null
    };
  },
  mounted() {
    this.fetchEmployees();
  },
  methods: {
    async fetchEmployees() {
      this.loading = true;
      try {
        const response = await axios.get(this.apiUrl);
        this.employees = response.data;
      } catch (error) {
        console.error("Error fetching employees:", error);
      }
      this.loading = false;
    },

    async handleAdd(formData) {
      try {
        await axios.post(this.apiUrl, formData);
        this.fetchEmployees();
      } catch (error) {
        console.error("Error adding employee:", error);
      }
    },

    async handleUpdate(formData) {
      try {
        await axios.put(`${this.apiUrl}/${this.editId}`, formData);
        this.resetForm();
        this.fetchEmployees();
      } catch (error) {
        console.error("Error updating employee:", error);
      }
    },

    handleEdit(emp) {
      this.isEditing = true;
      this.editId = emp.id;
      this.currentEmployee = { ...emp };
      window.scrollTo({ top: 0, behavior: "smooth" });
    },

    confirmDelete(id) {
      this.deleteId = id;
      this.showDeleteModal = true;
    },

    async executeDelete() {
      try {
        await axios.delete(`${this.apiUrl}/${this.deleteId}`);
        this.closeDeleteModal();
        this.fetchEmployees();
      } catch (error) {
        console.error("Error deleting employee:", error);
      }
    },

    closeDeleteModal() {
      this.showDeleteModal = false;
      this.deleteId = null;
    },

    resetForm() {
      this.isEditing = false;
      this.editId = null;
      this.currentEmployee = null;
    }
  }
};
</script>

<style scoped>
/* Scoped styles removed in favor of global app.css and standard Bootstrap utilities */
</style>
