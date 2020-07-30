<template>
  <v-card
    max-width="1000"
    class="mx-auto"
    outlined 
    tile
    @click="openBlog"
  >
  <v-row>
    <v-col cols="6" class="pa-0">
      <v-img
      :src="img"
      height="250"
    ></v-img>
    </v-col>
    <v-col cols="6">
      <v-card-text class="headline">
      {{ title }}
    </v-card-text>
    <v-divider class="mx-4"></v-divider>

    <v-card-text class="subtitle-1">
      {{ description }}
    </v-card-text>
    </v-col>
  </v-row>
  </v-card>
</template>

<script>
import { defineComponent } from 'nuxt-composition-api';
export default defineComponent({
  props: {
    title: {
      type: String,
      default: '',
    },
    description: {
      type: String,
      default: '',
    },
    index: {
      type: Number,
      default: 0,
    },
    img: {
      type: String,
      default: '',
    },
    slug: {
      type: String,
      default: '',
    },
  },
  setup(props, context) {
    const openBlog = () => {
      context.root.$router.push({ path: `/blog/${props.slug}` });
    };

    return {
      openBlog
    }
  },
})
</script>