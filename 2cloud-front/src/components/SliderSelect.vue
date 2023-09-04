<template>
  <div>
    <el-select :placeholder="label" class="block-display" v-model="display">
      <el-option disabled :label="label" class="custom-disabled" value=""></el-option>
      <el-option disabled :value="year" class="custom-disabled" >
        <div>
          <el-input v-model="year[0]" class="year-input custom-disabled" disabled></el-input>
          &nbsp;&nbsp;
          <el-input v-model="year[1]" class="year-input custom-disabled" disabled></el-input>
        </div>
      </el-option>
      <el-option disabled :value="year" class="custom-disabled" >
        <div>
          <el-slider v-model="year" range :min="minBar" :max="maxBar"></el-slider>
        </div>
      </el-option>
    </el-select>
  </div>
</template>

<script>
export default {
  name: "SliderSelect",
  props: {
    label:'',
    minBar:'',
    maxBar:'',
  },
  computed:{
    display(){
      return `${this.year[0]}|${this.year[1]}`;
    }
  },
  data(){
    return {
      year:[0,0],
    }
  },
  mounted() {
    this.year[0] = this.minBar;
    this.year[1] = this.maxBar;
  }
}
</script>

<style scoped>
.year-input {
  width: 80px;
}
.custom-disabled {
  pointer-events: none;
  cursor: default;
}
</style>