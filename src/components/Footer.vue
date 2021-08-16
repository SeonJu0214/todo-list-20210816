<template>
  <div>
    <hr>
    <b-button variant="outline-danger" @click="clearTodo"
      class="clearBtn">전체 삭제</b-button>
  </div>
</template>

<script>
  export default {
    methods: {
      // 로컬 스토리지의 데이터를 모두 삭제
      clearTodo() {
        this.$emit('removeAll');
      }
    }
  }
</script>

<style scoped>
  hr {
    border: 1px solid #6E5F54;
  }

  .clearBtn {
    border: 1px solid #C9563A;
  }
</style>