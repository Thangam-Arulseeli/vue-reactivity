 <!-- // <script setup lang="ts"> -->
  <!-- // let count = 1;  // Dynamically won't be updated - When changed by user/server
                     // Reactivity comes in place
//import { reactive, ref, toRef, toRefs } from 'vue';  
//import ReactiveTransform from './components/ReactiveTransform.vue';

// Lesson #1: Use reactive() for state which changes over time                   
  //let obj = reactive( { count: 1, 
  //                        list: ['Subscribe']}); 

  // Lesson #2: You can simply mutate properties directly! 
  // const increment = () => {
  //    obj.count++;
  //   // Object.assign(obj, {count: obj.count++}) -- Err
  //    obj.list.push('Like!');
  // }

  // Lesson #2.1 -- To include reactive(), have new concept Object.assign
  // const reset = () => {
  //   Object.assign(obj, {count: 1});
  // } 

  // To have many properties in the object, have the reactive form like the following
 // Lesson #4  // initialState with reactive
  // const initialState = { count: 1}
  // let obj = reactive({...initialState});
  
  // const increment = () => { 
  //       obj.count++;
  // }

  // const reset = () => {
  //     Object.assign(obj, initialState);
  // }
// -------------

// To have many properties in the object, have the ref form like the following
 // Lesson #4.1  // initialState with ref instead of reactive
//    const initialState = { count: 1}
//    let obj = ref({...initialState});
  
//    const increment = () => { 
//          obj.value.count++;
//    }

//    const reset = () => {
//       obj.value = {...initialState};
//    }
// // -------------


  // Lesson #3: You can't use reactive() for primitives... Reactive for objects or collections (map,sets etc..)
  //const something = reactive ('checking') // Wrong, since primitive
  // const count = reactive({ value: 1})   // Instance of reactive object is created and use

  // let count = ref(1); // instead of reactive object in #3, use ref(1), since it is referred in other places [ Note: we can also use string, boolean instead of int 1] 
  // No need to use .value property to access the value in the template, directly access count, it implicitly tells it is a ref
  // const increment2 = () => {
  //   count.value++;
  // }

  // const reset2 = () =>{
  //   // obj = { count: 1};
  //   //obj.count =1;
  //   count.value=1;
  // }


 // Lesson #5: Use reactive() for state which changes over time                   
 // Clean up the code
 
//  let obj1 = reactive( { count: 1, 
//                          list: ['Subscribe']}); 

//  // Lesson #: You can simply mutate propertoies directly! 
//   const increment1 = () => {
//      obj1.count++;
//     // Object.assign(obj, {count: obj.count++}) -- Err
//      obj1.list.push('Like!');
//   }
  
//  // If we use the reactive variables within function when returning the obj return it with toRefs(obj) like the following
//  function myComposable(){
//    const obj1 = reactive({ count: 1, list: ['Subscribe!'] });
  
//   return toRefs(obj1);
//  }
 // Remember DON'T destructure without toRefs()
  // toRefs() is used with composibles()
 // const { count, list} = toRefs(obj1); // Without function
//  const { count, list } = myComposable();  // With function true - composibles

// </script>  

//  <template> 
  // With #1 & #2 -->
  //    <!-- <div> Count: {{ obj.count }}
  //     <button @click="increment"> Add </button> 
  //   <button @click="reset">Reset</button>
  //   <ul>
  //     <li v-for="item in obj.list">
  //         {{ item }}
  //     </li>
  //   </ul>
  // </div>  -->

  
//   <!-- With #3 -->
//       <!-- <div> Count: {{ count }}
    
    
//      -->
//     <!-- <button @click="increment2"> Add </button> 
//     <button @click="reset2">Reset</button> -->
    

//     <!-- <ul>
//       <li v-for="item in obj.list">
//           {{ item }}
//       </li>
//     </ul>
//   </div>  -->


//   <!--With #5 -- Clean up  the code using const { count, list} = obj1; -->
//       <!-- <div> Count: {{ count }}
//       <button @click="increment1"> Add #5</button> 
    
//     <ul>
//       <li v-for="item in list">
//           {{ item }}
//       </li>
//     </ul>
//   </div>  

// </template> 
//  -->
 
<!-- Lesson #6 - Reactive Tranform-->
<!-- <script setup lang="ts">
// To get cleaner code - Use Reactive Transform (Set in vite.config.ts & env.d.ts)
import { toRefs } from 'vue';

const obj = $ref({ count: 1, list: ['Subscribe!']});

const increment = () => {
    obj.count++;
    obj.list.push('like');
};
const { count, list } = toRefs(obj);

</script>

<template>
<div> Count {{ count }} 
<button @click="increment"> Add using $ref & toRefs </button>
</div>
<ul>
    <li v-for="item in list"> {{ item }}</li>
</ul>
</template> -->
<!-- Reactive Tranform - Over -->



// <!-- <script setup lang="ts">
//   import {ref} from 'vue';
//   // let msg = "Hello World";   // Normal variable
//   // let msg= ref("Hello World !!!");   // Reactive variable -- when it is changed automatically updated in DOM
//   // let age= ref(10);
//    let msg= ref({num: 10})   // msg is object, num is property
//   //  const onClick = () => msg.value ="New World";    // Normal variable
//   const onClick = () => msg.value = "New World" 
// </script> -->

// <!-- <template> -->
//   <!-- <button @click="onClick"> Change </button>
//    {{ msg }}    Primitive data type 
//   {{ msg.num }}   -->
// <!-- </template> -->




<script setup lang="ts">
  import Reactivity1 from './components/Reactivity1.vue';
  import Reactivity2 from './components/Reactivity2.vue';
  import RefInitialStateVue from './components/RefInitialState.vue'
  import ReactiveTransform from './components/ReactiveTransform.vue';
  import WatchCompAPI from './components/WatchCompAPI.vue';
</script>

<template>
   <!-- <Reactivity1 />  -->
   <!-- <Reactivity2 />  -->
   <!-- <RefInitialStateVue> </RefInitialStateVue> -->
   <ReactiveTransform></ReactiveTransform>
   <!-- <WatchCompAPI></WatchCompAPI> -->
</template>