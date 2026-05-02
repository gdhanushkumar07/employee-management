<template>
  <div class="card border-0 shadow-sm sticky-top" style="top: 2rem">
    <div class="card-header bg-white border-0 pt-4 px-4 pb-0">
      <h5 class="fw-semibold mb-0">➕ New Employee</h5>
    </div>
    <div class="card-body p-4">
      <div class="mb-3">
        <label class="form-label small fw-medium text-slate-600">Full Name</label>
        <input
          v-model="form.name"
          class="form-control custom-input"
          placeholder="e.g. John Doe"
        />
      </div>
      <div class="mb-3">
        <label class="form-label small fw-medium text-slate-600">Designation</label>
        <input
          v-model="form.designation"
          class="form-control custom-input"
          placeholder="e.g. Software Engineer"
        />
      </div>
      <div class="mb-3">
        <label class="form-label small fw-medium text-slate-600">Department</label>
        <input
          v-model="form.department"
          class="form-control custom-input"
          placeholder="e.g. Engineering"
        />
      </div>
      <div class="mb-4">
        <label class="form-label small fw-medium text-slate-600">Salary (₹)</label>
        <div class="input-group">
          <span class="input-group-text bg-white border-end-0 text-slate-400">₹</span>
          <input
            v-model.number="form.salary"
            type="number"
            class="form-control custom-input border-start-0 ps-0"
            placeholder="0.00"
          />
        </div>
      </div>
      
      <div class="d-grid gap-2">
        <button class="btn btn-indigo py-2 fw-medium" @click="handleSubmit">
          Create Employee
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddEmployee",
  data() {
    return {
      form: {
        name: "",
        designation: "",
        department: "",
        salary: ""
      }
    };
  },
  methods: {
    handleSubmit() {
      if (!this.form.name || !this.form.designation || !this.form.department || !this.form.salary) {
        alert("Please fill in all fields.");
        return;
      }
      this.$emit("add", { ...this.form });
      this.resetForm();
    },
    resetForm() {
      this.form = { name: "", designation: "", department: "", salary: "" };
    }
  }
};
</script>

<style scoped>
.text-slate-600 { color: #475569; }
.text-slate-400 { color: #94a3b8; }
.custom-input {
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  padding: 0.6rem 1rem;
  transition: all 0.2s ease;
  background-color: #fdfdfd;
}
.custom-input:focus {
  border-color: #818cf8;
  box-shadow: 0 0 0 4px rgba(129, 140, 248, 0.1);
  background-color: #fff;
}
.btn-indigo {
  background-color: #4f46e5;
  color: white;
  border: none;
  border-radius: 8px;
  transition: all 0.2s ease;
}
.btn-indigo:hover {
  background-color: #4338ca;
  transform: translateY(-1px);
  box-shadow: 0 4px 6px -1px rgba(79, 70, 229, 0.2);
}
.sticky-top { z-index: 10; }
</style>
