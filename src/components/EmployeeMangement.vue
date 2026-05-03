<template>
  <div>
    <!-- Delete: Pops up to confirm record removal -->
    <DeleteEmployee
      :show="showDeleteModal"
      :apiUrl="apiUrl"
      :employeeId="deleteId"
      @employee-deleted="onEmployeeDeleted"
      @cancel="closeDeleteModal"
    />

    <div class="row g-4">
      <div class="col-lg-4">
        <!-- Forms: Swaps between Add and Update components -->
        <UpdateEmployee
          v-if="isEditing"
          :employee="currentEmployee"
          :apiUrl="apiUrl"
          @employee-updated="onEmployeeUpdated"
          @cancel="resetForm"
        />

        <AddEmployee v-else :apiUrl="apiUrl" @employee-added="refreshList" />
      </div>

      <div class="col-lg-8">
        <!-- List View: Displays all employee records -->
        <EmployeeList
          ref="employeeList"
          :apiUrl="apiUrl"
          @edit="handleEdit"
          @delete="confirmDelete"
        />
      </div>
    </div>
  </div>
</template>

<script>
// Import all required child components
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
    EmployeeList,
  },

  data() {
    return {
      // MockAPI endpoint for all CRUD operations
      apiUrl: "https://69e856172f51b534be5fead9.mockapi.io/api/employees",

      // Control state for editing and modals
      isEditing: false,
      editId: null,
      currentEmployee: null,
      showDeleteModal: false,
      deleteId: null,
    };
  },

  methods: {
    // Tells the list component to fetch fresh data
    refreshList() {
      if (this.$refs.employeeList) {
        this.$refs.employeeList.fetchEmployees();
      }
    },

    // Runs after an employee is successfully updated
    onEmployeeUpdated() {
      this.resetForm();
      this.refreshList();
    },

    // Prepares the form for editing a specific employee
    handleEdit(emp) {
      this.isEditing = true;
      this.editId = emp.id;
      this.currentEmployee = { ...emp };
      window.scrollTo({ top: 0, behavior: "smooth" });
    },

    // Shows the delete confirmation modal
    confirmDelete(id) {
      this.deleteId = id;
      this.showDeleteModal = true;
    },

    // Runs after an employee is successfully deleted
    onEmployeeDeleted() {
      this.closeDeleteModal();
      this.refreshList();
    },

    // Closes the delete modal and clears selection
    closeDeleteModal() {
      this.showDeleteModal = false;
      this.deleteId = null;
    },

    // Switches back to "Add New Employee" mode
    resetForm() {
      this.isEditing = false;
      this.editId = null;
      this.currentEmployee = null;
    },
  },
};
</script>

<style scoped></style>
