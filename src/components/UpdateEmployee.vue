<template>
  <div class="card border-0 shadow-sm sticky-top" style="top: 2rem">
    <div class="card-header bg-white border-bottom-0 pt-4 px-4 pb-0">
      <h5 class="fw-bold text-dark mb-0">Edit Details</h5>
    </div>
    <div class="card-body p-4">
      <div class="mb-3">
        <label class="form-label small fw-semibold text-muted">Full Name</label>
        <input
          v-model="form.name"
          class="form-control"
          placeholder="e.g. John Doe"
        />
      </div>
      <div class="mb-3">
        <label class="form-label small fw-semibold text-muted">Designation</label>
        <input
          v-model="form.designation"
          class="form-control"
          placeholder="e.g. Software Engineer"
        />
      </div>
      <div class="mb-3">
        <label class="form-label small fw-semibold text-muted">Department</label>
        <input
          v-model="form.department"
          class="form-control"
          placeholder="e.g. Engineering"
        />
      </div>
      <div class="mb-4">
        <label class="form-label small fw-semibold text-muted">Salary (₹)</label>
        <div class="input-group">
          <span class="input-group-text bg-light text-muted">₹</span>
          <input
            v-model.number="form.salary"
            type="number"
            class="form-control"
            placeholder="0.00"
          />
        </div>
      </div>
      
      <div class="d-grid gap-2">
        <button class="btn btn-warning py-2 fw-semibold text-dark" @click="handleSubmit">
          Update Records
        </button>
        <button class="btn btn-outline-secondary py-2 fw-semibold" @click="$emit('cancel')">
          Cancel Edit
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UpdateEmployee",
  props: {
    employee: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      form: { ...this.employee }
    };
  },
  watch: {
    employee: {
      handler(newVal) {
        this.form = { ...newVal };
      },
      deep: true
    }
  },
  methods: {
    handleSubmit() {
      if (!this.form.name || !this.form.designation || !this.form.department || !this.form.salary) {
        alert("Please fill in all fields.");
        return;
      }
      this.$emit("update", { ...this.form });
    }
  }
};
</script>

<style scoped>
.sticky-top { z-index: 10; }
</style>
