<template>
  <section>
    <h1>{{user.name}}</h1>
    <hr>
    <b>{{user.email}}</b>
  </section>
</template>

<script>
  export default {
    async asyncData({params, store, error}) {
      try {
        const user = await store.dispatch('users/fetchUserById', params.id);
        return {user};
      } catch (e) {
        error(e);
      }
    },
    validate({params}) {
      return /^\d+?$/.test(params.id);
    }
  }
</script>

<style scoped>

</style>
