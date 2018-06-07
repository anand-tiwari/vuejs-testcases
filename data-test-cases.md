# Hello.vue
<template>
  <div class="container">
    <div class="container__counter">{{counter}}</div>
    <div class="container__msg">{{msg}}</div>
  </div>
</template>

# hello.js
export default {
    name: 'hello',
    components: {
      ClickMeButton
    },
    data () {
      return {
        msg: 'Welcome to Your Vue.js App',
        counter: 0
      }
    },
    methods: {
      incrementCounter: function () {
        this.counter += 1
      }
   }
}

# Hello.spec.js
import Vue from 'vue'
import VueResource from 'vue-resource'
import Hello from '@/components/Hello'

Vue.use(VueResource)
describe('Hello.vue', () => {
  let vm
  beforeEach(function () {
    const Constructor = Vue.extend(Hello)
    vm = new Constructor().$mount()
  })
  it('should check that msg is Welcome to Your Vue.js App', () => {
    expect(vm.$data.msg).to.equal('Welcome to Your Vue.js App')
  })
  
  it('should create a counter with value is zero', () => {
    expect(vm.$data.counter).to.equal(0)
  })
  
  it('should check the name of my vue', () => {
    expect(vm.$options.name).to.equal('hello')
  })
  
  it('should increment the counter to 1', () => {
    vm.incrementCounter()
    expect(vm.$data.counter).to.equal(1)
  })
})
