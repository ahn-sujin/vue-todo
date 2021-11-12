<template>
    <div class="inputBox shadow">
        <input type="text" v-model = "newTodoItem" placeholder="Type what you have to do" v-on: keyup.enter="addTodo">
        <!-- v-on:key.enter 인풋 박스에 enter를 눌렀을 때 동작하는 속성   -->
        <span class="addContainer" v-on:click= "addTodo"><i class="addBtn fa fa-plus" aria-hidden= "true"></i></span>
    </div>
</template>

<script>
    export default{
        data() {
            return{
                newTodoItem: ''
            }
        },
        methods: {
            addTodo(){
                // console.log(this.newTodoItem);
                // localStorage.setItem(this.newTodoItem, this.newTodoItem);
    
                // 1.  인풋 박스의 입력 값이 있을 때만 저장
                if (this.newTodoItem !== "") {
                    // 2. 인풋 박스에 입력된 텍스트의 앞뒤 공백 문자열 제거
                    var value = this.newTodoItem && this.newTodoItem.trim();
                    localStorage.setItem(value, value); //* setItem : 로컬 스토리지에 데이터를 추가하는 API (키 , 값) 형태로 저장
                    // 3. 인풋 박스의 입력 초기화
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