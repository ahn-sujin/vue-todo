<template>
    <section>
        <ul>
            <!-- 
                v-for = "아이템명 in array"
                : 지정한 데이터의 갯수만큼 html을 출력 
             -->
            <li v-for= "(todoItem, index) in propsdata" :key="index" class="shadow">
                <i class="checkBtn fa fa-check"></i>
                {{ todoItem }}
                <span class="removeBtn" type="button" v-on:click= "removeTodo(todoItem, index)">
                    <i class="fa fa-trash"></i>
                </span>
            </li>
        </ul>
    </section>
</template>

<script>
export default{    
    //props 속성
    props : ['propsdata'],

    methods: {
        removeTodo(todoItem, index){
            // console.log(todoItem);
           this.$emit('removeList', todoItem, index);
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