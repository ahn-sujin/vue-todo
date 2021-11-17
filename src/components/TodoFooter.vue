<template>
    <div class="clearAllContainer">
        <span class="clearAllBtn" @click="clearTodo">Clear All</span>
    </div>
</template>

<script>
    export default{
        methods : {
            clearTodo(){
                // localStorage.clear();
                this.$emit('removeAll');
            }
        }
    }
</script>

<style>
    .clearAllContainer{
        width: 8.5rem;
        height: 50px;
        line-height: 50px;
        background: #fff;
        border-radius: 5px;
        margin: 40px auto 0;
    }

    .clearAllBtn{
        display: block;
        color: #e20303;
        cursor: pointer;
    }

</style>