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
      axios.get('students/4.json').then(response => {
        console.log(response.data)
        this.studentInfo = response.data
      })
    },
    methods: {},
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

  </div>
</template>

<style></style>