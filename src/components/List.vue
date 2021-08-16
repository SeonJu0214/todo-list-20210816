<template>
  <section>
    <transition-group name="list" tag="ul">
      <li v-for="(todoItem, index) in propsdata" :key="index">
        <i class="checkBtn fas fa-check" aria-hidden="true"></i>
        {{ todoItem }}
        <span class="removeBtn" type="button" @click="removeTodo(index)">
          <i class="far fa-trash-alt" aria-hidden="true"></i>
        </span>
      </li>
    </transition-group>
  </section>
</template>

<script>
  export default {
    props: ['propsdata'],
    methods: {
      removeTodo(index) {
        this.$emit('removeTodo', index);
      }
    }
  }
</script>

<style scoped>
  /* 뷰 애니메이션 속성 */
  .list-enter-active, .list-leave-active {
    transition: all ls;
  }

  .list-enter, .list-leave-to {
    opacity: 0;
    transform: translateY(30px);
  }
    
  ul {
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
  }

  li {
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
    border: 1px solid #E8D2BA;
  }

  .checkBtn {
    line-height: 45px;
    color: #6EA2C7;
    margin-right: 5px;
  }

  .removeBtn {
    margin-left: auto;
    color: #C9563A;
  }
</style>