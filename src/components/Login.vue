<template>
    <div>
        <form>
  <div class="form-group">
    <label for="exampleInputEmail1">Ingrese Email</label>
    <input v-model="email" type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
  </div>
  <div class="form-group">
    <label for="exampleInputPassword1">Contraseña</label>
    <input v-model="pass" type="password" class="form-control" id="exampleInputPassword1" placeholder="Password">
  </div>
  <button v-on:click="login" type="submit" class="btn btn-primary">Entrar</button>
</form>
    </div>
</template>

<script>
export default {
    name: 'Login',
    data() {
        return{
            email:'',
            pass:'',
            usuarios:[],
        }
    },

mounted() {
    this.loadUsers(),
    this.login()

},
methods: {
    loadUsers: async function() {
        const data = await fetch('./users.json')
        this.usuarios = await data.json()
    },
    login(){
       if (this.usuarios.email == this.email && this.usuarios.pass == this.pass) {
           console.log("todo piola amigo")
       }
       else{
           console.log("nada piola amigo")
       } 
    },
  }
}
</script>

