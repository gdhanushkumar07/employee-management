<template>
  <div class="card border-0 shadow-sm overflow-hidden">
    <div class="card-header bg-primary border-bottom-0 pt-4 px-4 pb-3 d-flex justify-content-between align-items-center rounded-top">
      <h5 class="fw-bold text-white mb-0">Employee Directory</h5>
      <span class="badge bg-light text-primary rounded-pill px-3 py-2 shadow-sm">
        {{ employees.length }} Members
      </span>
    </div>
    <div class="card-body p-0">
      <div v-if="loading" class="text-center py-5">
        <div class="spinner-border text-primary" role="status">
          <span class="visually-hidden">Loading...</span>
        </div>
        <p class="text-muted mt-3 small">Loading records...</p>
      </div>
      <div v-else class="table-responsive">
        <table class="table table-hover align-middle mb-0">
          <thead class="bg-light text-muted">
            <tr>
              <th class="ps-4 fw-semibold text-uppercase" style="font-size: 0.75rem; letter-spacing: 0.05em;">Employee</th>
              <th class="fw-semibold text-uppercase" style="font-size: 0.75rem; letter-spacing: 0.05em;">Role</th>
              <th class="fw-semibold text-uppercase" style="font-size: 0.75rem; letter-spacing: 0.05em;">Dept</th>
              <th class="fw-semibold text-uppercase" style="font-size: 0.75rem; letter-spacing: 0.05em;">Salary</th>
              <th class="text-end pe-4 fw-semibold text-uppercase" style="font-size: 0.75rem; letter-spacing: 0.05em;">Actions</th>
            </tr>
          </thead>
          <tbody>
            <tr v-if="employees.length === 0">
              <td colspan="5" class="text-center py-5">
                <div class="empty-state">

                  <h6 class="text-muted mb-1">No employees found</h6>
                  <p class="text-muted small mb-0">Get started by creating a new record.</p>
                </div>
              </td>
            </tr>
            <tr v-for="emp in employees" :key="emp.id">
              <td class="ps-4 py-3">
                <div class="d-flex align-items-center">
                  <div class="rounded-circle bg-primary text-white d-flex align-items-center justify-content-center me-3" style="width: 36px; height: 36px; font-weight: 600;">
                    {{ emp.name.charAt(0) }}
                  </div>
                  <div class="fw-bold text-dark">{{ emp.name }}</div>
                </div>
              </td>
              <td class="py-3"><span class="text-secondary">{{ emp.designation }}</span></td>
              <td class="py-3"><span class="badge bg-secondary bg-opacity-10 text-secondary border fw-normal">{{ emp.department }}</span></td>
              <td class="py-3"><span class="fw-medium text-dark">₹{{ Number(emp.salary).toLocaleString() }}</span></td>
              <td class="text-end pe-4 py-3">
                <div class="btn-group shadow-sm" role="group">
                  <button
                    class="btn btn-sm btn-warning text-dark border-0"
                    @click="$emit('edit', emp)"
                    title="Edit"
                  >
                    Edit
                  </button>
                  <button
                    class="btn btn-sm btn-danger border-0"
                    @click="$emit('delete', emp.id)"
                    title="Delete"
                  >
                    Delete
                  </button>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "EmployeeList",
  props: {
    employees: Array,
    loading: Boolean
  }
};
</script>

<style scoped>
/* Scoped styles removed in favor of standard Bootstrap */
</style>
