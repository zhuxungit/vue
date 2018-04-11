<template>
  <div :title="hello">
    <a v-if="isPartA">isPartA</a>
    <a v-else>nodata</a>
    <p v-for="(value,key) in objList">{{value+key}}</p>
    <button @click="addItem">addItem</button>
    <input @keydown.enter="onkeydown"/>
    <input v-model="myBox" type="radio" value="apple">
    <input v-model="myBox" type="radio" value="banane">
    <input v-model="myBox" type="radio" value="pin">
    <select v-model="selection">
      <option v-for="item in selectOption" :value="item.value">{{item.text}}</option>
    </select>
    {{myBox}}
    {{selection}}
    <comA @my-event="onComaMyEvent"></comA>

    <input v-model="myValue" type="text"/>
    {{myValue}}
  </div>
</template>

<script>
import Vue from 'vue'
import comA from './components/a'
export default {
  components: {
    comA
  },
  computed: {
    myValueWithoutNum () {
      return this.myValue.replace(/\d/g,'')
    }
  },
  data () {
    return {
      selectOption: [
        {
          text: 'apple',
          value: 0
        },
        {
          text: 'banana',
          value: 1
        }
      ],
      selection: '',
      myBox: [],
      myValue: '',
      isPartA: true,
      hello: '<p>world</p>',
      num: 1,
      status: false,
      list: [
        {
          name: 'apple',
          price: 34
        },
        {
          name: 'banana',
          price: 56
        }
      ],
      objList: {
        name: 'apple',
        price: 34,
        color: 'red',
        weight: 14
      }
    }
  },
  methods: {
    addItem () {
      Vue.set(this.list, 1, {
        name: 'pin',
        price: 23
      })
    },
    toggle () {
      this.isPartA = !this.isPartA
    },
    onkeydown () {
      console.log('sda')
    },
    onComaMyEvent (parmfromA) {
      console.log('onComaMyEvent' + parmfromA)
    },
    getMyValWithoutNum () {
        return this.myValue.replace(/\d/g,'')
    }
  },
  watch: {
      myValue: function (val, oldVal) {
      console.log(val, oldVal)
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
