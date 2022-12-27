<template>
  <div>
    <HeaderNotification />
    <div class="container">
      <TheHeader />
      <TheMenu />
      <Product />
    </div>
  </div>
</template>

<style lang="scss">
@import "assets/styles/main.scss";

body {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: Onest, sans-serif;
  background: #e0ffaf;
}

.container {
 max-width: 1296px;
  margin: 0 auto;
}
</style>