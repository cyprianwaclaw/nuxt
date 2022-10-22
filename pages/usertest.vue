<template>
<div class="mt-20 mb-32 px-20 mx-aute gap-20" data-scroll-section>
  <div class="mt-20 mb-20">
      <form>
      <label>Enter Title</label>
      <input type="text" v-model="title"/>
      <input  class="ml-10" type="number" v-model="price"/>
      <button class="ng-bt-pri" @click="update">Send Message</button>
      </form>
  {{title}}
  </div>                        
  {{data}}                                     
</div>
</template>


<script setup lang="ts">
import { ref} from "vue";

const title = ref("");
const price = ref("");

const update = async() => await $fetch( "https://api.escuelajs.co/api/v1/products/61", {
        headers: {
           "Content-Type": "application/json",
                  },
        method: "put",
        body: { 
          'title': title.value,
          'price': price.value
         }
    });
    
const {data} = await useFetch('https://api.escuelajs.co/api/v1/products/61')
</script>