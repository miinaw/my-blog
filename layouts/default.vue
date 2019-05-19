<template>
  <div>
    <Header />

    <section class="main-content columns">
      <NavMenu />

      <div class="container column is-10 section">
        <nuxt />
      </div>
    </section>

    <Footer />
  </div>
</template>

<script>
import Header from '~/components/Header.vue'
import Footer from '~/components/Footer.vue'
import NavMenu from '~/components/NavMenu.vue'

export default {
  components: {
    Header,
    Footer,
    NavMenu
  }
}
</script>

<style lang="scss" scoped>
.main-content {
  min-height: 80vh; // for sticky footer
}
</style>
