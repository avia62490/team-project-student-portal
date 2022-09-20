<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Students Index",
      students: []
    };
  },
  created: function () {
    this.allStudents()
  },
  methods: {
    allStudents() {
      axios.get("/students.json").then(response => {
        console.log(response.data)
        this.students = response.data

      })
    }
  },
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="student in students">
      User ID{{student.user}}
      <hr />

    </div>

  </div>
</template>

<style>

</style>