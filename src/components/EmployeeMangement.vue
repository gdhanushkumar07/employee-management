<template>
  <div class="employee-dashboard container py-5">
    <!-- DELETE MODAL -->
    <DeleteEmployee
      :show="showDeleteModal"
      @confirm="executeDelete"
      @cancel="closeDeleteModal"
    />

    <div class="dashboard-header mb-5 text-center">
      <h1 class="display-5 fw-bold text-slate-900 mb-2">
        Employee <span class="text-indigo-600">Management</span>
      </h1>
      <p class="text-slate-500">Streamline your workforce operations with ease</p>
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
.employee-dashboard {
  max-width: 1200px;
}
.text-indigo-600 { color: #4f46e5; }
.text-slate-900 { color: #0f172a; }
.text-slate-500 { color: #64748b; }
</style>
