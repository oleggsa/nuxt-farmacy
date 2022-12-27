<template>
  <div class="header">
    <div class="left-btn">
      <img src="../assets/icons/burger-btn.svg" alt="menu">
      <img src="../assets/icons/search.svg" alt="search">
    </div>
    <div class="logo">
      <img src="../assets/icons/logo.svg" alt="logo">
    </div>
    <div class="right-btn">
      <img src="../assets/icons/call.svg" alt="call">
      <img src="../assets/icons/cart.svg" alt="cart">
    </div>
  </div>
</template>

<script>
export default {
  name: "TheHeader"
}
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 33px;
  .left-btn img:first-child,
  .right-btn img:first-child {
    margin-right: 40px;
  }
}
</style>