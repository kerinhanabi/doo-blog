<template>
  <div class="home">
      <h1>Home</h1>
      <!--p ref="p">My name is {{ name }} and my age is {{ age }}</p-->
      <p>My name is {{ name }} and my age is {{ age }}</p>
      <button @click="handleClick">Click Me</button>
      <button @click="age++">add 1 to age</button>
      <!-- using v-model to bind ref value , to update the name value in the p tag above -->
       <input type="text" v-model="name">
  </div>
</template>

<script>
import { ref } from 'vue';

// @ is an alias to /src


export default {
  name: 'Home',
  components: {
    
  },
      // the Option API format
      // data() {
          //return { whatever in here is reactive value ; if anything changes within here, will immediate reflect on the template }
      // }

  // format as using Composition API
  setup() {
    console.log('setup')

    // 1. console.log(this) //this.something as initial use as ref, is unavailable in setup, it will be undefined
    //1. below shows the right way to use / write ref
    //1. const p = ref(null) //auto import ref above

    //if show as below
    //1a. const p = ref('hello')
    //1a. then in browser console will show p value = hello

    //1a. console.log(p,p.value)

    //let name = 'daisy'  //not reactive value
    //let age = 30    // not reactive value meaning anything changes here won't reflect to template

    //2. to make the below a reactive value - use 'ref'
    const name = ref('daisy')
    const age = ref(30)
    
    //lets make a function: a click event
    const handleClick = () =>{
      console.log( 'you\'ve clicked me' )
      //1. console.log(p)
      //1. console.log(p.value)
      //1. p.value.classList.add('test') //p.value is a ref used in p tag
      //1. p.value.textContent='Hello Doo-er'

      //2. below method will change react the name & age value in template
      name.value = 'MeeMeee'
      age.value = 35
    }

    // data format below > 'key' use in template: 'key' use in setup
    //return { name: name, age: age }
    // or in short-form
    return { name, age, handleClick }
  },
  // created() {
  //   console.log('created')
  // },
  // mounted() {
  //   console.log('mounted')
  // }
}
</script>
