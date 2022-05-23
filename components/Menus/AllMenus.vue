<!-- Template -->
<template>
  <div>
    <div>
      <b-navbar
        toggleable="lg"
        type="light"
        variant="light"
        class="shadow-md"
        fixed="top"
      >
        <b-navbar-brand to="/">NUXT JARCOL</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item to="/master_area">Master Area</b-nav-item>
            <b-nav-item to="/master_cabang">Master Cabang</b-nav-item>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </div>
    <!-- <NuxtLogo /> -->
  </div>
</template>

<!-- Style -->
<style>
body {
  background-color: lightgray;
}
.mt-5 {
  margin-top: 100px !important;
}
</style>

<!-- Script -->
<script>
export default {
  name: 'AllMenus',
}
</script>
