<template>
  <div class="index--content">
    <vslider></vslider>
  </div>
</template>

<script>
  import Vslider from '@/components/Vslider'
  export default {
    name: 'index',
    components: {
      Vslider
    }
  }
</script>

<style scoped>
  .index--content {
    display: flex;
    flex-direction: row;
    justify-content: center;
  }
</style>
