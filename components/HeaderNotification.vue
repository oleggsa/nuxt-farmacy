<template>
  <div class="notification">
    Безкоштовна доставка від 1800 грн
  </div>
</template>

<script>
export default {
  name: "HeaderNotification"
}
</script>

<style lang="scss" scoped>
.notification {
  display: flex;
  justify-content: center;
  text-align: center;
  background: #99AFFF;
  color: white;
  font-weight: 500;
  font-size: 20px;
  padding: 10px 0;
  &:before {
    content: url("../assets/icons/drugs.svg");
    display: inline-block;
    width: 24px;
    height: 24px;
    margin-right: 13px;
  }
  &:after {
    content: url("../assets/icons/drugs.svg");
    display: inline-block;
    width: 24px;
    height: 24px;
    margin-left: 13px;
  }
}
</style>