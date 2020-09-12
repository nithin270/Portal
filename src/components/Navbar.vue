<template>
    <div class="Navbar">
        <nav class="nav-extended red lighten-1">
        <div class="nav-content">
            <router-link to="/">
            <span class="nav-title">NVS</span>
            </router-link>
            <ul class="right alignment">
                <li v-if="!user"><router-link to="/Login">Login</router-link></li>
                <li v-if="!user"><router-link to="/SignUp">SignUp</router-link></li>
            </ul>
        </div>
        </nav>
    </div>
</template>
<script>
export default {
    name:'Navbar',
data(){
        return{
          user: null
        }
},
created(){
firebase.auth().onAuthStateChanged((authUser) => {
  if (authUser) {
    this.user = authUser
  }else{
  this.user = null
  }
});
}
</script>
<style scoped>
.Navbar nav{
padding:0 20px;
}
.alignment{
    font-size: 1rem;
    color: #fff;
    display: block;
    padding: 33px 15px;
    cursor: pointer;
}
</style>
