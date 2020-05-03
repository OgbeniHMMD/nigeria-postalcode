<template>
  <div
    class="d-flex justify-content-center align-items-center min-vh-100 border-primary border-bottom text-center m-0 my-auto"
  >
    <div>
      <logo />
      <h1 class="title">postalcode</h1>
      <h2 class="subtitle">Nigeria&#39;s Postal Code Finder</h2>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          class="btn btn-lg btn-outline-success mr-3"
        >Documentation</a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="btn btn-lg btn-outline-success"
        >GitHub</a>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from "~/components/Logo.vue";

export default {
  components: {
    Logo
  }
};
</script>

<style>
.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
