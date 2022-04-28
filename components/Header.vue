<template>
  <nav class="navbar navbar-expand-md navbar-light bg-light">
    <div class="container">
      <a class="navbar-brand" href="#">Taskist</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <nuxt-link class="nav-link active" aria-current="page" to="/"
              >Home</nuxt-link
            >
          </li>
          <li class="nav-item">
            <nuxt-link class="nav-link active" aria-current="page" to="/app"
              >Todo</nuxt-link
            >
          </li>
        </ul>
      </div>
      <div class="ml-auto">
        <template
          v-if="isAuthenticated"
        >
        <nuxt-link
            class="navbar-item text-decoration-none text-reset mx-2"
            aria-current="page"
            to="/profile"
            >{{ loggedInUser.username }}</nuxt-link
          >
          <nuxt-link
            class="navbar-item text-decoration-none text-reset mx-2"
            aria-current="page"
            to="/profile"
            >My Profile</nuxt-link
          >
            <a class="navbar-item text-decoration-none text-reset mx-2" @click="logout">Logout</a>
          
        </template>
        <template v-else>
          <nuxt-link
            class="navbar-item text-decoration-none text-reset mh-2"
            aria-current="page"
            to="/register"
            >Register</nuxt-link
          >
          <nuxt-link
            class="navbar-item text-decoration-none text-reset mh-2"
            aria-current="page"
            to="/login"
            >Log In</nuxt-link
          >
        </template>
      </div>
    </div>
  </nav>
</template>
<script>
import { mapGetters } from "vuex";
export default {
  computed: {
    ...mapGetters(["isAuthenticated", "loggedInUser"]),
  },
  methods: {
    async logout() {
      await this.$auth.logout();
    },
  },
};
</script>