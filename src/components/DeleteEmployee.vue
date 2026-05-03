<template>
  <div v-if="show" class="modal-overlay">
    <div
      class="card border-0 shadow-lg"
      style="width: 90%; max-width: 400px; border-radius: 1rem"
    >
      <div class="card-body p-4 text-center">
        <h5 class="fw-bold text-dark mb-2">Delete Employee?</h5>
        <p class="text-muted small mb-4">
          Are you sure you want to remove this record? This action cannot be
          undone.
        </p>
        <div class="d-flex gap-2 justify-content-center">
          <button
            class="btn btn-light px-4 fw-medium text-secondary"
            @click="$emit('cancel')"
          >
            Cancel
          </button>
          <button class="btn btn-danger px-4 fw-medium" @click="handleDelete">
            Delete
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "DeleteEmployee",
  props: {
    show: Boolean,
    apiUrl: {
      type: String,
      required: true,
    },
    employeeId: {
      type: [String, Number],
      default: null,
    },
  },
  methods: {
    async handleDelete() {
      if (!this.employeeId) return;
      try {
        await axios.delete(`${this.apiUrl}/${this.employeeId}`);
        this.$emit("employee-deleted");
      } catch (error) {
        console.error("Error deleting employee:", error);
      }
    },
  },
};
</script>

<style scoped></style>
