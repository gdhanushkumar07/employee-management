<template>
  <div v-if="show" class="modal-overlay">
    <div class="card border-0 shadow-lg" style="width: 90%; max-width: 400px; border-radius: 1rem;">
      <div class="card-body p-4 text-center">

        <h5 class="fw-bold text-dark mb-2">Delete Employee?</h5>
        <p class="text-muted small mb-4">
          Are you sure you want to remove this record? This action cannot be undone.
        </p>
        <div class="d-flex gap-2 justify-content-center">
          <button class="btn btn-light px-4 fw-medium text-secondary" @click="$emit('cancel')">
            Cancel
          </button>
          <button class="btn btn-danger px-4 fw-medium" @click="$emit('confirm')">
            Delete
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DeleteEmployee",
  props: {
    show: Boolean
  }
};
</script>

<style scoped>
/* Modal overlay using classes previously defined in app.css */
</style>
