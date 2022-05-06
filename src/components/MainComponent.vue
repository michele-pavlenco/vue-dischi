<template>
   <main>
       <div class="container debug"> 
           <div v-for="items in data" :key="items">
               <img src="items.poster" alt=""> {{items.author}}
           </div>

       </div>
      
   </main>
</template>

<script>
import axios from 'axios'

export default {
    name:'MainComponent',
  mounted(){
    axios.get("https://flynn.boolean.careers/exercises/api/array/music")
    .then( (res) => {
      console.log(res.data)
    })
  }
   
    
}
</script>

<style scoped>
main{
    background-color:hsl(209deg 33% 17%) ;
    height: calc(100vh - 60px);
}
</style>