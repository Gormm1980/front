<template>
    <div>
        {{recipe}}
    </div>
</template>

<script>
export default {
    async asyncData({app, route}){
        const client = app.apolloProvider.defaultClient
        const id = route.params.recipe
        const query = {
            query:require("../../../graphql/recipe.gql"),
            variables:{id}
        }
        let recipe = null
        await client.query(query).then(data => {
            recipe = data.data.recipe
        }).catch(e => console.log(e))

        return {recipe}
    }
}
</script>