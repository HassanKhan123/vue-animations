<template>
  <transition-group tag="ul" name="user-list">
    <li v-for="user in users" :key="user" @click="removeUser(user)">
      {{ user }}
    </li>
  </transition-group>

  <div>
    <input type="text" ref="userName" />
    <button @click="addUser">Add User</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: ['Hassan', 'Khan', 'Babar'],
    };
  },
  methods: {
    addUser() {
      this.users.unshift(this.$refs.userName.value);
    },
    removeUser(name) {
      this.users = this.users.filter((usr) => usr !== name);
    },
  },
};
</script>

<style scoped>
ul {
  list-style-type: none;
  margin: 1rem 0;
  padding: 0;
}
li {
  border: 1px solid #ccc;
  padding: 1rem;
  text-align: center;
}
.user-list-enter-from {
  opacity: 0;
  transform: translateX(-30px);
}
.user-list-enter-active {
  transition: all 1s ease-out;
}
.user-list-enter-to {
  transform: translateX(0px);
  opacity: 1;
}

.user-list-leave-from {
  opacity: 1;
  transform: translateX(0px);
}
.user-list-leave-active {
  transition: all 1s ease-in;
}
.user-list-leave-to {
  transform: translateX(30px);
  opacity: 1;
}
</style>