<template>
  <div class="page">
    <Header @toggleForm="toggleForm" @toggleNav="toggleNav" />
    <Nav v-if="showNav" @toggleForm="toggleForm" @toggleNav="toggleNav" />
    <div class="content">
      <Slider @toggleForm="toggleForm" />
      <Calculator @toggleForm="toggleForm" />
    </div>
    <Form v-if="showForm" @toggleForm="toggleForm" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      showForm: false,
      showNav: false,
    };
  },
  methods: {
    toggleForm() {
      if (this.showNav) this.showNav = false;
      this.showForm = !this.showForm;
    },
    toggleNav() {
      this.showNav = !this.showNav;
    },
  },
};
</script>

<style>
.page {
  position: relative;
}
.content {
  max-width: 1440px;
  margin: 0 auto;
}

@media (max-width: 1439px) {
  .content {
    max-width: 975px;
  }
}
@media (max-width: 1023px) {
  .content {
    max-width: 696px;
  }
}
</style>
