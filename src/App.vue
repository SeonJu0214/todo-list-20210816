<template>
  <div id="index">
    <b-container class="bv-example-row">
      <b-row class="text-center">
        <b-col></b-col>
        <b-col cols="8">
          <b-card class="card-main">
            <Header></Header>
            <Menu></Menu>
            <Input v-on:addTodo="addTodo"></Input>
            <List v-bind:propsdata="todoItems" @removeTodo="removeTodo"></List>
            <Footer v-on:removeAll="clearAll"></Footer>
          </b-card>
        </b-col>
        <b-col></b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
  import Header from './components/Header.vue'
  import Menu from './components/Menu.vue'
  import Input from './components/Input.vue'
  import List from './components/List.vue'
  import Footer from './components/Footer.vue'

  export default {
    props: ['propsdata'],
    data() {
      return {
        // 데이터 속성 todoItems 선언
        todoItems: []
      }
    },
    created() {
      // localStorage에 저장된 데이터가 한 개라도 있는 경우
      if (localStorage.length > 0) {
        /*
            localStorage에 저장된 모든 아이템을 한 번에 불러오는
            API는 없기 때문에 반복문으로 아이템을 모두 불러와야 한다.
        */
        for (var i = 0; i < localStorage.length; i++) {
            // push() : 배열의 끝 요소에 배열 아이템을 하나씩 추가하는 자바스크립트 내장 API
            var key = localStorage.key(i);

            if (localStorage.key(i) != "loglevel:webpack-dev-server") {
              this.todoItems.push(localStorage.getItem(key));
            }
        }
      }
    },
    methods: {
      addTodo(todoItem) {
        /*
          로컬 스토리지에 데이터를 추가하는 로직
           - todoItem : TodoInput 컴포넌트에서 올려 보낸 할 일 텍스트 값
           - 이 값을 로컬 스토리지에 저장하고, App 컴포넌트의 todoItems 데이터 속성에도 추가
           ( 뷰 데이터 )

          [ Application → Local Storage → http://localhost:8080 ]
           - Storage.setItem(key: string, value: string)
           : 왼 쪽에 key, 오른쪽에 value 저장
           localStorage.setItem(key, value);
        */
        var length = this.todoItems.length;

        localStorage.setItem(length, todoItem);
        this.todoItems.push(todoItem);
      },
      clearAll() {
        localStorage.clear();
        this.todoItems = [];
      },
      removeTodo(index) {
        // 로컬 스토리지의 데이터를 삭제
        var key = localStorage.key(index);
        localStorage.removeItem(key);
        /*
            splice() : 배열의 특정 인덱스를 삭제하는 API
            할 일 삭제 처리
        */
        this.todoItems.splice(index, 1);
      }
    },
    components: {
      'Header': Header,
      'Menu': Menu,
      'Input': Input,
      'List': List,
      'Footer': Footer
    }
  }
</script>

<style>
  @font-face {
    font-family: 'JSDongkang-Bold';
    src: url('https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_2001@1.1/JSDongkang-BoldA1.woff') format('woff');
    font-weight: normal;
    font-style: normal;
  }

  body {
    background-color: #E8DECC;
  }

  div, input {
    font-family: 'JSDongkang-Bold';
  }

  #index {
    margin-top: 10px;
  }

  /* 그림자 정의 */
  .shadow {
    box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.3);
  }

  .card-main {
    border: 1px solid #6E5F54;
    border-radius: 10px;
  }
</style>