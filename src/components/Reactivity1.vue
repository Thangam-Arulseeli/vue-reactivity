<!-- Vue 3 - Default scripting is with TS, not with JS
Vue 3 - Related with Composition API, Not Options API
Composition API - No need for data(), methods and exports default for exporting the data & methods to the template like Options API
Automatically the data & methods are exported and used in Composition API -->
<script setup lang="ts">
 let count=1;
 let msg="Hai! Welcome!!";

 const increment_WOR = () =>{
   count++;  
 }

import { list } from 'firebase/storage';
import { reactive } from 'vue';
// Use reactive() for state which changes over time                   
  let obj = reactive( { count: 1,  list: ['Subscribe']
                        }); 

  // You can simply mutate properties directly! 
  const increment = () => {
     obj.count++;
    // Object.assign(obj, {count: obj.count++}) -- Err
     obj.list.push('Like!');
  }
  
  // To include reactive(), have new concept Object.assign
    const reset = () => {
     // obj = { count: 1};  // -- Working, when we remove list from obj (obj contains only 1 primitive value) -- 
     // obj.count = 1;  // -- Can be used, since it is a single value
     Object.assign(obj, {count: 1, list: ['Welcome'] });  // Generlised form to have many values in te object in real time scenerio 
   } 

   // You can simply mutate properties directly! -- decrement the value
   const decrement = () => {
     if (obj.count > 1) 
        obj.count--;
    else
       reset();
   }

   // Reactive is acceptable with objects/collections, not with primitive data
 //  const something = reactive( 10 );  // Err
// const something = reactive( new Map()); // Correct
// const something = reactive( new Set()); // Correct
</script>

<template>
    <div>
      <p> Count value (Without Reactivity) :  {{ msg + count }} </p>
      <button @click="increment_WOR">Increment Value-(No Reactivity)</button>
        <h3> Reactivity Example - Using reactive object </h3>
        <h4> Reactive Value: {{ obj.count }} </h4>
        <button @click="increment">Increment - Basics</button>
        <button @click="reset"> Reset Value </button>
        <button @click="decrement"> Decrement - Basics </button>
         <ul>
       <li v-for="item in obj.list">
          {{ item }}
      </li>
    </ul> 
    </div>
</template>
