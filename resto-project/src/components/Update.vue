<template>
    <Header />
    <h3>Hello , welcome to update page</h3>

    <form class="add">
        <input type="text" name="name" placeholder="Harish Bakery" v-model="restaurants.name"/>

        <input type="text" name="address" placeholder="Rajouri Garder,Delhi " v-model="restaurants.address"/>

        <input type="phonenumber" name="contact" placeholder="75757757" v-model="restaurants.contact"/> 
   
        <button  type="button" v-on:click="updaterestaurats">Update restaurants</button>
    </form>
</template>

<script>
/* eslint-disable */
import Header from './Header.vue'
import axios from 'axios'
export default {
    name:'Update',
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
        async updaterestaurats()
        {
            const result = await axios.put("http://localhost:3000/restaurants",{
                name:this.restaurants.name,
                address:this.restaurants.address,
                contact:this.restaurants.contact,

            });
            if(result.status==200)
            {
                this.$router.push({name:'Home'})
            }
        }
    },

   async  mounted()
    {
       let user =  localStorage.getItem('user-info');
       if(!user)
       {
        this.$router.push({name:'SignUp'})
       }

       const result = await axios.get("http://localhost:3000/restaurants/"+ this.$route.params.id)
    
       console.log(result)
       this.restaurants = result.data
    }

};



</script>