<template>
  <div>
    <InfoBlock v-for="car in res"
               :title="`${car.Make} ${car.Model} ${car.YearGroup}` "
               :description="car.Description"
               :odometer="car.Odometer"
               :sale-category="car.SaleCategory"
               :branch="car.Branch"
               :date="car.Sold_Date"/>
  </div>
  <div class="load-more">
    <el-button type="primary" v-if="hasMore" size="large" @click="loadMore">Load More</el-button>
  </div>
</template>

<script>
import InfoBlock from "../components/InfoBlock.vue";
import data from "../data/data.json";

export default {
  name: "Search",
  components: { InfoBlock },
  data() {
    return {
      allRes: [],
      res: [],
      size: 3,
      hasMore:false,
    };
  },
  mounted() {
    this.queryAndSliceResults();
  },
  methods: {
    loadMore(){
      console.log('in')
      let newPage = parseInt(this.$route.query.page) + 1;
      let newQuery = Object.assign({}, this.$route.query);
      newQuery.page = newPage;
      this.$router.push({
        name:'search',
        query: newQuery
      })
    },
    queryAndSliceResults() {
      const size = this.size;
      const params = this.$route.query;
      this.query(params);
      console.log(this.allRes);
      let temp = JSON.parse(JSON.stringify(this.allRes));
      console.log("temp",temp);
      this.res = temp.slice(0, size * params.page);
      console.log(this.res);
      this.hasMore = params.page * this.size < this.allRes.length

      console.log(this.hasMore)
    },
    query(params) {
      let res = [];

      console.log('处理query',params);
      for (let i in data) {
        if (params.make !== undefined && data[i].Make !== params.make) {
          console.log(data[i].Make)
          continue;
        }
        if (params.family !== undefined && data[i].Model !== params.family) {
          continue;
        }
        if (params.badges !== undefined && data[i].BadgeDescription !== params.badges) {
          continue;
        }
        res.push(data[i]);
      }
      console.log("res时",res)
      this.allRes = res;
    },
  },
  beforeRouteUpdate(to, from, next) {
    this.queryAndSliceResults();
    next();

  },
};
</script>

<style scoped>
.load-more {
  margin: 20px;
  display: flex;
  align-items: center;
  justify-content: center;

}
</style>