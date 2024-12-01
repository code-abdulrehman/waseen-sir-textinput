<template>
  <div>
    <h1>{{ msg }}</h1>
  </div>
  <div>
    <input type="text" id="txtadditem" v-model="insertedvalue" v-on:keydown.enter="additem">
    <div class="liststyle">
      <ul id="list">
        <li>Add Names</li>
        <li v-for="(item, index) in items" :key="item" >{{ item }} <button v-on:click="addtoanotherlist(item)" >add</button> <button v-on:click="remove(index)">Remove</button></li>
        
      </ul>
    </div>
      <div class="liststyle">
      <ul>
        <li>Final Names </li>
        <li v-for="item in anotherlist" :key="item">{{ item }} </li>
        <button v-on:click="removelist">Clear</button>
      </ul>
    </div>
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
      items: [],
      anotherlist: [],
    }
  },
  methods: {
    additem() {
      this.items.push(this.insertedvalue)
      this.insertedvalue = ""
    },
    remove(index){
        this.items.splice(index, 1);
        // this.items.$remove(index);
    },
    addtoanotherlist(insertedvalue) {
      this.anotherlist.push(insertedvalue)
      insertedvalue = ""
    },
    removelist() {
      this.anotherlist = [];

    }
  }
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.liststyle {
  margin: 40px 0 0;
  border: 1px solid black; width: 300px;
}
/* ul {padding-left:1em} */
/* li {padding-left:1em} */

</style>
