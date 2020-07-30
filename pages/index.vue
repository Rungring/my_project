<template lang="html">
  <div />
</template>

<script>
import { defineComponent } from 'nuxt-composition-api';

export default defineComponent({
  head: () => ({
    title: 'Index',
  }),

  middleware: 'redirect_to_blog',
});
</script>
