<template>
<div id="app">
  <h1>Test</h1>
  Username: {{ user.username }} - {{ fullname }}
  <strong>Followers: {{ followers }}</strong>
  <button @click="followUser">Follow</button>
</div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: '_Coolpot',
        firstName: 'Steve',
        lastName: 'Potts',
        email: 'coolpot_1@yahoo.com',
        isAdmin: true
      }
    }
  },
  components: {

  },
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained a follower`);
      }
    }
  },
  computed: {
    fullname() {
      return `${this.user.firstName} ${this.user.lastName}`
    }
  },
  methods: {
    followUser() {
      this.followers++;
    }
  },
  mounted() {
    this.followUser();
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  text-align: center;
}
</style>
