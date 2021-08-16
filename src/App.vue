<template>
  <div id="index">
    <b-container class="bv-example-row">
      <b-row class="text-center">
        <b-col></b-col>
        <b-col cols="8">
          <b-card>
            <h2 class="title">TODO LIST</h2>
          <hr>
            <b-nav tabs fill>
              <b-nav-item active>
                +
              </b-nav-item>
              
              <b-nav-item>YEAR</b-nav-item>
              <b-nav-item>MONTH</b-nav-item>
              <b-nav-item>WEEK</b-nav-item>
              <b-nav-item>TODAY</b-nav-item>
            </b-nav>

          <b-card>
            
          </b-card>
          </b-card>
            
        </b-col>
        <b-col></b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {

}
</script>

<style>
  body {
    background-color: #F9F8ED;
  }

  #index {
    margin-top: 10px;
  }

  .title {
    color: #7A6462;
    font-weight: bold;
    text-shadow: 0px 1px #ffffff, 3px 3px 0px #dad7d7;
  }
</style>