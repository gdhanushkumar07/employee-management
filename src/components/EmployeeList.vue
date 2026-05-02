<template>
  <div class="card border-0 shadow-sm overflow-hidden">
    <div class="card-header bg-white border-0 pt-4 px-4 pb-2 d-flex justify-content-between align-items-center">
      <h5 class="fw-semibold mb-0">📋 Employee Directory</h5>
      <span class="badge bg-indigo-50 text-indigo-600 px-3 py-2 rounded-pill">
        {{ employees.length }} Members
      </span>
    </div>
    <div class="card-body p-0">
      <div v-if="loading" class="text-center py-5">
        <div class="spinner-loader"></div>
        <p class="text-slate-400 mt-3 small">Loading records...</p>
      </div>
      <div v-else class="table-responsive">
        <table class="table custom-table mb-0">
          <thead>
            <tr>
              <th class="ps-4">Employee</th>
              <th>Role</th>
              <th>Dept</th>
              <th>Salary</th>
              <th class="text-end pe-4">Actions</th>
            </tr>
          </thead>
          <tbody>
            <tr v-if="employees.length === 0">
              <td colspan="5" class="text-center py-5">
                <div class="empty-state">
                  <p class="text-slate-400 mb-0">No records found.</p>
                </div>
              </td>
            </tr>
            <tr v-for="emp in employees" :key="emp.id" class="align-middle">
              <td class="ps-4">
                <div class="d-flex align-items-center">
                  <div class="avatar me-3">{{ emp.name.charAt(0) }}</div>
                  <div class="fw-semibold text-slate-700">{{ emp.name }}</div>
                </div>
              </td>
              <td><span class="text-slate-600">{{ emp.designation }}</span></td>
              <td><span class="badge bg-slate-100 text-slate-600 fw-normal">{{ emp.department }}</span></td>
              <td><span class="fw-medium">₹{{ Number(emp.salary).toLocaleString() }}</span></td>
              <td class="text-end pe-4">
                <div class="action-buttons">
                  <button
                    class="btn btn-icon text-warning me-1"
                    @click="$emit('edit', emp)"
                    title="Edit"
                  >
                    ✏️
                  </button>
                  <button
                    class="btn btn-icon text-danger"
                    @click="$emit('delete', emp.id)"
                    title="Delete"
                  >
                    🗑️
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
.text-indigo-600 { color: #4f46e5; }
.text-slate-700 { color: #334155; }
.text-slate-600 { color: #475569; }
.text-slate-400 { color: #94a3b8; }
.bg-indigo-50 { background-color: #eef2ff; }
.bg-slate-100 { background-color: #f1f5f9; }

/* Custom Table */
.custom-table thead th {
  background-color: #f8fafc;
  color: #64748b;
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  font-weight: 600;
  border-bottom: 1px solid #f1f5f9;
  padding: 1rem;
}

.custom-table tbody tr {
  transition: background-color 0.2s ease;
}

.custom-table tbody tr:hover {
  background-color: #f8fafc;
}

.custom-table td {
  padding: 1.25rem 1rem;
  border-bottom: 1px solid #f1f5f9;
}

/* Avatar */
.avatar {
  width: 36px;
  height: 36px;
  background-color: #818cf8;
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 600;
  font-size: 0.875rem;
}

.btn-icon {
  background: none;
  border: none;
  padding: 0.4rem;
  border-radius: 6px;
  transition: background-color 0.2s;
}

.btn-icon:hover {
  background-color: #f1f5f9;
}

/* Loader */
.spinner-loader {
  width: 40px;
  height: 40px;
  border: 3px solid #f1f5f9;
  border-top: 3px solid #4f46e5;
  border-radius: 50%;
  animation: spin 1s linear infinite;
  margin: 0 auto;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>
