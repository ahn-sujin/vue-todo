## ๐๋ชฉ์ฐจ 

### [1. ๋ฌธ์  ํด๊ฒฐ์ ์ํ ์ ํ๋ฆฌ์ผ์ด์ ๊ตฌ์กฐ ๊ฐ์ ](#1-๋ฌธ์ -ํด๊ฒฐ์-์ํ-์ ํ๋ฆฌ์ผ์ด์-๊ตฌ์กฐ-๊ฐ์ )

### [2. props์ ์ด๋ฒคํธ ์ ๋ฌ์ ์ด์ฉํด ํ  ์ผ ์๋ ฅ ๊ธฐ๋ฅ ๊ฐ์ ํ๊ธฐ](#2-props์-์ด๋ฒคํธ-์ ๋ฌ์-์ด์ฉํด-ํ -์ผ-์๋ ฅ-๊ธฐ๋ฅ-๊ฐ์ ํ๊ธฐ)

### [3. ์ด๋ฒคํธ ์ ๋ฌ์ ์ด์ฉํด Clear All ๋ฒํผ ๊ธฐ๋ฅ ๊ฐ์ ํ๊ธฐ](#3-์ด๋ฒคํธ-์ ๋ฌ์-์ด์ฉํด-Clear-All-๋ฒํผ-๊ธฐ๋ฅ-๊ฐ์ ํ๊ธฐ)

### [4. ์ด๋ฒคํธ ์ด์ฉํด ์ญ์  ๊ธฐ๋ฅ ๊ฐ์ ํ๊ธฐ](#4-์ด๋ฒคํธ-์ด์ฉํด-์ญ์ -๊ธฐ๋ฅ-๊ฐ์ ํ๊ธฐ)


<br><br>

### ๐ํ์ฌ ์ ํ๋ฆฌ์ผ์ด์ ๊ตฌ์กฐ์ ๋ฌธ์ ์ 
```
- ํ  ์ผ์ ์๋ ฅํ์ ๋, ํ  ์ผ ๋ชฉ๋ก์ ๋ฐ๋ก ๋ฐ์๋์ง ์์
- ํ  ์ผ์ ๋ชจ๋ ์ญ์ ํ์ ๋, ํ ์ผ ๋ชฉ๋ก์ ๋ฐ๋ก ๋ฐ์๋์ง ์์
```


<br>

## 1. ๋ฌธ์  ํด๊ฒฐ์ ์ํ ์ ํ๋ฆฌ์ผ์ด์ ๊ตฌ์กฐ ๊ฐ์ 

![image](/img/vue04-1-1.png)

- ์์ธ
  - ํ๋ฉด์ 4๊ฐ์ ์์ญ(```TodoHeader``` ```TodoInput``` ```TodoList``` ```TodoFooter```)์ผ๋ก ๋ถ๋ฆฌํด ๋์๊ธฐ ๋๋ฌธ์ ํ ์์ญ์ ์ฒ๋ฆฌ ๊ฒฐ๊ณผ๋ฅผ ๋ค๋ฅธ ์์ญ์์ ๊ฐ์งํ์ง ๋ชปํ๋ค.

![image](/img/vue04-2.png)

- ํด๊ฒฐ๋ฐฉ๋ฒ 
  - ํ์ฌ ์ ํ๋ฆฌ์ผ์ด์์ ๊ฐ๊ฐ์ ์ปดํฌ๋ํธ์์๋ง ์ฌ์ฉํ  ์ ์๋ ๋ทฐ ๋ฐ์ดํฐ ์์ฑ์ ๊ฐ๊ณ  ์๋ค.
  
    (```TodoInput```-newTodoItem, ```TodoList```-todoItems)
    
  - ๋ก์ปฌ ์คํ ๋ฆฌ์ง, ```TodoInput```, ```TodoList```๋ ๋ชจ๋ todoItems๋ผ๋ ๊ฐ์ ์ฑ๊ฒฉ์ ๋ฐ์ดํฐ๋ฅผ ์ฌ์ฉํ๊ณ  ์๋ค.
  - **์ต์์ ์ปดํฌ๋ํธ์ธ ```App``` ์ปดํฌ๋ํธ์ todoItems ๋ผ๋ ๋ฐ์ดํฐ๋ฅผ ์ ์ํ๊ณ  ํ์ ์ปดํฌ๋ํธ ```TodoList```์ Props๋ก ์ ๋ฌํ๋ค.**
 
