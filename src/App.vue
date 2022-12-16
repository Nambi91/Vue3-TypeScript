<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="site logo" />
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>

    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from "vue";
import JobList from "./components/JobsList.vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    // const state = reactive({
    //   name: "Link",
    //   age: 25 as number | string,
    // });
    // state.name = 999 // cannot change type;
    // state.age = "26";
    // return { ...toRefs(state) };
    // const name = ref("Links");
    // const age = ref<number | string>();
    // return { name, age };

    const order = ref<OrderTerm>("title");

    const jobs = ref<Job[]>([
      {
        title: "Developer",
        location: "Remote",
        salary: 8000,
        id: "1",
      },
      {
        title: "QA TESTER",
        location: "hybride",
        salary: 9000,
        id: "2",
      },
      {
        title: "Project Manager",
        location: "sur site",
        salary: 5000,
        id: "3",
      },
      {
        title: "CTO",
        location: "Site",
        salary: 10000,
        id: "4",
      },
    ]);

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleClick, order };
  },
});
</script>

<style scoped>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
header .title {
  display: flex;
  justify-content: center;
}
header img {
  width: 60px;
  margin-right: 20px;
}
header h1 {
  font-size: 3em;
}
</style>
