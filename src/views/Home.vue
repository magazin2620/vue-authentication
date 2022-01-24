<template>
  <div class="home">
    <h1>Welcome to the App!</h1>
    <template v-if="!loggedIn">
      <div>
        To use the app, you'll need to
        <router-link to="authenticate" @click.native="isNew(false)">
          Login
        </router-link>
        or
        <router-link to="authenticate" @click.native="isNew(true)">
          Register
        </router-link>
      </div>
    </template>
  </div>
</template>

<script>
import { authComputed } from "../vuex/helpers.js";
export default {
  methods: {
    isNew(isNewUser) {
      this.$store.dispatch("isNewUser", !isNewUser);
    },
  },
  computed: {
    ...authComputed,
  },
};
</script>
