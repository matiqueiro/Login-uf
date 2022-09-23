<template>
  <div class="login">
    <img alt="Urbano Fitness logo" src="../assets/Urban.png" class="img">
    <form class="px-4 py-3" v-on:submit.prevent="login">
      <div class="mb-3">
        <label class="form-label">User Name</label>
        <input type="text" class="form-control"  placeholder="Matias123" id="user" v-model="user">
      </div>
      <div class="mb-3">
        <label class="form-label">Password</label>
        <input type="password" class="form-control" placeholder="Password" id="password" v-model="password">
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
    user: "",
    password: ""
    }
  }, 
  methods:{
    login() {
      let json = {
        "user" : this.user,
        "password" : this.password
      };
      fetch('http://127.0.0.1:8000/api/auth/login', {
        "method": "post",
      })
       .then(response => response.json())
       .then(data => console.log(data))
    
    }
  }
  }
</script>
