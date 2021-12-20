<template>
  <v-container>
    <v-divider class="my-5"></v-divider>
  
    <!-- <p v-if="$fetchState.pending">Cargando los datos</p>
    <p v-else-if="$fetchState.error">Hay un error</p> -->
    <div>
      <div v-for="categoria in categories" :key="categoria.id">
        <v-btn
          :to="{
            name: 'category',
            params: { category: categoria.slug },
          }"
          class="my-1"
          >{{ categoria.name }}</v-btn
        >
      </div>
    </div>
    <!-- <ApolloQuery :query="query">
      <template slot-scope="{result:{data, loading, error}}">
        <div v-if="loading">Cargando datos...</div>
        <div v-else-if="error">{{error}}</div>
        <div v-else>
          <div v-for="categoria in data.categories" :key="categoria.id">
           <v-btn 
           :to="{
             name:'category', 
             params:{category:categoria.slug},
             query:{id:categoria.id}
             }" class="my-1">{{categoria.name}}</v-btn>
          </div>
        </div>
      </template>
    </ApolloQuery>  -->
  </v-container>
</template>

<script>
//import { categorias } from '../graphql/querys'

export default {
  data() {
    return {
     // categories: [],
      // query: categorias,
    };
  },
  computed:{
    categories(){
      return this.$store.getters.readCategories
    }
  }
  // async fetch() {
  //   //const client = this.$apollo.getClient();
  //   const query = {
  //     query: require("../graphql/categories.gql"),
  //   };

  //   await this.$apollo.query(query).then((data) => {
  //     console.log(data);
  //     this.categories = data.data.categories;
  //   });
  // },
  // async asyncData(context) {
  //   const client = context.app.apolloProvider.defaultClient

  //   const query = {
  //     query:require("../graphql/categories.gql")
  //   }

  //   let categories = []
  //   await client.query(query).then(data => {
  //     console.log(data)
  //     categories = data.data.categories
  //   })

  //   return {categories}
  // },
  // apollo:{
  //   cat:{
  //     query:categorias,
  //     update: data => data.categories
  //   }
  // }
};
</script>
