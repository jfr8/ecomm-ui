<template>
  <div class="card w-100 h-100" style>
    <img src="{category.image}" class="card-img-top" alt="..." />
    </div> 
    <div class="card-body">
      <h5 class="card-title">{{ category.categoryName }}</h5>
      <p class="card-text">
        {{  category.categoryDescription }}
      </p>
      <a href="#" class="btn btn-primary">Go somewhere</a>
    </div>
  
</template>

<script>


export default {
  name: "CategoryBox",
  props: ["category"],
  methods: {

  }
};
</script>