- ๋ฌ๋ผ์ง ์ 
  - ํ  ์ผ ๋ฐ์ดํฐ ์ถ๊ฐ, ์ญ์ ๋ฅผ ๋ชจ๋ ํ์ ์ปดํฌ๋ํธ ```TodoInput```, ```TodoList```์์ ํ์๋ค๋ฉด, 
  - ๋ทฐ ๋ฐ์ดํฐ ์์ฑ todoItems์ ๋ก์ปฌ ์คํ ๋ฆฌ์ง์ **๋ฐ์ดํฐ ์กฐํ, ์ถ๊ฐ, ์ญ์ **๋ฅผ ๋ชจ๋ **```App```์ปดํฌ๋ํธ**์์ ํ๋ค.
  - **ํ์ ์ปดํฌ๋ํธ๋ค**์ **์ด๋ฒคํธ ๋ฐ์๋ง** ์คํํ๋ค. 
  

<br>

## 2. props์ ์ด๋ฒคํธ ์ ๋ฌ์ ์ด์ฉํด ํ  ์ผ ์๋ ฅ ๊ธฐ๋ฅ ๊ฐ์ ํ๊ธฐ
1) ์ต์์ ์ปดํฌ๋ํธ์ธ ```App```์ ๋ฐ์ดํฐ ์์ฑ todoItems๋ฅผ ์ ์ธํ๋ค.
2) ์ ์ธํ todoItems ์์ฑ์ ```TodoList```์ปดํฌ๋ํธ์ props๋ก ์ ๋ฌํ๋ค.
3) ```TodoInput```์ปดํฌ๋ํธ ํ๊ทธ์ ํ ์ผ ์ถ๊ฐ ๋ฒํผ์ ํด๋ฆญํ์ ๋ ```App```์ปดํฌ๋ํธ๋ก ์ด๋ฒคํธ๋ฅผ ์ ๋ฌ ํ  ์ ์๊ฒ v-on ๋๋ ํฐ๋ธ๋ฅผ ์ถ๊ฐํ๋ค.
4) ํด๋น ์ด๋ฒคํธ๋ฅผ ๋ฐ์์ ์คํํ  ๋ฉ์๋๋ ์ถ๊ฐํ๋ค.

```vue
<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <!-- 3 -->
    <TodoInput v-on:inputTodo = "addTodo"></TodoInput>
    <!-- 2 -->
    <TodoList v-bind:propsdata = "todoItems"></TodoList> 
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
  export default{
    // 1 
    data(){
      return{
        todoItems: []  
      }
    },
    methods:{
      // 4
      addTodo(){
          // ๋ก์ปฌ์คํ ๋ฆฌ์ง์ ๋ฐ์ดํฐ๋ฅผ ์ถ๊ฐํ๋ ๋ก์ง
      }
    },
    components: {
      'TodoHeader' : TodoHeader,
      'TodoInput' : TodoInput,
      'TodoList' : TodoList,
      'TodoFooter' : TodoFooter
    }
}
</script>
...

```

### 2-1. TodoInput ์ปดํฌ๋ํธ์ TodoList ์ปดํฌ๋ํธ ์์ ํ๊ธฐ
- ```TodoInput```์ปดํฌ๋ํธ์ addTodo() ๋ฉ์๋ ์ถ๊ฐ 
```vue
...
<script>
  export default{
    export default{
        data(){
            return{
                newTodoItem: ''
            }
        },
        methods: {
            addTodo(){
                if(this.newTodoItem !== ""){
                    var value = this.newTodoItem && this.newTodoItem.trim();
                    // localStorage.setItem(value, value) ์ญ์ 
                    this.$emit('inputTodo', value); //์ถ๊ฐ, ์ด๋ฒคํธ ์ ๋ฌํ  ๋ ํ  ์ผ ํ์คํธ ๊ฐ์ธ value๊ฐ์ฒด๋ฅผ ์ธ์ ๊ฐ์ผ๋ก ์ ๋ฌํ๋ค.
                }
            },
            clearInput(){
                this.newTodoItem = '';
            }
        }
    }
}
</script>
...

```

<br>

