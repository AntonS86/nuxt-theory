<template>
  <section>
    <h1>{{pageTitle}}</h1>
    <ul>
      <li v-for="user of users" :key="user.id">
        <a href="#" @click.prevent="goTo(user)">{{user.name}} <{{user.email}}></a>
      </li>
    </ul>
  </section>
</template>

<script>
  export default {
    /*async asyncData({store, error}) {
      try {
        await store.dispatch('users/fetchUsers');
        return {};
      } catch (e) {
        error(e)
      }
    },*/
    /*async fetch({store, error}) {
      try {
        if (store.getters['users/users'].length === 0) {
          await store.dispatch('users/fetchUsers');
        }

      } catch (e) {
        error(e)
      }
    },*/
    data    : () => ({
      pageTitle: 'Users page',
    }),
    methods : {
      goTo(user) {
        this.$router.push('/users/' + user.id);
      }
    },
    computed: {
      users() {
        return this.$store.getters['users/users'];
      }
    }
  }
</script>
