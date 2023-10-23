<template>
  <div class="container">
    <nav>
      <router-link to="/">Главная</router-link>
      <router-link to="/chat">Чат</router-link>
      <router-link to="/test">Тест API</router-link>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'NavComp'
}

</script>

<style scoped>
.container {
  height: 50px;
  display: flex;
  justify-content: center;
}

nav {
  width: 400px;
  height: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
  font-weight: 700;
  font-size: 20px;
  margin-top: 30px;
}

a {
  text-decoration: none;
  color: #ccc;
}
</style>