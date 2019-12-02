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

# Vue Instance
## Create
* new Vue({})
## Data and methods
* data properties is reactive

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

* start $ property is vm property
    * $el
    * $data
    * $watch
## Lifecycle hooks 
* beforeCreate
* created
* beforeMount
* mounted
* beforeUpdate
* updated
* beforeDestroy
* destroyed
![](lifecycle.png)

# Template Syntax
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

# Computed Properties and Watchers

## computed property
