<template>
  <div class="menu">
    <ul>
      <li>
        <RouterLink v-for="item in links" key="name" to="/">{{item.name}}</RouterLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TheMenu",
  data() {
    return {
      links: [
        {name: 'Omega-3', link: '/'},
        {name: 'Вітаміни', link: '/'},
        {name: 'Добавки', link: '/'},
        {name: 'Доставка', link: '/'},
        {name: 'Про нас', link: '/'},
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.menu {
  margin-top: 45px;
}
ul {
  display: flex;
  justify-content: center;
  li {
    list-style: none;
    a {
      text-decoration: none;
      color: black;
      &:not(:last-child) {
        margin-right: 20px;
      }
    }
  }
}
</style>