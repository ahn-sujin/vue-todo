### 📌컴포넌트 별 구현할 기능
```
   TodoHeader : 애플리케이션 이름 표시 
   TodoInput :  할 일 입력 및 추가
   TodoList :  할 일 목록 표시 및 특정 할 일 삭제
   TodoFooter: 할 일 모두 삭제
```


## 1. TodoHeader 컴포넌트
  ```vue
  <template>
    <header>
        <h1>TODO it!</h1>
    </header>
  </template>

  <script>
    export default{

    }
  </script>

  <style>
      h1{
          color: #2f3b52;
          font-weight: 900;
          margin: 2.5rem 0 1.5rem;
      }
  </style>
  ```
  ![image](/img/todoinput01.PNG)

<br>

## 2. TodoInput 컴포넌트
### 2-1. 인풋 박스와 버튼 추가하기

```vue

<template>
    <div class="inputBox shadow">
       <!-- 
            * v-model  
            - 폼에서 주로 사용되는 속성, 폼에 입력한 값을 뷰 인스턴스의 데이터와 즉시 동기화 시켜준다. 
            - 화면에 입력된 값을 저장하여 서버에 보내거나 추가 로직을 수행 할 수 있다.
        -->    
        <input type="text" v-model= "newTodoItem">  
        <button>추가</button>
    </div>
</template>

<script>
    export default{
        data(){
            return{
                newTodoItem: ''
            }
        },
    }
</script>
...

```
![image](/img/todoinput03.gif)

* 인풋박스에 텍스트를 입력하면 뷰 개발자도구 newTodoItem 값이 같이 갱신되는 것을 확인 할 수 있다.

<br>

### 2-2. 텍스트를 저장하기 위한 버튼 이벤트를 추가하기
```vue

<template>
    <div class="inputBox shadow">  
        <input type="text" v-model= "newTodoItem">  
        <button v-on:click = "addTodo">추가</button>
    </div>
</template>

<script>
    export default{
        data(){
            return{
                newTodoItem: ''
            }
        },
        methods : {
            addTodo(){
              console.log(this.newTodoItem);
            }
        }
    }
</script>
...

```
![image](/img/todoinput2.gif)

* 추가 버튼을 클릭했을 때 console창에 텍스트 값이 표시됨으로, 이벤트가 정상적으로 동작하는 것을 확인할 수 있다.

<br>

### 2-3. 입력받은 텍스트를 로컬 스토리지에 저장하기
* 입력받은 텍스트를 로컬 스토리지의 setItem() API를 이용하여 저장한다.
* setItem()은 로컬 스토리지에 데이터를 추가하는 API로, API형식은 키, 값 형태이다.
* 로컬 스토리지에 저장된 것은 [개발자도구] -> [Aplication] -> [Local Storage] -> http://localhost:8080] 을 클릭하여 확인 할 수 있다.

```vue
<template>
    <div class="inputBox shadow">  
        <input type="text" v-model= "newTodoItem">  
        <button v-on:click = "addTodo">추가</button>
    </div>
</template>

<script>
    export default{
        data(){
            return{
                newTodoItem: ''
            }
        },
        methods: {
            addTodo(){
              localStorage.setItem(this.newTodoItem, this.newTodoItem);
            }
        }
    }
</script>
...
```
![image](/img/todoinput04.PNG)

<br>

### 2-4. addTodo() 안에 예외 처리 코드 넣기
* 인풋 박스에 입력된 텍스트가 없을 경우 로컬 스토리지에 데이터가 저장되지 않도록 처리해준다.

```vue
<template>
    <div class="inputBox shadow">  
        <input type="text" v-model= "newTodoItem">  
        <button v-on:click = "addTodo">추가</button>
    </div>
</template>

<script>
    export default{
        data(){
            return{
                newTodoItem: ''
            }
        },
        methods: {
            addTodo(){
              // 1. 인풋 박스의 입력 값이 있을 때만 저장 
              if(this.newTodoItem !== ""){
                 // 2. 인풋박스에 입력된 텍스트의 앞뒤 공백 문자열 제거 
                 var value = this.newTodoItem && this.newTodoItem.trim();
                 localStorage.setItem(this.newTodoItem, this.newTodoItem);
                 //3. 인풋 박스의 입력 값 초기화
                 this.clearInput();
              } 
            },
            clearInput() {
              this.newTodoItem = '';
            }
        }
    }
</script>
...
```

<br>

### 2-5. 버튼 스타일 적용하기

```vue
<template>
    <div class="inputBox shadow">  
        <input type="text" v-model= "newTodoItem" placeholder="type what your have to do" @keyup.enter= "addTodo">  
        <span class="addContainer" v-on:click = "addTodo">
            <i class="addBtn fa fa-plus"></i>
        </span>
    </div>
</template>

<script>
    export default{
        data(){
            return{
                newTodoItem: ''
            }
        },
        methods: {
            addTodo(){
              // 1. 인풋 박스의 입력 값이 있을 때만 저장 
              if(this.newTodoItem !== ""){
                 // 2. 인풋박스에 입력된 텍스트의 앞뒤 공백 문자열 제거 
                 var value = this.newTodoItem && this.newTodoItem.trim();
                 localStorage.setItem(this.newTodoItem, this.newTodoItem);
                 //3. 인풋 박스의 입력 값 초기화
                 this.clearInput();
              } 
            },
            clearInput() {
              this.newTodoItem = '';
            }
        }
    }
</script>
<style>
    input:focus {
        outline: none;
    }
    .inputBox {
        background: #fff;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }
    .inputBox input {
        border-style: none;
        font-size: 0.9rem;
    }
    .addContainer {
        float:right;
        background: linear-gradient(to right, #6478fb, #8763fb);
        display: block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }
    .addBtn{
        color: #fff;
        vertical-align: middle;
    }
</style>
```
![image](/img/todoinput05.PNG)

<br>

## 3. TodoList 컴포넌트
### 3-1. 로컬 스토리지 데이터를 뷰 데이터에 저장하기
```vue
...
<script>
export default{
  //1. todoItems 데이터 속성을 빈 배열로 선언한다.
  data() {
    return {
      todoItems : [] 
    }
  },
  // 2. created 라이프사이클 훅에 for 반복문과 push()로 로컬 스토리지의 데이터를 todoItems에 담아준다. 
  created() {
    if(localStorage.length > 0){
      for(var i = 0, i < localStorage.length; i++){
        this.todoItems.push(localStorage.key(i));
      }
    }
  }
}
</script>
...
```
* 뷰의 인스턴스가 생성되자마자 뷰 데이터에 접근할 수 있도록 **eated() 라이프 사이클**에서 로컬 스토리지의 데이터를 뷰 데이터로 옮긴다.


### 3-2. 뷰 데이터의 아이템 개수만큼 화면에 표시하기

### 3-3. 할 일 목록 & 삭제 버튼 마크업 작업하기

### 3-4. 할 일 삭제 버튼에 클릭 이벤트 추가하기

### 3-5. 선택한 할 일을 뷰에서 인식하도록 만들기

### 3-6. 선택한 할 일을 로컬 스토리지와 뷰 데이터에서 삭제하기

<br>

## 4. TodoFooter 컴포넌트 
### 4-1. 모두 삭제하기 버튼 추가하기 






