<template>
  <div class="menu">
    <ul>
      <li v-for="item in links" :key="item.name">
        <RouterLink to={{item.link}}>{{item.name}}</RouterLink>
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
    &:not(:last-child) a {
      margin-right: 20px;
    }
    a {
      text-decoration: none;
      color: black;
    }
  }
}
</style>