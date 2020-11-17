<template>

<header>
  <h1 v-on:click="changeTitle">{{title}}</h1>

  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>List Of Hackers</h2>
  </div>

  </header>
</template>

<script>
import {bus} from '../main';

export default {

  props: {
    title: {
      type: String
    }
  },
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Hackers Community'
    }
  },
  methods: {
    changeTitle: function() {
      this.title = 'Vue Wizards'
      bus.$emit('titleChanged', 'Vue wizards');
      //this.$emit('changeTitle', 'Vue Start');
      // this.title = "Vue Wizards"
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
