<script setup lang="ts">
// To get cleaner code (Destructuring the values in reactive object) - Use Reactive Transform (Set in vite.config.ts & env.d.ts)

// vite.config.ts file inclusions for Reactive Transform
// https://vitejs.dev/config/
// export default defineConfig({
//   plugins: [
//     vue(
//        {
//         reactivityTransform: true
//        }
//     ),
//   ],

// env.d.ts file inclisions for Reactive Transform 
 /// <reference types="vue/macros-global" />


// Instead of using the code in Reactivity1.vue using reactive object, we have the cleaner code without obj.count

import {reactive, toRefs} from  'vue';
// import { $toRef, $ref} from 'vue/macros'; // Import $ref/$toRef explicitly 
//import { toRefs } from 'vue'; 

const obj = reactive({ count: 1, list: ['Subscribe!']});
 
const increment_rtive = () => {
    obj.count++;   // Count is frozen - Not working
    obj.list.push('like');
    
};

function myComposable(){
    const obj_com = reactive({ count1: 1, list1: ['Subscribe!']});
    return toRefs(obj_com);
}

// const { count, list} = obj;  -- Count is frozen -- For that use toRefs like below
// Lesson #4 -- Remember Don't destructure without toRefs() 
const { count, list } = toRefs(obj); // // Destructuring the object values

// Using Composible
const { count1, list1 } = myComposable();

// const increment_com = () => {
//     obj_com.count1++;   // Count is frozen - Not working
//     obj_com.list1.push('like');
// };

// Reactive Tranform using $ref
const obj_rtsform = $ref({ count_t: 1, list_t: ['Subscribe!']});
const increment_rtsform = () =>{
    obj_rtsform.count_t++;
    obj_rtsform.list_t.push('Like!!');
}

// Destructuring the object values
const { count_t, list_t } = toRefs(obj_rtsform);
</script>

<template>
<div> Count Using toRefs :  {{ count }} 
<button @click="increment_rtive"> Add - Using  toRefs </button>
</div>
<ul>
    <li v-for="item in list"> {{ item }}</li>
</ul>

<div> Count Using Composable  {{ count1 }} 
<button @click="increment_rtive"> Add - Using  toRefs </button>
</div>
<ul>
    <li v-for="item in list1"> {{ item }}</li>
</ul>

<p> Reactive Tranform  is a composition API specific feature... currently an experimental feature. It is disabled by default and requires explicit-opt-in. It my also change before being finalised.
    Set in vite.config.ts and env.d.ts file.
    Every reactivity API that returns refs will have a $ -prefixed macro eqivalent. These API's include
   <pre>
    . ref -> $ref
    . computed -> $computed
    . shallowRef -> $shallowRef
    . customRef -> $customRef 
    . toRef -. $toRef
These macros are globally available and do not need to be imported when Reactivity Transform is enabled, but you can optionally import them from vue/macros if you want to be more explicit..
import {$ref} from 'vue/macros'
</pre>
</p>
<div> Count Using Reactive Tranform  {{ count_t }} 
<button @click="increment_rtsform"> Add - Using  toRefs </button>
</div>
<ul>
    <li v-for="item in list_t"> {{ item }}</li>
</ul>

</template>

