<template>
  <div id="index">
    <b-container class="bv-example-row">
      <b-row class="text-center">
        <b-col></b-col>
        <b-col cols="8">
          <b-card class="card-main">
            <Header></Header>
            <Menu></Menu>

            <Input></Input>
            <br>
            <ul class="list-group">
              <li class="list-group-item">
                청소하기
              </li>
              <li class="list-group-item">
                청소하기
              </li>
              <li class="list-group-item">
                청소하기
              </li>
            </ul>
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

  export default {
    components: {
      'Header': Header,
      'Menu': Menu,
      'Input': Input
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
    background-color: #F9F8ED;
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
    border: 1px solid #7A6462;
  }
</style>