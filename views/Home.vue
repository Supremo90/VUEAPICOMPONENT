<template>
  <div class="home">
    <p>{{a.name}} and my age is {{a.age}}</p>
    <button @click="a.age++">Add Age </button>
    <button @click="aa">XXXXX </button>
    <h1>REACTIVE</h1>
    <p>{{b.name}} and my age is {{b.age}}</p>
    <button @click="bb">REACTIVE </button>
    <hr/>
    <input type="text" v-model="search" style="text-transform:uppercase">
    <p>search term - {{search}}</p>
    <p v-for="name in searchfilter" :key="name">
      {{name}}
    </p>
  </div>
</template>

<script>
// @ is an alias to /src
import { ref, reactive, computed } from 'vue'   //si importa sempre
export default {
  name: 'Home',
  setup(){
    const a = ref({ name: 'Mario', age: 40}); //serve per sostituire il this normale
    const b = reactive({ name: 'CARLO', age: 140});//nuova modalità d'importazione delle variabili
    const aa = () => {
      alert(a.value.name);
    }

    //REACTIVE FUNCTION
     const bb = () => {
      alert(b.name);
    }
    //Computed
    const search = ref('');
    const names = ref(['A','B','C','GG','HHHH','HHIIBSHUW']);
    const searchfilter = computed(() => {
      return names.value.filter((name) => name.includes(search.value.toUpperCase()))
    })
    



      return {a,aa,b,bb, names,search,searchfilter}
  }
    
}

</script>
