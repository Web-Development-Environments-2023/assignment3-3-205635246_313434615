
<template>
  <div class="container">
    <RecipePreviewList title="serch results" 
    queryString="http://127.0.0.1:3000/user/profile/getFavouriteRecipe" 
    isRandom
    :class="{
      RandomRecipes: false,
      blur: !$root.store.username,
      center: true
    }"
    disabled>
    </RecipePreviewList>
    
    
    <!-- <div
      style="position: absolute;top: 70%;left: 50%;transform: translate(-50%, -50%);"
    >
      Centeredasdasdad
    </div>-->
  </div>
</template>

<script>
import RecipePreviewList from "../components/RecipePreviewList";
export default {
  name:"Search Results",
  components: {
    RecipePreviewList
  }
};
</script>

<style lang="scss" scoped>
.RandomRecipes {
  margin: 10px 0 10px;
}
.blur {
  -webkit-filter: blur(5px); /* Safari 6.0 - 9.0 */
  filter: blur(2px);
}
::v-deep .blur .recipe-preview {
  pointer-events: none;
  cursor: default;
}
</style>
