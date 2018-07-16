<template>
  <div class="hello">
    <!-- Material form login -->
<form @submit.prevent = "submit">
    <p class="h4 text-center mb-4">Sign in</p>

    <!-- Material input email -->
    <div class="md-form">
        <i class="fa fa-envelope prefix grey-text"></i>
        <input type="email" id="materialFormLoginEmailEx" class="form-control" v-model="formdata.email" >
        <label for="materialFormLoginEmailEx">Your email</label>
    </div>


    <!-- Material input password -->
    <div class="md-form">
        <i class="fa fa-lock prefix grey-text"></i>
        <input type="password" id="materialFormLoginPasswordEx" class="form-control" v-model="formdata.password">
        <label for="materialFormLoginPasswordEx">Your password</label>
    </div>

    <div class="text-center mt-4">
        <button class="btn btn-default" type="submit">Login</button>
    </div>
</form>
<!-- Material form login -->
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: 'HelloWorld',
  data () {
    return {
      formdata:{

      }
  }
  },
  methods: {
    submit(){
      axios.post('http://localhost:3000/login/user',this.formdata).then((res) =>{
        window.localStorage.setItem("token",res.data);
        this.$router.push("/Details")
      });
  }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
