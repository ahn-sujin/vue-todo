<template>
    <section>
        <ul>
            <!-- 
                v-for = "아이템명 in array"
                : 지정한 데이터의 갯수만큼 html을 출력 
             -->
            <li v-for= "todoItem in todoItems" :key= "todoItem">
                <i class="checkBtn fa fa-check"></i>
                {{ todoItem }}
                <span class="removeBtn" type="button" @click= "removeTodo(todoItem)">
                    <i class="fa fa-trash"></i>
                </span>
            </li>
        </ul>
    </section>
</template>

<script>
export default{
     // 데이터 속성 생성
    data(){
        return {
            todoItems: []
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
    methods: {
        removeTodo(todoItem){
            // console.log(todoItem);
            localStorage.removeItem(todoItem);
        }
    }
}    

</script>

<style>
    ul{
        list-style-type: none;
        padding-left: 0px;
        margin-top: 0;
        text-align: left;
    }
    li{
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: 0.5rem 0;
        padding: 0 0.9rem;
        background: #fff;
        border-radius: 5px;
    }
    .checkBtn{
        line-height: 45px;
        color: #62acde;
        margin-right:5px;
        cursor: pointer;
    }
    .removeBtn{
        line-height: 45px;
        margin-left: auto;
        color: #de4343;
        cursor: pointer;
    }
</style>