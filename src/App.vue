<template>
    <div id="app">
        <p :is="currentView">

        </p>



        <componentA :myValue="myValue" @my-event="oncomamyevent">
            <p slot="header">123</p>
            <p slot="footer">456</p>
        </componentA>
        <input type="text" v-model.number ="myValue">{{ myValue }}




        <p v-for="(item, index) in list">
            {{ item.name }}
            {{ item.price }}

        </p>
        <a v-if="isParta">asdfs</a>
        <a v-else>no data</a>
        <button v-on:click="addItem" >添加列</button>
        <input @keydown.enter="onkeydown">
        <input v-model="myBox" type="radio" value="apple">
        <input v-model="myBox" type="radio" value="banana">
        <input v-model="myBox" type="radio" value="pin">
        {{ myBox }}

        <select v-model="seelctnum">
            <option value="1">1</option>
            <option value="2">2</option>
        </select>
        {{ seelctnum }}


        <p v-color="'red'">hello world</p>
        <input type="text" v-focus >
    </div>
</template>

<script>
    import componentA from './components/a';
    import Vue from 'Vue';
    export default {
        components: {
            componentA
        },
        directives: {
            color: function (el, binding) {
                el.style.color = binding.value
            },
            focus: {
                inserted (el, binding) {
                    el.focus()
                }
            }
        },
        data () {
            return {
                currentView:'componentA',
                seelctnum : null,
                myBox: [],
                myValue: '',
                link: 'www.baidu.com',
                hello: 'world',
                dataA: 12,
                num: 1,
                status: true,
                isParta: true,
                classObj: {
                  redFont: true,
                  blueFont: false
                },
                list: [
                    {
                        'name': 'apple',
                        'price': 23
                    },
                    {
                        'name': 'banane',
                        'price': 24
                    },
                ],
                objlist: {
                    'name': 'ssss',
                    'price': '3232'
                },
                linkCss: {
                    'color': 'red',
                    'font-size': 20
                }
            }
        },
        methods: {
            addItem: function () {

                Vue.set(this.list,1,{
                    'name': 'sdfsdfsd',
                    'price': 26
                });
            },
            change () {
                this.isParta = !this.isParta
            },
            onkeydown (res) {
                console.log(res)
            },
            oncomamyevent (param) {
                console.log('oncomamyevent'+param)
            },
            getmyValueWithoutNum() {
                return this.myValue.replace(/\d/g,'')
            }

        },
        computed: {
            myValueWithoutNum: function () {
                return this.myValue.replace(/\d/g,'')
            }
        },
        watch: {
            myValue: function (val,oldval) {
                console.log(val,oldval)
            }
        }
        
    };
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
