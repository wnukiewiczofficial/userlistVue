<template>
  <h1>User List using REST API</h1>
  <p>https://stackexchange.com/</p>
  <img alt="Vue logo" src="./assets/logo.png" />
  <MyTable :data="tableData.value" />
</template>

<script>
import MyTable from "./components/MyTable.vue";
import { ref } from "vue";

export default {
  name: "App",
  components: {
    MyTable,
  },
  setup() {
    const tableData = ref([]);
    return { tableData };
  },
  methods: {
    fetchUsers() {
      fetch(
        "https://api.stackexchange.com/2.3/users?order=desc&sort=reputation&site=stackoverflow"
      )
        .then((response) => response.json())
        .then((data) => {
          console.log(data.items);
          this.tableData.value = data.items.map((item) => {
            return { displayName: item.display_name, location: item.location };
          });
        })
        .catch((err) => console.log(err.message));
    },
  },
  mounted() {
    this.fetchUsers();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
