<template>
    <!-- 2. 뷰 데이터의 아이템 개수만큼 리스트 아이템 표시 -->
    <section>
        <ul>
            <li v-for= "(todoItem, index) in todoItems" :key="index" class="shadow">
                <i class="checkBtn fa fa-check" aria-hidden="true"></i>
                {{ todoItem }}
                <!-- @click은 v-on:click 과 동일하게 동작한다. -->
                <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
                    <i class="fa fa-trash" aria-hidden="true"></i>
                </span>
            </li>
        </ul>
    </section>
</template>

<script>    
    export default{
         // 1. 로컬 스토리지 데이터를 뷰 데이터에 저장
        data() {
            return {
                todoItems: []
            }
        },
        created() {
            if (localStorage.length > 0){
                for(var i = 0; i < localStorage.length; i++) {
                    this.todoItems.push(localStorage.key(i));
                }
            }
        },
        methods: {
            //3. 선택한 일을 뷰에서 인식하도록 만들기 
            removeTodo(todoItem, index) {
                // console.log(todoItem, index);
                // 4. 선택 한 일을 로컬 스토리지와 뷰 데이터에서 삭제하기
                localStorage.removeItem(todoItem);
                // * splice() :  배열의 특정 인덱스에서 부여한 숫자만큼의 인덱스를 삭제한다.
                this.todoItems.splice(index, 1);

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