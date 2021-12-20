<template>
  <div>
   <div v-for="recipe in recipes" :key="recipe.id">
     <nuxt-link
     :to="{
       name:'category-recipe',
       params:{category:$route.params.category, recipe:recipe.id}
     }"
     >{{recipe.name}}</nuxt-link>
   </div>
   <v-divider></v-divider>
   <nuxt-link to="/">Volver</nuxt-link>
  </div>
</template>

<script>


export default {
  data() {
    return {
    
    };
  },
  async asyncData({app, route}){
    const slug = route.params.category
    const client = app.apolloProvider.defaultClient
    const query = {
      query:require("../../graphql/recipes.gql"),
      variables:{slug}
    }
    let recipes = []
    await client.query(query).then(data => {
      recipes = data.data.recipes
    }).catch(e => console.log(e))

    return { recipes }
  }
};
</script>