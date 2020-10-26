<template>
  <div>
    <div>
      <keep-alive>
        <component :is="component"> </component>
      </keep-alive>
      <button v-on:click="component = form-one">Show form one</button>
      <button v-on:click="component = form-two">Show form two</button>
    </div>
    <hr>
    <div>
    <form-helper>
      <div slot="form-header">
        <h3>This is the title of the form</h3>
        <p> Information about the form</p>
      </div>
      <div slot="form-feilds">
        <input type="text" placehoder="name" required/>
        <input type="password" placehoder="password" required/>
      </div>
      <div slot="form-controls">
        <button v-on:click="handleSubmit">Submit</button>
      </div>
    </form-helper>
    </div>
    <hr>
    <app-header :title="title" v-on:changeTitle="updateTitle($event)"></app-header>
    <app-ninjas :ninjas="ninjas"></app-ninjas>
    <app-footer :title="title"></app-footer>
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
  components:{
    'app-header': Header,
    'app-footer': Footer,
    'app-ninjas': Ninjas,
    'form-helper': formHelper,
    'form-one': formOne,
    'form-two': formTwo,
  },
  data () {
    return {
      ninjas: [
                {name: 'Ryu', speciality: 'Vue Components', show: false},
                {name: 'Crystal', speciality: 'HTML Wizardry', show: false},
                {name: 'Hitoshi', speciality: 'Click Events', show: false},
                {name: 'Tango', speciality: 'Conditionals', show: false},
                {name: 'Kami', speciality: 'Webpack', show: false},
                {name: 'Yoshi', speciality: 'Data Diggin', show: false}
            ],
      title: "Vue Ninjas",
      component : 'form-one'
    }
  },
  methods:{
    updateTitle: function(updatedTitle){
      this.title = updatedTitle
    }
  }
}
</script>

<style scoped>

</style>
