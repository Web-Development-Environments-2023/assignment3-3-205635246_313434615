
<template>
  <div class="container">
    <h1 class="title">Main Page</h1>
    <Split style="height: 500px;">
    <SplitArea :size="50">
        <RecipePreviewList title="Random Recipes" 
            queryString="http://localhost:3000/recipes/getRandomRecipes" 
             :needAddButton="true"
              class="RandomRecipes center" />
    </SplitArea>
    <SplitArea :size="50">
        <router-link v-if="!$root.store.username" to="/login" tag="button">
        You need to Login to vue this</router-link>
        {{ !$root.store.username }}
        <RecipePreviewList title="Last Viewed Recipes" 
              queryString="http://127.0.0.1:3000/user/profile/getLastViewed"
              :needAddButton="true"
               :class="{
          RandomRecipes: true,
          blur: !$root.store.username,
          center: true
        }"
        disabled>
        </RecipePreviewList>
    </SplitArea>
    </Split>
    
    
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
