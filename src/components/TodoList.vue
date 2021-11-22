<template>
    <section>
        <!-- 
          - transition-group 은 목록에 애니메이션을 추가할 때 사용되는 태그  
          - tag 속성에 html 태그 이름을 지정
          - name 속성은 css 클래스와 연관
        -->
        <transition-group name="list" tag="ul">
            <!-- 
                v-for = "아이템명 in array"
                : 지정한 데이터의 갯수만큼 html을 출력 
             -->
            <li v-for= "(todoItem, index) in propsdata" :key="todoItem" class="shadow">
                <i class="checkBtn fa fa-check"></i>
                {{ todoItem }}
                <span class="removeBtn" type="button" v-on:click= "removeTodo(todoItem, index)">
                    <i class="fa fa-trash"></i>
                </span>
            </li>
        </transition-group>
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
    /* 
      앞에서 설정한 name 속성 값(list)을 접두사로 두고,
      enter-active , leave-active, enter, leave-to 로 동작을 정의 
      (자세한 내용은 뷰 애니메이션 클래스 공식 문서 참고) 
    */
    .list-enter-active,
    .list-leave-active{
      transition: all 1s;
    }
    .list-enter, 
    .list-leave-to{
      opacity: 0;
      transform: translateY(30px);
    }
</style>