<template>
  <div>
    <div class="section-container">
      <div class="card-container">
        <div class="card-input card-name">
          {{ formData.firstName }} {{ formData.lastName }}
        </div>
        <div class="card-input academic-year">
          {{ formData.academicYear }}
        </div>
        <div class="card-input department-name">
          Dept of {{ formData.department }}
        </div>  
      </div>
    </div>
    <div class="circleBase circle2" style="cursor: pointer;" width="120px">
      <img :src="image" class="circleBase circle1" width="120px" />
    </div>
  </div>
</template>
<script>
export default {
  name: "GeneratedIDCard",
  components: {},
  data() {
    return {};
  },

  props: {
    formData: Object,
    image: String,
  },
};
</script>
