<template>
  <footer>
    <p>Copyright &copy; "{{yearVal}}" </p>
  </footer>
</template>

<script>
export default {
  name: 'AppFooter',
  computed: {
    yearVal () {
      return new Date().getFullYear()
    }
  }
}
</script>

<style lang="scss">
footer {
    text-align: center;
}
</style>
