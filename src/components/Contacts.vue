<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
      <ul class='list'>
        <li class='item' v-for="char in characters" 
        :key='char.id' >
        <img class='img' :src='char.image' alt="">
        <p> {{char.name}}</p>
        <slot :geroi='char' />         <!-- scoped slots can only pass a whole object --->
        <p slot='id'>  {{ char.id}}</p>         <!-- named slots can only pass a property --->
        </li>
      </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      characters: []
    }
  },  
  methods: {
    async loadData() {
      const url = 'https://rickandmortyapi.com/api/character'
      const response = await fetch(url, {method:'GET'})
      const json = await response.json()
      this.characters = json.results
    }
  },
  async created() {
    await this.loadData()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}

.list {
 width:500px;
 margin: 2rem auto;
}

.item {
  display:flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.5rem;
}

.img {
  width:100px;
  border-radius: 100%;
}

</style>
