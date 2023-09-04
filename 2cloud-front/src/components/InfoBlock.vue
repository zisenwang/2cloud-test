<template>
    <div class="content">
      <div class="text">
        <div>
          <span class="title">{{title}}</span> {{description}}
        </div>
        <div class="detail">
          <el-tag type="info">{{saleCategory}}</el-tag>
          <el-tag type="info">{{addCommasToStringNumber(odometer)}} Kms</el-tag>
          <el-tag type="info">Sold in {{branch}}</el-tag>
          <el-image src="/img.png" style="max-width: 30px"></el-image>
          Excellent Condition
          <SmallCalendar :date="date"/>
        </div>
      </div>
      <div class="button">
        <el-button type="danger">Subscribe to Reveal Price</el-button>
        <el-button>See More</el-button>
      </div>
    </div>
</template>

<script>
import SmallCalendar from "./icons/SmallCalendar.vue";
export default {
  name: "InfoBlock",
  components: { SmallCalendar },
  props: {
    title:'',
    description:'',
    saleCategory:'',
    odometer:'',
    branch:'',
    date:'',
  },
  methods: {
    addCommasToStringNumber(str) {
      const number = parseFloat(str.replace(/,/g, ''));
      if (isNaN(number)) {
        return str;
      }
      return number.toLocaleString();
    }
  },

};
</script>

<style scoped>
.content {
  padding: 15px;
  background: #ffffff;
  border-radius: 5px;
  position:relative;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.text {
  display: flex;
  flex-direction: column;
  flex-grow: 1; /* 占据剩余空间 */
  margin-right: 20px; /* 添加一些间距 */
}

.title {
  font-weight: bold;
}

.detail {
  display: flex;
  align-items: center;
  gap: 8px; /* 添加项之间的间距 */
}

.button {
  display: flex;
  gap: 10px; /* 添加按钮之间的间距 */
}


</style>
