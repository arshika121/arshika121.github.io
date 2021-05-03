<template>
  <div class="section-container">
    <form onsubmit="return false" style=" max-width: 25em;">
      <div v-for="item in formInputElements" :key="item.formValueKey">
        <div style="margin: 5px;">
          {{ item.labelName }}
          <input
            class="form-input"
            type="text"
            id="name"
            :value="formData[item.formValueKey]"
            @input="
              changeFormData({ [item.formValueKey]: $event.target.value })
            "
          />
          <i :class="item.iconClass"></i>
        </div>
      </div>
      <div>Upload Profile Picture</div>
      <div v-for="picture in items" :key="picture.image">
        <div v-if="!picture.image">
          <input type="file" @change="onFileChange(picture, $event)" />
        </div>
        <div v-else>
          <img
            :src="picture.image"
            class="circleBase circle1"
            width="120px"
          /><br />
          <button @click="removeImage(picture)">Remove image</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "UserInputElements",
  data() {
    return {
      formInputElements: [
        {
          labelName: "First Name",
          formValueKey: "firstName",
          placeholder: "Enter First Name",
        },
        {
          labelName: "Last Name",
          formValueKey: "lastName",
          placeholder: "Enter Last Name",
        },
        {
          labelName: "Department",
          formValueKey: "department",
          placeholder: "Enter Department",
        },
        {
          labelName: "Academic Year",
          formValueKey: "academicYear",
          placeholder: "Enter Academic Year",
        },
      ],
      items: [
        {
          image: false,
        },
      ],
    };
  },
  props: {
    formData: Object,
  },
  methods: {
    changeFormData(value) {
      console.log("Child element value : ", value);
      this.$emit("changeFormData", value);
    },
    onFileChange(picture, e) {
      var files = e.target.files || e.dataTransfer.files;
      if (!files.length) return;
      this.createImage(picture, files[0]);
    },
    createImage(picture, file) {
      var image = new Image();
      var reader = new FileReader();
      console.log(image);
      reader.onload = (e) => {
        picture.image = e.target.result;
        this.items[0].image = picture.image;
        this.$emit("onFileChange", picture.image);
      };
      reader.readAsDataURL(file);
    },
    removeImage: function(picture) {
      picture.image = false;
    },
  },
};
</script>
