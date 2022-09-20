<script>
import axios from 'axios'
export default {
  data: function () {
    return {
      message: "Viewing Student Profile",
      studentInfo: {}
    };
  },
  created: function () {
    axios.get(`students/${this.$route.params.id}.json`).then(response => {
      console.log(response.data)
      this.studentInfo = response.data
    })
  },
  methods: {
    editProfile() {
      console.log("editing profile")
      document.querySelector('#student-details').showModal();
    },
    updateStudent() {
      console.log("updating student")
      axios.patch(`/students/${this.studentInfo.id}.json`, this.studentInfo).then(response => {
        console.log(response.data)
      })

    }
  },
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <p>First Name: {{studentInfo.first_name}}</p>
    <p>Last Name: {{studentInfo.last_name}}</p>
    <p>Email: {{studentInfo.email}}</p>
    <p>Phone NUmber: {{studentInfo.phone_number}}</p>
    <p>Bio: {{studentInfo.short_bio}}</p>
    <p>LinkedIn: {{studentInfo.linked_in}}</p>
    <p>Twitter: {{studentInfo.twitter}}</p>
    <p>Blog/Website: {{studentInfo.blog_or_website}}</p>
    <p>Resume: {{studentInfo.online_resume}}</p>
    <p>GitHub: {{studentInfo.github}}</p>
    <p>photo: {{studentInfo.photo}}</p>

    <button v-on:click="editProfile()">Edit</button>

    <dialog id="student-details">
      <form method="dialog">

        <p>First Name: <input type="text" v-model="studentInfo.first_name" /> </p>
        <p>Last Name: <input type="text" v-model="studentInfo.last_name" /> </p>
        <p>Email: <input type="text" v-model="studentInfo.email" /> </p>
        <p>Phone NUmber: <input type="text" v-model="studentInfo.phone_number" /> </p>
        <p>Bio: <input type="text" v-model="studentInfo.short_bio" /> </p>
        <p>LinkedIn: <input type="text" v-model="studentInfo.linked_in" /> </p>
        <p>Twitter: <input type="text" v-model="studentInfo.twitter" /> </p>
        <p>Blog/Website: <input type="text" v-model="studentInfo.blog_or_website" /> </p>
        <p>Resume: <input type="text" v-model="studentInfo.online_resume" /> </p>
        <p>GitHub: <input type="text" v-model="studentInfo.github" /> </p>
        <p>photo: <input type="text" v-model="studentInfo.photo" /> </p>
        <button v-on:click="updateStudent()">Update</button>
      </form>

    </dialog>
  </div>
</template>

<style>

</style>