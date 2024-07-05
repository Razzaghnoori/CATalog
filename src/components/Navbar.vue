<template>
  <nav
    :class="`navbar navbar-expand-lg bg-${theme} sticky-top`"
    :data-bs-theme="theme"
  >
    <div class="container container-fluid">
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
        <a class="nav-link active" aria-current="page" href="/">
          <i class="fa-solid fa-cat fs-1"></i>
        </a>
        <ul class="navbar-nav ms-auto mb-2 mb-lg-0 align-items-center">
          <li class="nav-item">
            <a class="nav-link" href="/about">About</a>
          </li>
          <li class="nav-item">
            <a class="btn btn-dark" @click="toggleTheme()">
              <i
                class="fa-solid"
                :class="{
                  'fa-moon': theme === 'light',
                  'fa-sun': theme === 'dark',
                }"
              ></i>
            </a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "navbar-component",
  props: {
    theme: {
      type: String,
      default: "dark",
    },
    toggleTheme: {
      type: Function,
    },
  },
};
</script>

<style lang="scss" scoped>
nav {
  margin-bottom: 4rem;
}
</style>
