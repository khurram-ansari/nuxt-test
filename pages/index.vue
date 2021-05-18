<template>
  <div class="container">
    <div>
      <h1>Dynamic Data</h1>
      <br />
      <h6 v-for="data in dynamicData" :key="data.id">{{ data.title }}</h6>
    </div>
  </div>
</template>

<script>
import Single from "../components/Single";
export default {
  components: {
    Single,
  },
  data() {
    return {
      dynamicData: null,
    };
  },
  methods: {
    async asyncData() {
      const ip = await this.$axios.get(
        "https://jsonplaceholder.typicode.com/todos"
      );
      this.dynamicData = ip.data;
    },
  },
  created() {
    this.asyncData();
  },
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
