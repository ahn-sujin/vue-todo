## 📝목차 

### [1. 문제 해결을 위한 애플리케이션 구조 개선](#1-문제-해결을-위한-애플리케이션-구조-개선)

### [2. props와 이벤트 전달을 이용해 할 일 입력 기능 개선하기](#2-props와-이벤트-전달을-이용해-할-일-입력-기능-개선하기)

### [3. 이벤트 전달을 이용해 Clear All 버튼 기능 개선하기](#3-이벤트-전달을-이용해-Clear-All-버튼-기능-개선하기)

### [4. 이벤트 이용해 삭제 기능 개선하기](#4-이벤트-이용해-삭제-기능-개선하기)


<br><br>

### 📌현재 애플리케이션 구조의 문제점
```
- 할 일을 입력했을 때, 할 일 목록에 바로 반영되지 않음
- 할 일을 모두 삭제했을 때, 할일 목록에 바로 반영되지 않음
```


<br>

## 1. 문제 해결을 위한 애플리케이션 구조 개선

![image](/img/vue04-1-1.png)

- 원인
  - 화면을 4개의 영역(```TodoHeader``` ```TodoInput``` ```TodoList``` ```TodoFooter```)으로 분리해 놓았기 때문에 한 영역의 처리 결과를 다른 영역에서 감지하지 못한다.

![image](/img/vue04-2.png)

- 해결방법 
  - 현재 애플리케이션은 각각의 컴포넌트에서만 사용할 수 있는 뷰 데이터 속성을 갖고 있다.
  
    (```TodoInput```-newTodoItem, ```TodoList```-todoItems)
    
  - 로컬 스토리지, ```TodoInput```, ```TodoList```는 모두 todoItems라는 같은 성격의 데이터를 사용하고 있다.
  - **최상위 컴포넌트인 ```App``` 컴포넌트에 todoItems 라는 데이터를 정의하고 하위 컴포넌트 ```TodoList```에 Props로 전달한다.**
 
- 달라진 점
  - 할 일 데이터 추가, 삭제를 모두 하위 컴포넌트 ```TodoInput```, ```TodoList```에서 했었다면, 
  - 뷰 데이터 속성 todoItems와 로컬 스토리지의 **데이터 조회, 추가, 삭제**를 모두 **```App```컴포넌트**에서 한다.
  - **하위 컴포넌트들**은 **이벤트 발생만** 실행한다. 
  

<br>

## 2. props와 이벤트 전달을 이용해 할 일 입력 기능 개선하기
1) 최상위 컴포넌트인 ```App```에 데이터 속성 todoItems를 선언한다.
2) 선언한 todoItems 속성을 ```TodoList```컴포넌트에 props로 전달한다.
3) ```TodoInput```컴포넌트 태그에 할일 추가 버튼을 클릭했을 때 ```App```컴포넌트로 이벤트를 전달 할 수 있게 v-on 디렉티브를 추가한다.
4) 해당 이벤트를 받아서 실행할 메서드도 추가한다.

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
          // 로컬스토리지에 데이터를 추가하는 로직
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

### 2-1. TodoInput 컴포넌트와 TodoList 컴포넌트 수정하기
- ```TodoInput```컴포넌트의 addTodo() 메서드 추가 
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
                    // localStorage.setItem(value, value) 삭제
                    this.$emit('inputTodo', value); //추가, 이벤트 전달할 때 할 일 텍스트 값인 value객체를 인자 값으로 전달한다.
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

- ```App```컴포넌트의 addTodo() 메서드 추가
  - ```TodoInput``` 컴포넌트에서  ```App```컴포넌트로 이벤트를 보내면 ```App```컴포넌트의 addTodo()메서드를 실행한다. 
  - 인자 값 todoItem은 ```TodoInput````컴포넌트에서 올려 보낸 할 일 텍스트 값이다.
  - 이 값(todoItem)을 로컬 스토리지에 저장하고, ```APP```컴포넌트의 todoItems 데이터 속성에도 추가한다.  
```vue
...
<script>
  export default{
    data(){
      return{
        todoItems: []  
      }
    },
    porps: ['propsdata'],
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

- ```TodoList```컴포넌트 ```<template>``` 내용 수정
  - v-for 디렉티브의 반복 대상을 porpsdata로 변경
  - 기존에는 TodoList의 데이터 속성인 datatItems 였지만, 이제는 ```App```컴포넌트의 todoItems데이터의 개수만큼 목록 아이템을 생성한다.

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

### 2-2. TodoList에서 불필요한 코드 제거하기
- ```TodoList```컴포넌트에서 사용하던 데이터 속성 todoItems는 불필요하므로 제거한다.
  - ```App```컴포넌트의 todoItems에서 propsdata로 데이터를 전달해주기 때문에
- created() 로직도 ```App```컴포넌트로 옯겨준다.
  - 할 일 데이터(todoItems)는 모두 ```App```컴포넌트에서 관리하기 때문에   

```vue
...
<script>
export default{
  data() { //제거
    return {
      todoItems : [] 
    }
  },
  
  created() { // App.vue로 이동
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

## 3. 이벤트 전달을 이용해 Clear All 버튼 기능 개선하기
- 컴포넌트 간 **이벤트 전달** 방식을 사용
  - 이벤트 전달 : 하위 컴포넌트에서 발생시킨 이벤트를 상위 컴포넌트에서 받아 상위 컴포넌트의 매서드를 동작시키는 것
- 하위 컴포넌트 ```TodoFooter```에서 발생시킬 이벤트 이름을 removeAll , 상위 컴포넌트 ```App```에서 받아 실핼시킬 매서드 이름을 clearAll() 설정

### 3-1. 상위 컴포넌트 App 코드 수정하기

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
        localStorage.clear(); // 로컬 스토리지의 데이터를 모두 삭제
        this.todoItems = []; // todoItems의 데이터를 비움
      },
    },
    ...
  }
</script>
...
```

### 3-2. 하위 컴포넌트 코드 수정하기
```vue
<script>
export default{
    methods: {
        clearTodo(){
            // localStorage.clear(); 삭제
            this.$emit('removeAll');  //추가 
        },
    }
}
</script>
```

<br>

## 4. 이벤트 이용해 삭제 기능 개선하기
- ```todoList```컴포넌트의 각 할 일 아이템을 삭제하는 로직에도 **이벤트 전달 방식**을 적용한다.

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
        this.todoItems.splice(index, 1); //splice() 메소드는 배열의 기존 요소를 삭제 또는 교체하거나 새 요소를 추가하여 배열의 내용을 변경
      }
    },
   ...
  }
</script>
...
```
<br> 

#### TodoList.vue
- 할 일 목록에서 삭제 아이콘을 클릭하면 ```TodoList```컴포넌트의 removeTodo 메서드에서 removeList라는 이벤트를 발생 시켜 ```App```컴포넌트로 전달한다.
- 이벤트를 전달할 때 선택한 할 일의 텍스트(todoItem)와 순서(index)를 보낸다.
- **이벤트를 전달할 때 인자를 한께 전달 할 수 있다.**

```vue
...
<script>
export default{
  ...
  methods: {
    removeTodo(todoItem, index) {
      // localStorage.removeItem(todoItem); App.vue clearList(todoItem, index) 메소드로 이동
      // this.todoItems.splice(index, 1); App.vue clearList(todoItem, index) 메소드로 이동
      this.$emit('removeList', todoItem, index); // 추가
    }
  }
}
</script>
...
```

<br>

![image](/img/todolist_final.gif)
