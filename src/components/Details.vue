<template>
<div>
   <p>Add My student details</p>
   <input type="text" hint="Enter Name" v-model="sname">
   <button class="submit" @click="submit">Submit</button> 
</div>
</template>
<script>
import axios from "axios";
export default {
    data() {
        return {
            sname: ""
        }
    },
    methods: {
        submit(){
var instance = axios.create({
  baseURL: 'http://localhost:3000/user/details',
  headers: {'x-auth': window.localStorage.getItem('token')}
});
instance.post(this.data).then((res) =>{
    console.log(res)
}).catch((err) => {
    console.log(err);
});
;
}

    }
}
</script>
