<template lang='pug'>
article
  header
    h1(v-if='error.statusCode === 404')
      | {{ pageNotFound }}
    h1(v-else)
      | {{ otherError }}
  div
    NuxtLink(to='/')
      | Home page
</template>

<script>
export default {
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null
    }
  },
  data () {
    return {
      pageNotFound: '404 Not Found',
      otherError: 'An error occurred'
    }
  },
  head () {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError
    return {
      title
    }
  }
}
</script>
