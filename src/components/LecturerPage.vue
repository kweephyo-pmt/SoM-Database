<template>
  <div class="lecturer-page">
    <!-- App Bar -->
    <header class="app-bar">
      <h1>Lecturer Dashboard</h1>
    </header>

    <div class="content-container">
      <!-- Left Section: Menu -->
      <div class="menu">
        <label for="menu-dropdown" class="menu-label">Navigate</label>
        <select id="menu-dropdown" @change="navigateToPage" v-model="selectedOption">
          <option value="kpi">KPI</option>
          <option value="instructor-schedule">Instructor Schedule</option>
          <option value="budget">Budget</option>
          <option value="self-development">Self-Development</option>
        </select>
      </div>

      <!-- Right Section: Profile -->
      <div class="profile">
        <img :src="profilePhoto" alt="Profile Photo" class="profile-photo" />
        <div class="profile-info">
          <h2 class="profile-name">{{ lecturerName }}</h2>
        </div>
      </div>
    </div>

    <!-- Placeholder for Selected Page -->
    <div class="page-content">
      <component :is="currentPage" />
    </div>
  </div>
</template>

<script>
// Import your pages
import KpiPage from './KpiPage.vue';
import InstructorSchedulePage from './InstructorSchedulePage.vue';
import BudgetPage from './BudgetPage.vue';
import SelfDevelopmentPage from './SelfDevelopmentPage.vue';

export default {
  name: 'LecturerPage',
  data() {
    return {
      lecturerName: 'Prof. John Doe',
      profilePhoto: require('@/assets/logo.png'), // Use logo.png from the assets folder
      selectedOption: 'kpi', // Default to KPI
    };
  },
  computed: {
    currentPage() {
      // Map the selected option to the corresponding component
      const pages = {
        kpi: KpiPage,
        'instructor-schedule': InstructorSchedulePage,
        budget: BudgetPage,
        'self-development': SelfDevelopmentPage,
      };
      return pages[this.selectedOption];
    },
  },
  methods: {
    navigateToPage() {
      console.log(`Navigated to: ${this.selectedOption}`);
    },
  },
};
</script>

<style scoped>
/* App Bar */
.app-bar {
  background-color: #034E69 ;
  color: white;
  padding: 10px 20px;
  text-align: center;
  font-size: 24px;
  font-weight: bold;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* Layout */
.lecturer-page {
  display: flex;
  flex-direction: column;
  font-family: Arial, sans-serif;
}

.content-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
  gap: 20px;
}

.menu {
  width: 20%;
}

.menu-label {
  display: block;
  margin-bottom: 8px;
  font-size: 14px;
  font-weight: bold;
}

.menu select {
  width: 100%;
  padding: 8px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.profile {
  display: flex;
  align-items: center;
  gap: 10px;
}

.profile-photo {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid #007bff;
}

.profile-name {
  font-size: 18px;
  font-weight: bold;
  color: #333;
}

/* Page Content */
.page-content {
  margin: 20px;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 4px;
  background-color: #f9f9f9;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
</style>
