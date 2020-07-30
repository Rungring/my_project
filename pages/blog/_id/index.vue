<template>
<v-row justify="center" align="center">
  <v-col cols="12" xl="12">
    <Blog :slug="slug" />
  </v-col>
</v-row>
</template>

<script>
import Blog from '~/components/Blog.vue'
import { defineComponent, ref } from 'nuxt-composition-api';

export default defineComponent({
  components: {
    Blog
  },
  setup(_props, context) {
    const slug = ref(context.root.$route.params.id);
 
    return {
     slug,
    }
  },
});
</script>