- ```App```์ปดํฌ๋ํธ์ addTodo() ๋ฉ์๋ ์ถ๊ฐ
  - ```TodoInput``` ์ปดํฌ๋ํธ์์  ```App```์ปดํฌ๋ํธ๋ก ์ด๋ฒคํธ๋ฅผ ๋ณด๋ด๋ฉด ```App```์ปดํฌ๋ํธ์ addTodo()๋ฉ์๋๋ฅผ ์คํํ๋ค. 
  - ์ธ์ ๊ฐ todoItem์ ```TodoInput```์ปดํฌ๋ํธ์์ ์ฌ๋ ค ๋ณด๋ธ ํ  ์ผ ํ์คํธ ๊ฐ์ด๋ค.
  - ์ด ๊ฐ(todoItem)์ ๋ก์ปฌ ์คํ ๋ฆฌ์ง์ ์ ์ฅํ๊ณ , ```APP```์ปดํฌ๋ํธ์ todoItems ๋ฐ์ดํฐ ์์ฑ์๋ ์ถ๊ฐํ๋ค.  
```vue
...
<script>
  export default{
    data(){
      return{
        todoItems: []  
      }
    },
    methods:{
      addTodo(todoItem){ 
          localStorage.setItem(todoItem,todoItem);
          this.todoItem.push(todoItem);
      }
    },
    components: {
      'TodoHeader' : TodoHeader,
      'TodoInput' : TodoInput,
      'TodoList' : TodoList,
      'TodoFooter' : TodoFooter
    }
}
</script>

...

```

<br>

- ```TodoList```์ปดํฌ๋ํธ ```<template>``` ๋ด์ฉ ์์ 
  - v-for ๋๋ ํฐ๋ธ์ ๋ฐ๋ณต ๋์์ porpsdata๋ก ๋ณ๊ฒฝ
  - ๊ธฐ์กด์๋ TodoList์ ๋ฐ์ดํฐ ์์ฑ์ธ datatItems ์์ง๋ง, ์ด์ ๋ ```App```์ปดํฌ๋ํธ์ todoItems๋ฐ์ดํฐ์ ๊ฐ์๋งํผ ๋ชฉ๋ก ์์ดํ์ ์์ฑํ๋ค.

```vue
  <template>
    <section>
        <ul>
            <li v-for= "(todoItem, index) in propsdata" :key="todoItem" class="shadow">
                <i class="checkBtn fa fa-check"></i>
                {{ todoItem }}
                <span class="removeBtn" type="button" v-on:click = "removeTodo(todoItem, index)">
                    <i class="fa fa-trash"></i>
                </span>
            </li>
        </ul>
    </section>
  </template> 
  
```
<br>

### 2-2. TodoList์์ ๋ถํ์ํ ์ฝ๋ ์ ๊ฑฐํ๊ธฐ
- ```TodoList```์ปดํฌ๋ํธ์์ ์ฌ์ฉํ๋ ๋ฐ์ดํฐ ์์ฑ todoItems๋ ๋ถํ์ํ๋ฏ๋ก ์ ๊ฑฐํ๋ค.
  - ```App```์ปดํฌ๋ํธ์ todoItems์์ propsdata๋ก ๋ฐ์ดํฐ๋ฅผ ์ ๋ฌํด์ฃผ๊ธฐ ๋๋ฌธ์
- created() ๋ก์ง๋ ```App```์ปดํฌ๋ํธ๋ก ์ฏ๊ฒจ์ค๋ค.
  - ํ  ์ผ ๋ฐ์ดํฐ(todoItems)๋ ๋ชจ๋ ```App```์ปดํฌ๋ํธ์์ ๊ด๋ฆฌํ๊ธฐ ๋๋ฌธ์   

```vue
...
<script>
export default{
  data() { //์ ๊ฑฐ
    return {
      todoItems : [] 
    }
  },
  props: ['porpsdata'],
  created() { // App.vue๋ก ์ด๋
    if(localStorage.length > 0){
      for(var i = 0; i < localStorage.length; i++){
        this.todoItems.push(localStorage.key(i));
      }
    }
  },
  
  methods: {
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    }
  }
}
</script>
...
```


<br>

## 3. ์ด๋ฒคํธ ์ ๋ฌ์ ์ด์ฉํด Clear All ๋ฒํผ ๊ธฐ๋ฅ ๊ฐ์ ํ๊ธฐ
- ์ปดํฌ๋ํธ ๊ฐ **์ด๋ฒคํธ ์ ๋ฌ** ๋ฐฉ์์ ์ฌ์ฉ
  - ์ด๋ฒคํธ ์ ๋ฌ : ํ์ ์ปดํฌ๋ํธ์์ ๋ฐ์์ํจ ์ด๋ฒคํธ๋ฅผ ์์ ์ปดํฌ๋ํธ์์ ๋ฐ์ ์์ ์ปดํฌ๋ํธ์ ๋งค์๋๋ฅผ ๋์์ํค๋ ๊ฒ
