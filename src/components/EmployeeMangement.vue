<template>
  <div>
    <!-- DELETE MODAL -->
    <DeleteEmployee
      :show="showDeleteModal"
      :apiUrl="apiUrl"
      :employeeId="deleteId"
      @employee-deleted="onEmployeeDeleted"
      @cancel="closeDeleteModal"
    />

    <div class="row g-4">
      <div class="col-lg-4">
        <!-- Swapping between Add and Update components -->
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
      apiUrl: "https://69e856172f51b534be5fead9.mockapi.io/api/employees",
      isEditing: false,
      editId: null,
      currentEmployee: null,
      showDeleteModal: false,
      deleteId: null,
    };
  },
  methods: {
    refreshList() {
      if (this.$refs.employeeList) {
        this.$refs.employeeList.fetchEmployees();
      }
    },

    onEmployeeUpdated() {
      this.resetForm();
      this.refreshList();
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

    onEmployeeDeleted() {
      this.closeDeleteModal();
      this.refreshList();
    },

    closeDeleteModal() {
      this.showDeleteModal = false;
      this.deleteId = null;
    },

    resetForm() {
      this.isEditing = false;
      this.editId = null;
      this.currentEmployee = null;
    },
  },
};
</script>

<style scoped></style>
