<template>
  <div class="valuation-banner-main">
    <div>Need a Prices People Pay Valuation Report?</div>&nbsp;&nbsp;
    <el-button class="button"><span>&nbsp;Get One Now&nbsp;</span></el-button>
  </div>
</template>

<script>
export default {
  name: "ValuationBanner"
}
</script>

<style scoped>
.valuation-banner-main {
  display: flex;
  background-color: #ff5a60;
  align-items: center;
  padding: 5px;
  font-size: 14px;
  justify-content: center;
}

.main div {
  color: white;
  font-weight: 550;

}
.button {
  color: #ff5a60;
  border-radius: 20px;

}
.button span {
  font-weight: 550;
}
</style>