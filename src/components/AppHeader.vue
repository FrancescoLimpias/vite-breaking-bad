<script>

export default {
  props: {
    title: String,
  }
}

</script>

<template>
  <h1>
    {{ title }}
  </h1>
</template>

<style lang="scss" scoped>
h1 {
  padding: .5rem;
  color: white;
}
</style>
