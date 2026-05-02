<template>
  <div v-if="show" class="modal-overlay">
    <div class="delete-modal card border-0 shadow-lg">
      <div class="card-body p-4 text-center">
        <div class="warning-icon mb-3">⚠️</div>
        <h5 class="fw-bold text-slate-900 mb-2">Delete Employee?</h5>
        <p class="text-slate-500 small mb-4">
          Are you sure you want to remove this record? This action cannot be undone.
        </p>
        <div class="d-flex gap-2 justify-content-center">
          <button class="btn btn-light px-4 fw-medium text-slate-600" @click="$emit('cancel')">
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
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(15, 23, 42, 0.4);
  backdrop-filter: blur(4px);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.delete-modal {
  width: 90%;
  max-width: 400px;
  background: white;
  border-radius: 16px;
  animation: modal-pop 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
}

@keyframes modal-pop {
  0% { transform: scale(0.9); opacity: 0; }
  100% { transform: scale(1); opacity: 1; }
}

.warning-icon {
  font-size: 2.5rem;
}

.text-slate-900 { color: #0f172a; }
.text-slate-600 { color: #475569; }
.text-slate-500 { color: #64748b; }

.btn-light {
  background-color: #f1f5f9;
  border: none;
  border-radius: 8px;
}

.btn-danger {
  background-color: #ef4444;
  border: none;
  border-radius: 8px;
}

.btn-danger:hover {
  background-color: #dc2626;
  box-shadow: 0 4px 6px -1px rgba(220, 38, 38, 0.2);
}
</style>
