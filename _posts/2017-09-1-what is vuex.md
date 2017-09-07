---
layout:   post
title:    "Vuex 使用总结"
date:     2016-12-12
excerpt:  详细介绍 Vuex 的使用。
tags:     [Vue]
#comments: true
---

入 Vue 的坑已经一个多月了，自己也开发了一些组件，但对 Vuex 还是一知半解，所以上 Vuex 官网及网上找了些帖子，总结一下 Vuex 的使用。

#### 前言
**Vue 组件通信方式**可分为父子组件通信和非父子组件通信。父子组件使用 Prop 传递数据，在 Vue 中，父子组件的关系可以总结为 props down, events up。父组件通过 props 向下传递数据给子组件，子组件通过 events 给父组件发送消息；非父子组件通信可使用 global event bus ，挂载在一个空的 Vue 实例上。
{% highlight javascript %}
/* 父子组件 */
// 子组件需用 props 声明从父组件获取的数据
Vue.component('child', {
  // 声明 props
  props: ['message'],
  // 就像 data 一样，prop 可以用在模板内
  // 同样也可以在 vm 实例中像“this.message”这样使用
  template: '<span>{{ message }}</span>'
})
// 父组件中 传入字符串
<child message="hello!"></child>

/* 非父子组件 */
// 创建空的 Vue 实例
var bus = new Vue()

// 触发组件 A 中的事件
bus.$emit('id-selected', 1)

// 在组件 B 创建的钩子中监听事件
bus.$on('id-selected', function (id) {
  // data
})
{% endhighlight %}
当然，这只是适合小型 SPA 应用的开发，在大型 SPA 中，组件之间通信过多，组件与组件之间的通信变得难以开发和维护，并且并不符合组件化的思想开发。Vuex 就是来解决这一问题的。
#### Vuex 介绍
Vuex 是一个专为 Vue.js 应用程序开发的**状态管理模式**，管理应用所有组件的状态。状态可以理解为 Vue 实例的 data 保存的属性，并且这个属性需要与其它组件共享。Vuex 的核心是 store（仓库），包含应用中的 state（状态）。  
下面从官方的图例分析：
![image](/assets/img/images/vuex.png)
Vue Component（组件）接收用户操作等交互行为，执行 dispatch 方法触发对应的 Actions，显式地提交(commit) mutations 修改 State，通过 getters 获取到 State 新值，重新渲染 Vue Component。
代码表现为：
{% highlight javascript %}
// 需先引入 Vue,Vuex
Vue.use(Vuex)
const store = new Vuex.Store({
  state: {
    // 应用状态的数据
  },
  actions: {
    // 
  },
  mutations: {

  },
  getters: {
    // 从 store 中的 state 中派生出一些状态
  },  
  modules: {
    
  }
})
{% endhighlight %}