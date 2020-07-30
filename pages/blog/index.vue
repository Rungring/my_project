<template>
<v-row justify="center" align="center">
  <v-col cols="12" xl="12">
    <Card  
      v-for="(post, index) in posts"
      :key="`Card${index}`"
      :title="post.title"
      :description="post.description"
      :img="post.img"
      :index="index"
      :slug="post.slug"
      class="mt-4" />
  </v-col>
</v-row>
</template>

<script>
import { useAsync, defineComponent, ref } from 'nuxt-composition-api'
import Card from '~/components/Card.vue'

export default defineComponent({
  head: () => ({
    title: 'Blog',
  }),
  components: {
    Card
  },
  setup(_props, context) {

   const posts = useAsync(async () => await context.root.$content('posts').fetch());
   
    return { 
     posts,
    }
  },
});
</script>
