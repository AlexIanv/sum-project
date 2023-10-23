<template>
  <div class="container">
    <div class="title">Пользователи гитхаба</div>
    <div v-if="isLoad" class="loading">
      Loading data
    </div>
    <div v-else class="data">
      <div v-for="(user, index) in teamData" :key="index">
        {{ index + 1 }}. {{ user.login }}
        <button @click="removeUser(user.id)">𐄂</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TestApi',
  data() {
    return {
      teamData: [],
      isLoad: true,
    };
  },
  mounted() {
    const url = "https://api.github.com/users";
    fetch(url)
      .then((res) => res.json())
      .then((res) => {
        this.teamData = res;
        this.isLoad = false;
      });
  },
  methods: {
    removeUser(id) {
      this.teamData = this.teamData.filter((user) => user.id !== id);
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
}

.title {
  font-size: 2em;
  color: #ccc;
  margin-top: 20px;
  font-weight: bold;
}

.data {
  padding: 20px;
  text-align: left;
  color: #ccc;
}

.loading {
  padding-bottom: 30px;
}

button {
  margin-left: 10px;
  cursor: pointer;
  background: none;
  border: none;
  color: #ff0000;
  font-size: 20px;
}
</style>