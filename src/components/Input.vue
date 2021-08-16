<template>
  <div class="input-group">
    <input type="text" class="form-control" v-model="newTodoItem"
      v-on:keyup.enter="addTodo">
    <span class="input-group-btn" v-on:click="addTodo">
      <button class="btn btn-default" type="button">추가</button>
    </span>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        newTodoItem: ''
      }
    },
    methods: {
      addTodo() {
        // Input 박스의 입력 값이 있을 때만 저장하기
        if (this.newTodoItem !== "") {
        // Input 박스에 입력된 텍스트의 앞 뒤 공백 문자열 제거
        var value = this.newTodoItem && this.newTodoItem.trim();
        /*
          emit : 다른 컴포넌트에게 이벤트를 전달하기 위해 사용
          - ex. 자식 컴포넌트에서 사용자 지정 이벤트를 만들어 부모 컴포넌트에게
          전달할 수 있다. 부모 컴포넌트는 자식 컴포넌트에서 만들어진 사용자 지정
          이벤트를 받아 특정 동작을 수행할 수 있다.

          이벤트를 전달할 때 할 일 텍스트 값인 value 객체를 인자 값으로 전달

          ( 자식 컴포넌트 ) : Input.vue
          ( 부모 컴포넌트 ) : App.vue
        */
        this.$emit('addTodo', value);
        // Input 박스의 입력 값을 초기화
        this.clearInput();
        }
      },
      // Input 박스의 입력 값을 초기화 하기 위해 생성한 함수
      clearInput() {
        this.newTodoItem = '';
      }
    }
  }
</script>

<style scoped>
  input {
    border: 1px solid #E8D2BA;
  }

  .input-group-btn {
    background-color: #F3F2F1;
    border: 1px solid #E8D2BA;
    border-radius: 5px;
  }
</style>