<template>
    <Header />
    <h3>Hello , welcome to add  page</h3>
    <form class="add">
        <input type="text" name="name" placeholder="Harish Bakery" v-model="restaurants.name"/>

        <input type="text" name="address" placeholder="Rajouri Garder,Delhi " v-model="restaurants.address"/>

        <input type="phonenumber" name="contact" placeholder="75757757" v-model="restaurants.contact"/> 
   
        <button  type="button" v-on:click="addrestaurats">Add New restaurants</button>
    </form>
</template>

<script>
/* eslint-disable */
import Header from './Header.vue';
import axios from 'axios';
export default {
    name:'Add',
    components:{
        Header
    },
    data()
    {
        return{
            restaurants:{
                name:'',
                address:'',
                contact:''
            }
        }

    },

    methods:{
         async addrestaurats()
         {
            console.log(this.restaurants)

            const result = await axios.post("http://localhost:3000/restaurants",{
                name:this.restaurants.name,
                address:this.restaurants.address,
                contact:this.restaurants.contact,

            });
            if(result.status==201)
            {
                this.$router.push({name:'Home'})
            }

            console.log("result",result)
         }

    },

    mounted()
    {
       let user =  localStorage.getItem('user-info');
       if(!user)
       {
        this.$router.push({name:'SignUp'})
       }
    }

};



</script>