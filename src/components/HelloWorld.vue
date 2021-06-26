<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p v-for="user in users" :key="user.id">{{ user.password }}</p>
  </div>
</template>

<script>
// import axios from "../axiosInstance";

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      users: [],
    };
  },
  mounted() {
    this.getIndex();
    this.intervalIndex();
  },
  methods: {
    getIndex() {
      this.$axios
        .get("http://localhost:8888/")
        .then((response) => (this.users = response.data))
        .catch((err) => {
          this.users = []
          console.log('hello world error: ',err)
        });
    },
    intervalIndex() {
      setInterval(() => {
        this.getIndex();
      }, 10000);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
