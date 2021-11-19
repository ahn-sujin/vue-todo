<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:inputTodo = "addTodo"></TodoInput>
    <TodoList v-bind:propsdata = "todoItems" v-on:removeList = "clearList"></TodoList>
    <TodoFooter v-on:removeAll = "clearAll"></TodoFooter>
  </div>
</template>

<script>
// import 불러올 파일의 내용이 담길 객체 from '불러올 파일 위치';
  import TodoHeader from './components/TodoHeader.vue'
  import TodoInput from './components/TodoInput.vue'
  import TodoList from './components/TodoList.vue'
  import TodoFooter from './components/TodoFooter.vue'

  export default{
    // 데이터 속성 
    data(){
      return{
        todoItems: []  
      }
    },
    methods:{
      addTodo(todoItem){ // 매서드 addTodo의 인자값 todoItem은 TodoInput컴포넌트에서 올려 보낸 할 일 텍스트 값
        localStorage.setItem(todoItem, todoItem);
        this.todoItems.push(todoItem);
      },
      clearAll(){
        localStorage.clear(); // 로컬 스토리지의 데이터를 모두 삭제
        this.todoItems = []; // todoItems의 데이터를 비움
      },
      clearList(todoItem, index){
        localStorage.removeItem(todoItem);
        this.todoItems.splice(index, 1); //splice() 메소드는 배열의 기존 요소를 삭제 또는 교체하거나 새 요소를 추가하여 배열의 내용을 변경
      }
    },
    // 로컬 스토리지 데이터를 뷰 데이터에 저장하는 코드
    created(){
        if(localStorage.length > 0){
            for(var i = 0; i < localStorage.length; i++){
                this.todoItems.push(localStorage.key(i));
            }
        }
    },
    components: {
      // '컴포넌트 태그 이름' : 컴포넌트 내용(불러올 파일의 내용이 담길 객체)
      'TodoHeader' : TodoHeader,
      'TodoInput' : TodoInput,
      'TodoList' : TodoList,
      'TodoFooter' : TodoFooter
    }
  }
</script>

<style>
  body{
    text-align: center;
    background-color: #f6f6f8;
  }
  input{
    border-style: groove;
    width: 200px;
  }
  button{
    border-style: groove;
  }
  .shadow{
    box-shadow: 5px 10px 10px rgba(0,0,0,0.3);
  }
</style>