<template>
  <div id="app">
    <img src="./assets/logo.png">
    
    <app-header v-bind:title="title" v-on:changeTitle="updateTitle($event)"></app-header>
    
     <form-helper>
      <div slot="form-header">
        <h3>Title of form</h3>
        <p>Information about form</p>
      </div>
      <div slot="form-fields">
        <input type="text" placeholder="name" required/>
        <input type="password" placeholder="password" required/>
      </div>
      <div slot="form-controls">
        <button v-on:click="handleSubmit">Submit</button>
      </div>

     </form-helper>

     <div>
       <keep-alive>
         <component v-bind:is="component"> </component>
       </keep-alive>
      <button v-on:click="component = 'form-one'">Show form one</button>
      <button v-on:click="component = 'form-two'">Show form Two</button>
     </div>

    <app-ninjas v-bind:ninjas="ninjas"></app-ninjas>
    <app-footer v-bind:title="title"></app-footer>
    
   
   
  </div>
</template>

<script>
import Header from './components/Header';
import Ninjas from './components/Ninjas';
import Footer from './components/Footer';
import formHelper from './components/formHelper';
import formOne from './components/formOne';
import formTwo from './components/formTwo';

export default {
  name: 'App',
  components: {
    'app-header': Header,
    'app-ninjas': Ninjas,
    'app-footer': Footer,
    'form-helper': formHelper,
    'form-one': formOne,
    'form-two': formTwo,
  
  },
  data(){
    return{
      ninjas: [
                {name: 'Ryu', speciality: 'React Wizard',show: false},
                {name: 'Crystal', speciality: 'HTML Wizadry',show: false},
                {name: 'Hitoshi', speciality: 'Vue Pro',show: false},
                {name: 'Tango', speciality: 'AWS Witch',show: false},
                {name: 'Kami', speciality: 'Database Grandfather',show: false},
                {name: 'Yoshi', speciality: 'Data Munger',show: false}
            ],
        title: "I am a dynamic title"
    }
  },
  methods: {
    updateTitle: function(updatedTitle){
      this.title = updatedTitle
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
