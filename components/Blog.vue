<template>
    <v-card class="pa-8" outlined>
      <v-card-text class="headline pb-0 black--text"> {{posts.title}} </v-card-text>
      <v-card-title>{{posts.description}}</v-card-title>
      
      <v-img
      class="mx-4"
      :src="posts.img"
    ></v-img>

      <nuxt-content class="pa-4" :document="posts" />
      
    </v-card>
</template>

<script>
import { useAsync, defineComponent } from 'nuxt-composition-api'
export default defineComponent({
  props: {
    slug: {
      type: String,
      default: '',
    },
  },
  setup(props, context) {

  const posts = useAsync(async () => await context.root.$content('posts', props.slug).fetch());

  return {
    posts
  }

  },
})
</script>