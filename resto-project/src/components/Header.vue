<template>
    <div class="nav">

        <router-link to="/">Home</router-link>
        <router-link to="/add">Add Resturant</router-link>
        


        <a v-on:click="logout" href="#">Logout</a>
    </div>

</template>

<script>
/* eslint-disable */
export default {
    name:'Header',
    methods:{
        logout()
        {
            localStorage.clear();
            this.$router.push({name:'Login'})
        }
    }
}
</script>

<style>
.nav{
    background-color: orangered;
    overflow: hidden;
    display: flex;
   justify-content: center;
    text-decoration: none;

}

.nav a{
    color: white;
    padding: 14px 16px;
    text-align: center;
    font-size: 17px;
    text-decoration: none;
    cursor: pointer;

}

.nav a:hover{
    color: black;
    text-decoration: underline;
    font-size: 20px;
    font-weight: bold;
    background-color: blanchedalmond;
    transition: 0.3s ease;

}
</style>