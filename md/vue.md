# Introduce

## 文本插值
* {{}}
## 属性绑定
* v-bind :
## DOM结构
* v-if
## 循环
* v-for
## 事件绑定
* v-on @
## 表单交互
* v-model
## 自定义组件
* Vue.component

# Vue Instance 实例对象
## Create 创建
* new Vue({})
## Data and methods 数据和方法
* data properties is reactive 数据属性是响应式的

    * data 

    * methods

    * ```javascript
        new Vue({
        	el: '#app',
        	data: {
        		message: 'hello',
        	},
        	methods: {
        		hello(){ return this.message; }
        	}
        
        })
        ```

* start $ property is vm property $开头的属性是实例自带的属性
    * $el
    * $data
    * $watch
## Lifecycle hooks 生命周期钩子
* beforeCreate
* created
* beforeMount
* mounted
* beforeUpdate
* updated
* beforeDestroy
* destroyed
![](lifecycle.png)

# Template Syntax 模板语法
## Interpolation 插值

* **Text** {{}} 文本插值

* **Raw HTML** v-html 原始HTML

* **Attributes** v-bind:attr 属性绑定

* **JS Expressions** 单值表达式 
  ##Directives

* **Arguments** v-bind:arg="property"

* **Dynamic Arguments** v-bind:[property]

* **Modifiers** 

## Shorthands 快捷方式

* **v-bind** :

* **v-on** @

# Computed Properties and Watchers 计算属性以及侦听器

## computed property 计算属性

1. **computed properties are cached based on their reactive dependencies** 计算属性能被缓存
2.  **And the best part is that we’ve created this dependency relationship  declaratively: the computed getter function has no side effects, which  makes it easier to test and understand.**
3. 计算属性可以缓存，声明式的依赖，易于测试以及理解。