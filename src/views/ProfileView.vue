<script>
import { conditionalExpression } from '@babel/types';
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Profile Page",
      newStudent: {},
      userId: {}
    };
  },
  created: function () {
    axios.get(`/users/${this.$route.params.id}`).then(response => {
      console.log(response.data["id"])
      this.userId = response.data["id"]
    })

  },
  methods: {
    studentCreate() {
      console.log("creating student")
      axios.post("http://localhost:3000/students.json", this.newStudent).then(response => {
        console.log(response.data)
        this.newStudent = response.data
        console.log(this.newStudent.id)
        this.$router.push(`/students/${this.newStudent.id}`)
      })
    },

  },
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    Already have a student profile? <button v-on:click="(`/student/${this.currentUser}`)"> click here</button>

    <p> First Name: <input type="text" v-model="newStudent.first_name" /></p>
    <p> Last Name: <input type="text" v-model="newStudent.last_name" /> </p>
    <p> Email: <input type="text" v-model="newStudent.email" /> </p>
    <p> Phone Number: <input type="text" v-model="newStudent.phone_number" /> </p>
    <p> short bio: <input type="text" v-model="newStudent.short_bio" /> </p>
    <p> LinkedIn: <input type="text" v-model="newStudent.linked_in" /> </p>
    <p> Twitter: <input type="text" v-model="newStudent.twitter" /> </p>
    <p> Blog or Website: <input type="text" v-model="newStudent.blog_or_website" /> </p>
    <p> Online Resume: <input type="text" v-model="newStudent.online_resume" /> </p>
    <p> Git Hub: <input type="text" v-model="newStudent.git_hub" /> </p>
    <p> Photo: <input type="text" v-model="newStudent.photo" /> </p>
    <!-- <input type="submit" value="Create" /> -->
    <br />
    <button v-on:click="studentCreate()">Create Student</button>




  </div>
</template>

<style>

</style>