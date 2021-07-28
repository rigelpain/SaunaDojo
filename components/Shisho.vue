<template>
  <div>
    <Card2 />
    <Card2 />
    <Card2 />
  </div>
</template>

<script>
import Writing from '~/components/Writing.vue'
import Card1 from '~/components/Card1.vue'
import Card2 from '~/components/Card2.vue'

export default {
  data () {
      return {
      }
    },
  computed: {
  },
  components: {
    Writing,
    Card1,
    Card2,
  }
}
</script>
