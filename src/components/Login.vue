<template>
    <div>
        <form v-on:submit.prevent="login">
  <div class="form-group">
    <label for="exampleInputEmail1">Ingrese Email</label>
    <input v-model="emailIng" type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
  </div>
  <div class="form-group">
    <label for="exampleInputPassword1">Contraseña</label>
    <input v-model="passIng" type="password" class="form-control" id="exampleInputPassword1" placeholder="Password">
  </div>
  <button type="submit" class="btn btn-primary">Entrar</button>
</form>
    </div>
</template>

<script>
export default {
    name: 'Login',
    data() {
        return{
            emailIng:'',
            passIng:'',
            usuarios:[],
        }
    },

mounted() {
    this.loadUsers()

},
methods: {
    loadUsers: async function() {
        const data = await fetch('./users.json')
        this.usuarios = await data.json()
    },
    login()
    {
        for (let i = 0; i < this.usuarios.length; i++) 
        {
            if (this.usuarios[i].email === this.emailIng && this.usuarios[i].pass === this.passIng) 
            {
                window.alert("Bienvenido " + this.usuarios[i].nombre)
            }
            else
            {
                window.alert("Datos Incorrectos")
            } 
        
        }
       
    },
  }
}
</script>

