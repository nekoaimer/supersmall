<template>
  <div>
    <div class="nav-bar">
      <div class="navbar-left">
        <slot name="navbar-left"></slot>
      </div>
      <div class="navbar-center">
        <slot name="navbar-center"></slot>
      </div>
      <div class="navbar-right">
        <slot name="navbar-right"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NavBar"
}
</script>

<style scoped>
.nav-bar {
  display: flex;
  height: 44px;
  line-height: 44px;
  text-align: center;
  box-shadow:  0 1px 0.5px rgba(80,80,80,.2);
}

.navbar-left, .navbar-right {
  width: 60px;
}

.navbar-center {
  flex: 1;
}
</style>
