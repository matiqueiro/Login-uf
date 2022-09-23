<template>
  <div class="login">
    <img alt="Urbano Fitness logo" src="../assets/Urban.png" class="img">
    <form class="px-4 py-3" v-on:submit.prevent="login">
      <div class="mb-3">
        <label class="form-label">Email</label>
        <input type="text" class="form-control"  placeholder="Matias123" v-model="user">
      </div>
      <div class="mb-3">
        <label class="form-label">Password</label>
        <input type="password" class="form-control" placeholder="Password" v-model="password">
      </div>
      <br>
      <button type="submit" class="btn btn-primary">Sign in</button>
    </form>


  
  </div>
</template>
<script>
  //importa axios
  export default{
  name: 'LoginView',
  components: {
    
  },
  data: function(){
    return{    
    email: "",
    password: ""
    }
  }, 
  methods:{
    login() {
      var formdata = new FormData();
      formdata.append("email", this.user);
      formdata.append("password", this.password);

      var requestOptions = {
        method: 'POST',
        body: formdata,
        redirect: 'follow'
      };

      fetch("http://127.0.0.1:8000/api/auth/login?email=pepemujica@gmail.com&password=12345678", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));
      }
  }
  }
</script>
