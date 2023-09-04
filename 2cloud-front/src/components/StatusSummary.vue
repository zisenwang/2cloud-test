<template>
  <div class="status-summary-main">
    <div class="title">
      {{title}} Status
    </div>
    <div class="content">
      A: 123 B: 1234
    </div>
  </div>
</template>

<script>
export default {
  name: "StatusSummary",
  props:{
    title:'',
  },
  data(){
    return{
    }
  }
}
</script>

<style scoped>
  .status-summary-main {
    display: flex;
    margin-top: 10px;
    margin-bottom: 10px;
    background: white;
  }
  .title {
    background-color: #00a0df;
    color: white;
    padding:10px 15px;
  }
</style>