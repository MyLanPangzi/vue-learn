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
## 创建 Create 
* new Vue({})
## 数据和方法 Data and methods 
*  数据属性是响应式的 data properties is reactive

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
## 生命周期钩子 Lifecycle hooks 
* beforeCreate
* created
* beforeMount
* mounted
* beforeUpdate
* updated
* beforeDestroy
* destroyed
![](lifecycle.png)

# 模板语法 Template Syntax 
## 插值 Interpolation 

* **Text** {{}} 文本插值

* **Raw HTML** v-html 原始HTML

* **Attributes** v-bind:attr 属性绑定

* **JS Expressions** 单值表达式 
  ##Directives

* **Arguments** v-bind:arg="property"

* **Dynamic Arguments** v-bind:[property]

* **Modifiers** 

## 快捷方式 Shorthands

* **v-bind** :

* **v-on** @

# 计算属性以及侦听器 Computed Properties and Watchers 

## 计算属性 computed property 

1. **computed properties are cached based on their reactive dependencies**

2.  计算属性能被缓存

3. ```html
   <div id="example">
       <p>Original message:{{message}}</p>
       <p>Computed reversed message:{{reversedMessage}}</p>
       <p>Reversed message:{{reverseMessage()}}</p>
       <p>Now: {{now}}</p>
   </div>
   ```

4. 

   ```javascript
       const vm = new Vue({
           el: '#example',
           data: {
               message: 'hello',
           },
           methods: {
               reverseMessage() {
                   return this.message.split('').reverse().join('');
               },
           },
           computed: {
               reversedMessage() {
                   return this.message.split('').reverse().join('');
               },
               now() {
                   return new Date().toLocaleString();
               }
           }
       });
   ```

5. **And the best part is that we’ve created this dependency relationship  declaratively: the computed getter function has no side effects, which  makes it easier to test and understand.**

6. 计算属性可以缓存，声明式的依赖，易于测试以及理解。

## 侦听器

**侦听器根据其他属性计算某个值，可用于异步操作。**

```html
<div id="watch-example">
    <p>
        Ask a yes/no question:
        <input v-model="question">
    </p>
    <p>{{answer}}</p>
</div>
```

```javascript
 const watchExampleVm = new Vue({
        el: '#watch-example',
        data: {
            question: '',
            answer: 'I cannot give you an answer until you ask a question!',
        },
        watch: {
            question(newQuestion, oldQuestion) {
                this.answer = 'Waiting for you to stop typing...';
                this.debouncedGetAnswer();
            },
        },
        created() {
            this.debouncedGetAnswer = _.debounce(this.getAnswer, 500);
        },
        methods: {
            getAnswer() {
                if (!this.question.includes('?')) {
                    this.answer = 'Questions usually contain a question mark.';
                    return;
                }
                this.answer = 'Thinking...';
                const vm = this;
                axios.get('https://yesno.wtf/api')
                    .then(res => vm.answer = _.capitalize(res.data.answer))
                    .catch(err => vm.answer = 'Error! Cloud not reach the API.' + err);
            },
        },
    });
```

