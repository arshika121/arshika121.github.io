<template>
  <div id="app">
    <div class="container d-flex container-box">
      <UserInputElements
        :formData="formData"
        @changeFormData="changeFormData($event)"
        @onFileChange="onFileChange($event)"
      />
      <GeneratedCardComponent :formData="formData" :image="image" />
    </div>
  </div>
</template>

<script>
import UserInputElements from "./components/UserInputElements";
import GeneratedCardComponent from "./components/GeneratedCardComponent";
export default {
  name: "App",
  components: {
    UserInputElements,
    GeneratedCardComponent,
  },
  data() {
    return {
      formData: {
        firstName: "",
        lastName: "",
        department: "",
        academicYear: "",
      },

      image: "",
    };
  },
  methods: {
    changeFormData(keyObject) {
      console.log("Parent Element Value: ", keyObject);
      this.formData = Object.assign({}, this.formData, keyObject);
    },
    onFileChange(images) {
      this.image = images;
    },
  },
};
</script>

<style>
#app {
  font-weight: 500;
}
.form-input {
  min-width: 25em;
  padding: 3%;
  border: 1px solid #c5c0c0;
  border-radius: 6px;
}
.card-input {
  position: relative;
  margin: 20px;
  text-align: center;
}
.card-name {
  top: 50px;
}
.academic-year {
  top: 40px;
}
.department-name {
  top: 70px;
}
.section-container {
  min-width: 550px;
  height: 585px;
  border: 1px solid black;
  box-sizing: border-box;
}
.card-container {
  position: relative;
  max-width: 55%;
  margin: 0px;
  padding: 14%;
  top: 100px;
  left: 110px;
  border: 1px solid black;
}
.circleBase {
  border-radius: 50%;
  position: absolute;
  height: 200px;
  width: 200px;
  border: 1px solid #000;
}

.circle1 {
  background: white;
}
.circle2 {
  left: 835px;
  top: 0px;
  background: white;
}
button {
  position: relative;
  top: 180px;
  width: 200px;
}
</style>
