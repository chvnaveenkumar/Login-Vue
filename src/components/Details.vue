<template>
<div>
   <p>Add My student details</p>
   <input type="text" hint="Enter mail id:" v-model="sname">
   <button class="submit" @click="submit">Search</button>
   <p>Password: {{ student_password }} </p>
</div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      sname: "",
      student_password: ""
    };
  },
  methods: {
    submit() {
      console.log(window.localStorage.getItem("token"));
      axios({
          method:'post',
          url: 'http://localhost:3000/user/details',
          headers: {
          'x-auth': window.localStorage.getItem("token")
         },
        data: {
            sname: this.sname,
            }
      }).then(res => {
          this.student_password = res.data
          console.log(res.data);
        })
        .catch(err => {
          console.log(err);
        });
    }
  }
};
</script>
