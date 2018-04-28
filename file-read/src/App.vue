<template>
  <div id="app">
    <textarea rows="10" v-model="text"></textarea>
    <br>
		<text-reader @load="text = $event"></text-reader>
    <button v-on:click="showlist" type="button" class="btn btn-info">Show List</button>

    <ul class="list-group">
      <li  v-for="item in arraydata" class="list-group-item d-flex justify-content-between align-items-center">
        {{item.item}}
        <span class="badge badge-primary badge-pill">{{item.id}}</span>
      </li>
    </ul>

	</div>
</template>

</template>

<script>
import TextReader from "./TextReader";
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      text:'',
      jsondata:'',
      arraydata:''
    }

  },
methods:{
showlist(){
  this.jsondata = JSON.parse(this.text);
this.arraydata=this.jsondata.menu.items;
  console.log(this.jsondata.menu.items);
}

},



  components: {
  TextReader
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
