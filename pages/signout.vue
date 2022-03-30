<template>
  <h1>Привет, это страница выхода</h1>
</template>

<script>
export default {
  async created() {
    await this.$auth.logout()
    this.$router.back(); // после выхода возвращаемся на ту же страницу, что были
  }
}
</script>

<style scoped>

</style>