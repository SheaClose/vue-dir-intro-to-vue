<template>
  <div>
    <h3>{{ test }}</h3>
    <form @submit.prevent="addName(inputName)">
      <input type='text' placeholder='Name' v-model='inputName'/>
      <button @click="addName(inputName)">Submit</button>
    </form>
    <button @click="order = '+'">+</button>
    <button @click="order = '-'">-</button>
    <br/>
    <div :key='i' v-for="(e, i) in sortedAdmin">
      <Child :name="e.name" />
      <span :title="e.title" v-if='e.name[0] === "c"'>{{ e.name }}</span>
      <h2 :class="e.name[0] === 'j' ? 'red': 'blue'" v-else>{{e.name}}</h2>
    </div>
  </div>
</template>

<script>
import Child from '@/components/Child';


  export default {
    components:{
      Child: Child
    },
    data(){
      return {
        test: 'This is a test of the emergency podcast system',
        inputName: '',
        admin: [
          {name:{}},
          {name:'joshua'},
          {name:'cody', title:'Boss!'}
        ],
        order: ''
      }
    },
    methods:{
      addName(name){
        console.log('e: ', name);
        this.admin.push({name:name});
        this.inputName = ''
      }
    },
    computed:{
      sortedAdmin(){
        if (!this.order)return this.admin;
        let sorted = this.admin.slice().sort((a,b)=>a.name.localeCompare(b.name));
        return this.order === '+' ? sorted : sorted.reverse();
      }
    },
    created(){
      console.log('created');
    },
    mounted(){
      console.log('mounted');
    },
    updated(){
      console.log('updated');
    },
    beforeDestroy(){
      console.log('destroydd');
    }    
  }
</script>

<style>
  .red {
    background: red;
  }
  .blue {
    background: blue;
  }
</style>