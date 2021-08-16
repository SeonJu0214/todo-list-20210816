<template>
  <div class="input-group">
    <input type="text" class="form-control" v-model="newTodoItem" placeholder="Type what you have to do"
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
                newTodoItem: '',
            }
        },
        methods: {
            addTodo() {
                // Input 박스의 입력 값이 있을 때만 저장하기
                if (this.newTodoItem !== "") {
                    // Input 박스에 입력된 텍스트의 앞 뒤 공백 문자열 제거
                    var value = this.newTodoItem && this.newTodoItem.trim();
                    /*
                        [ Application → Local Storage → http://localhost:8080 ]
                        - Storage.setItem(key: string, value: string)
                         : 왼 쪽에 key, 오른쪽에 value 저장
                        localStorage.setItem(value, value);
                    */
                   /*
                        이벤트를 전달할 때 할 일 텍스트 값인 value 객체를 인자 값으로 전달
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
    .input-group-btn {
        background-color: #F3F2F1;
        border: 1px solid #FFCAC5;
        border-radius: 5px;
    }
</style>