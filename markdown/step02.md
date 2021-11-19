# 1. 컴포넌트 생성
- 프로젝트 폴더에 `src` 밑에 `components` 폴더를 생성하고 그 아래에 `TodoHeader.vue` `TodoInput.vue` `TodoList.vue` `TodoFooter.vue`를 생성한다.
- 컴포넌트 같은 경우 관례상 src/components 폴더에서 관리를 한다. (폴더 관리, 추후 재활용 접근에 용이)
- 애플리케이션의 규모가 커질 경우 `components/기능/컴포넌트.vue` 와 같은 형싱으로 관리 (기능별로 폴더 나누기)

[이미지 첨부]

> 컴포넌트 코드 구조
```vue

<template>
    <!-- html 입력 -->
</template>

<script>
export default{
  
}

</script>

<style>
  /* css 입력 */
</style>

```
<br>

# 2. 컴포넌트 등록
- 앞에서 생성한 4개의 컴포넌트를 등록하여 화면에 나타낼 수 있도록 등록한다.

  > 지역 컴포넌트 등록 방법 
  ```vue
  component: {
    '컴포넌트 이름' : 컴포넌트 내용
  }
  ```
  <br>

  > 특정 컴포넌트에서 다른 위치에 있는 컴포넌트의 내용을 불러 오는 방법
  ```vue
  import 불러온 파일의 내용이 담길 객체 from `불러올 파일 위치`;
  ```
  
* App.vue

```vue
<template>
  <div id="app">
     <!-- 등록한 컴포넌트 4개를 HTML에 표시 -->
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
  // 컴포넌트 내용 불러오기;
  import TodoHeader from './components/TodoHeader.vue'
  import TodoInput from './components/TodoInput.vue'
  import TodoList from './components/TodoList.vue'
  import TodoFooter from './components/TodoFooter.vue'

  export default{
    components: {
      // 지역 컴포넌트 등록
      'TodoHeader' : TodoHeader,
      'TodoInput' : TodoInput,
      'TodoList' : TodoList,
      'TodoFooter' : TodoFooter
    }
  }
</script>
....

```

[이미지 첨부]

