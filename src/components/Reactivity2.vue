<script setup lang="ts">
import {reactive } from 'vue';
import { ref } from 'vue';
// Lesson #3: You can't use reactive() for primitives... Reactive for objects or collections (map,sets etc..)
  //const something = reactive ('checking') // Wrong, since primitive
 // const something = reactive (Map)
  // When we use reactive, to use the primitive values we must use value property like the following
  const count_rtive = reactive({ value: 1})   // Instance of reactive object is created and use

  const decrement_rtive = () => {
     if (count_rtive.value > 0)
        count_rtive.value--;
      else
         count_rtive.value = 0;
  }
   
  let count_ref = ref(100); // instead of reactive object in #3, use ref(1), since it is referred in other places [ Note: we can also use string, boolean instead of int 1] 
    let msg = ref('Hai! Welcome!!'); // String value 
 // No need to use reactive({value: 1})  -- .value property to access the value in the template, directly access count, it implicitly tells it is a ref
   const increment2 = () => {
     count_ref.value++;
     msg.value='Come in!!';
   }

   const reset2 = () =>{
     // obj = { count: 1};
     //obj.count =1;
     count_ref.value=1;
     msg.value='Hai! Welcome!!';
   }
</script>

<template>
  <div>
     <p> Count Using reactive : {{ count_rtive.value }} </p>
     <p> <button @click="count_rtive.value++"> Add Use reactive - value property </button> 
      <button @click="decrement_rtive"> Subtract Use reactive - value property </button>
    </p>
  </div>

   <div>
    <p>Count Using ref: {{ count_ref + msg }} </p>
    <p><button @click="increment2"> Add Use ref </button> 
    <button @click="reset2">Reset</button> 
    </p>
    
   </div>  
</template>