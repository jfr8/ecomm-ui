<template>
  <div class="container">
    <div class="row">
      <div class="col-12 text-center">
        <h3 class="pt-3">Add Category</h3>
      </div>
    </div>
    <div class="row">
      <div class="col-3"></div>
      <div class="col-6">
        <form>
          <div class="form-group">
            <label>Name</label>
            <input type="text" class="form-control" v-model="categoryName" />
          </div>
          <div class="form-group">
            <label>Description</label>
            <textarea
              type="text"
              class="form-control"
              v-model="categoryDescription"
            />
          </div>
          <div class="form-group">
            <label>Image</label>
            <input type="text" class="form-control" v-model="imageURL" />
          </div>
          <button type="button" class="btn btn-primary" @click="addCategory">
            Add Category
          </button>
        </form>
      </div>
      <div class="col-3"></div>
    </div>
  </div>
</template>

<script>
const axios = require("axios");
const sweetalert = require("sweetalert");

export default {
  data() {
    return {
      categoryName: "",
      categoryDescription: "",
      imageURL: "",
    };
  },

  methods: {
    addCategory() {
      console.log(this.categoryName, this.categoryDescription);

      const newCategory = {
        categoryName: this.categoryName,
        categoryDescription: this.categoryDescription,
        imageURL: this.imageURL,
      };

      const baseURL = "https://limitless-lake-55070.herokuapp.com";

      axios({
        method: "post",
        url: `${baseURL}/category/create`,
        data: JSON.stringify(newCategory),
        headers: {
          "Content-type": "application/json",
        },
      }).then((response) => {
        console.log(response.data.data);

        sweetalert({
          text: 'Category added sucessfully',
          icon: 'success',
        })
      }).catch((error) => {
        console.log(error);
      });
    },
  },
};
</script>


