<template>
    <Header />
    <h3>Hello {{name}}, welcome to home page</h3>

    <table border="1px solid black">
        <tr class="header">
            <td>ID</td>
            <td>NAME</td>
            <td>CONTACT</td>
            <td>ADDRESS</td>
            <td>Actions</td>
        </tr>
        <tr v-for="item in restaurants" :key="item.id">
                <td>{{item.id}}</td>
                <td>{{item.name}}</td>
                <td>{{item.contact}}</td>
                <td>{{item.address}}</td>
                <td><router-link :to="'/update/'+item.id">Update</router-link></td>

        </tr>
    </table>
</template>

<script>
/* eslint-disable */
import Header from './Header.vue'
import axios from 'axios';
export default {
    name:'Home',
    data(){
        return {
            name:'',
            restaurants:[],
        }
    },
    components:{
        Header
    },

    async mounted()
    {
       let user =  localStorage.getItem('user-info');
       this.name = JSON.parse(user).name;
       
       if(!user)
       {
        this.$router.push({name:'SignUp'})
       }

       let result = await axios.get("http://localhost:3000/restaurants");
       console.log(result)

       this.restaurants = result.data;
    }

};



</script>

<style>

.header td{
    color:orange;
    font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
    font-weight:bolder;
    font-size: 25px;
    border-spacing: 10px;
}

table{
    width:100%;
    height: 150%;
    align-items: center;
    margin-left: auto;
    padding-left: 70px;
    padding-right: 70px;
    border: auto;
    border-radius: 10px;
    border-width: auto;
}




</style>