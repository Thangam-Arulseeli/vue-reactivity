<script>
// Example #1
export default{
    data(){
        return ({
          age: ''
        });
    },
   
    computed: {
        doubleAge() {
            return 2 * this.age;
        }
    },

    watch: {
        doubleAge(newValue) {
            alert(`yes, computed property changed: ${newValue}`);
        }
    }
}



// computed: {
//     name: {
//       get: function(){
//         return this.name;
//       }
//     }
//   },
//   watch: {
//     name: function(){
//       console.log('changed');
//     }
//   }
</script>


<!-- https://stackoverflow.com/questions/71451021/how-to-trigger-a-vue-method-when-computed-property-changes -->
<script>
// Example #2
  import API from '@/utils/Api.js'

    ...

    export default ({
        ...
        tableData: [],
            }
        },
    computed: {
      search() {
        return this.$store.getters.search;
      }
    },
    mounted() {
      this.getContacts();
    },
    methods: {
      async getContacts() {
        try {
          const {data} = await API.get('/contacts?search=' + this.search)
          this.tableData = data
          } catch (e) {
          console.error(e)
        }
      }
    },

    watch: {
      search () {
        this.getContacts();
      }
    }
  })

</script>

<script> 
// Example #3
export default {
    data() {
      return { 
        h1: null,
        wrap: null,
        shouldShowArrow: false,
      };
    },
      isEllipsisActive() {
        if (!this.wrap && !this.h1) {
          console.log("Not initialized", 'not initalized');
          return false;
        }
        return this.wrap.scrollHeight < this.h1.scrollHeight;
      },
    },
    mounted() {
      this.$nextTick(() => {
        this.h1 = this.$refs.h1;
        this.wrap = this.$refs.wrap;
      });
    },
    watch: {
      isEllipsisActive(newValue) {
        this.h1 !== null && console.log('changed')
      },
    },
  };

</script> 
<template>
    <!-- Example #3 -->
    <h1 v-if="isEllipsisActive">{{ title }}</h1>
</template>