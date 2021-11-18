<template>
    <!-- 2. 뷰 데이터의 아이템 개수만큼 리스트 아이템 표시 -->
    <section>
        <ul>
            <li v-for= "(todoItem, index) in propsdata" :key="index" class="shadow">
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
        // + 추가
        props : ['propsdata'],
        
        methods: {
            //3. 선택한 일을 뷰에서 인식하도록 만들기 
            removeTodo(todoItem, index) {
                // console.log(todoItem, index);
                this.$emit('removeTodo', todoItem, index)
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