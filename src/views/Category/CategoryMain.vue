<template>
    <div class="container">
      <div class="row">
        <div class="col-12 text-center">
          <h3 class="pt-3">Our Categories</h3>
      
        </div>
      </div>
      <div class="row">
        <div v-for="category of categories" :key="category.id" class="col-xl-4 col-md-6 col-12 d-flex">
          <CategoryBox :category="category" />
        </div>
      </div>
    </div>
</template>
  
  <script>
  const axios = require("axios");
  import CategoryBox from '../../components/Category/CategoryBox.vue'
  
  export default {
    name: "CategoryMain",
    components: { CategoryBox},

    data() {
      return {
        baseURL: "https://limitless-lake-55070.herokuapp.com",
        categories: []
      };
    },

    methods: {
      async getCategories() {
        await axios.get(`${this.baseURL}/category/`)
        .then((response) => {
          this.categories = response.data;
        })
        .error((error) => {
          console.log(error)
        })
      }
    },

    mounted() {
      this.getCategories();
    }

  
   
  };
  </script>
  
  
  