- ํ์ ์ปดํฌ๋ํธ ```TodoFooter```์์ ๋ฐ์์ํฌ ์ด๋ฒคํธ ์ด๋ฆ์ removeAll , ์์ ์ปดํฌ๋ํธ ```App```์์ ๋ฐ์ ์คํผ์ํฌ ๋งค์๋ ์ด๋ฆ์ clearAll() ์ค์ 

### 3-1. ์์ ์ปดํฌ๋ํธ App ์ฝ๋ ์์ ํ๊ธฐ

```vue
<template>
  <div id="app">
    ...
    <TodoFooter v-on:removeAll = "clearAll"></TodoFooter>
  </div>
</template>

<script>
  export default{
   ...
    methods:{
       ... 
      clearAll(){
        localStorage.clear(); // ๋ก์ปฌ ์คํ ๋ฆฌ์ง์ ๋ฐ์ดํฐ๋ฅผ ๋ชจ๋ ์ญ์ 
        this.todoItems = []; // todoItems์ ๋ฐ์ดํฐ๋ฅผ ๋น์
      },
    },
    ...
  }
</script>
...
```

### 3-2. ํ์ ์ปดํฌ๋ํธ ์ฝ๋ ์์ ํ๊ธฐ
```vue
<script>
export default{
    methods: {
        clearTodo(){
            // localStorage.clear(); ์ญ์ 
            this.$emit('removeAll');  //์ถ๊ฐ 
        },
    }
}
</script>
```

<br>

## 4. ์ด๋ฒคํธ ์ด์ฉํด ์ญ์  ๊ธฐ๋ฅ ๊ฐ์ ํ๊ธฐ
- ```todoList```์ปดํฌ๋ํธ์ ๊ฐ ํ  ์ผ ์์ดํ์ ์ญ์ ํ๋ ๋ก์ง์๋ **์ด๋ฒคํธ ์ ๋ฌ ๋ฐฉ์**์ ์ ์ฉํ๋ค.

#### App.vue
```vue
<template>
  <div id="app">
    ...
    <TodoList v-bind:propsdata = "todoItems" v-on:removeList = "clearList"></TodoList>
    ...
  </div>
</template>

<script>
  ...
  export default{
    ...
    methods:{
      ...
      clearList(todoItem, index){
        localStorage.removeItem(todoItem);
        this.todoItems.splice(index, 1); //splice() ๋ฉ์๋๋ ๋ฐฐ์ด์ ๊ธฐ์กด ์์๋ฅผ ์ญ์  ๋๋ ๊ต์ฒดํ๊ฑฐ๋ ์ ์์๋ฅผ ์ถ๊ฐํ์ฌ ๋ฐฐ์ด์ ๋ด์ฉ์ ๋ณ๊ฒฝ
      }
    },
   ...
  }
</script>
...
```
<br> 

#### TodoList.vue
- ํ  ์ผ ๋ชฉ๋ก์์ ์ญ์  ์์ด์ฝ์ ํด๋ฆญํ๋ฉด ```TodoList```์ปดํฌ๋ํธ์ removeTodo ๋ฉ์๋์์ removeList๋ผ๋ ์ด๋ฒคํธ๋ฅผ ๋ฐ์ ์์ผ ```App```์ปดํฌ๋ํธ๋ก ์ ๋ฌํ๋ค.
- ์ด๋ฒคํธ๋ฅผ ์ ๋ฌํ  ๋ ์ ํํ ํ  ์ผ์ ํ์คํธ(todoItem)์ ์์(index)๋ฅผ ๋ณด๋ธ๋ค.
- **์ด๋ฒคํธ๋ฅผ ์ ๋ฌํ  ๋ ์ธ์๋ฅผ ํ๊ป ์ ๋ฌ ํ  ์ ์๋ค.**

```vue
...
<script>
export default{
  ...
  methods: {
    removeTodo(todoItem, index) {
      // localStorage.removeItem(todoItem); App.vue clearList(todoItem, index) ๋ฉ์๋๋ก ์ด๋
      // this.todoItems.splice(index, 1); App.vue clearList(todoItem, index) ๋ฉ์๋๋ก ์ด๋
      this.$emit('removeList', todoItem, index); // ์ถ๊ฐ
    }
  }
}
</script>
...
```

<br>

![image](/img/todolist_final.gif)
