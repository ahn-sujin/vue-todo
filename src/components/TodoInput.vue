<template>
    <div class="inputBox shadow">
        <!-- 
            * v-model  
            - 폼에서 주로 사용되는 속성, 폼에 입력한 값을 뷰 인스턴스의 데이터와 즉시 동기화 시켜준다. 
            - 화면에 입력된 값을 저장하여 서버에 보내거나 추가 로직을 수행 할 수 있다.
         -->
        <input type="text" v-model= "newTodoItem" placeholder="type what your have to do" @keyup.enter= "addTodo">  
        <span class="addContainer" v-on:click = "addTodo">
            <i class="addBtn fa fa-plus"></i>
        </span>
    </div>
</template>

<script>
    export default{
        // 데이터 속성 생성
        data(){
            return{
                newTodoItem: ''
            }
        },
        methods: {
            addTodo(){
                // console.log(this.newTodoItem);
                if(this.newTodoItem !== ""){ //인풋박스에 입력된 텍스트가 없을 경우 로컬 스토리지에 데이터가 저장되지 않도록 한다.
                    var value = this.newTodoItem && this.newTodoItem.trim(); //trim() : 문자열 좌우에서 공백을 제거하는 함수
                    this.$emit('inputTodo', value);
                    this.clearInput();
                }
            },
            clearInput(){
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