<template>
  <!-- begin::Page loader -->
  <div class="loader">
    <img alt="Logo" :src="logo" />
    <div
      class="spinner"
      v-bind:class="spinnerClass || 'spinner-brand'"
    ></div>
  </div>
  <!-- end::Page Loader -->
</template>

<script>
export default {
  name: "Loader",
  props: {
    logo: String,
    spinnerClass: String,
  },
};
</script>
