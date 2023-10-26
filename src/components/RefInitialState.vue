<script setup lang="ts">
import { ref, reactive } from 'vue'
// To have many properties in the object, have the reactive form like the following
 // static initialState with reactive
   const initialState = { count: 1}   
  // let obj = reactive({initialState});
    let obj = reactive({...initialState});
  
   const increment = () => { 
         obj.count++;
   }

   const reset = () => {
       Object.assign(obj, initialState);
   }
// -------------

// To have many properties in the object, have the ref form like the following
 //  initialState with ref instead of reactive
     const initialState_ref = { count: 1}
     let obj_ref = ref({...initialState_ref});
  
     const increment_ref = () => { 
           obj_ref.value.count++;
     }

     const reset_ref = () => {
     // Object.assign(obj_ref, initialState_ref); 
      obj_ref.value = {...initialState_ref};
     }
 // -------------
</script>

<template>
    
    <div> Count - initialState-reactive: {{ obj.count }} 
      <button @click="increment"> Add Using reactive </button> 
      <button @click="reset">Reset - Using reactive</button> 
    </div>
    
    
    <div> Count - initialState-ref: {{ obj_ref.count }} 
      <button @click="increment_ref"> Add - Using ref </button> 
      <button @click="reset_ref">Reset Using ref</button> 
    </div>

    <!-- <ul>
       <li v-for="item in obj.list">
           {{ item }}
       </li>
     </ul> -->
   <!-- </div>  -->

</template>