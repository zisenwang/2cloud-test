<template>
  <div class="filter" v-loading="loadingSub">
    <el-row :gutter="10">
      <el-col :span="3">
        <el-select v-model="make"
                   placeholder="Make">
          <el-option disabled
                     value=""
                     class="custom-disabled">Make</el-option>
          <el-option value="Chrysler">Chrysler</el-option>
          <el-option value="Volkswagen">Volkswagen</el-option>
          <el-option value="Volvo">Volvo</el-option>
        </el-select>
      </el-col>
      <el-col :span="3">
        <el-select v-model="family"
                   placeholder="Family"
                   :loading="loadingFamily">
          <el-option disabled
                     value=""
                     class="custom-disabled">Family</el-option>
          <el-option v-for="family in familySet"
                     :key="family"
                     :value="family"
                     :label="family"></el-option>
        </el-select>
      </el-col>
      <el-col :span="3">
        <SliderSelect label="Year" :min-bar="minYearBar" :max-bar="maxYearBar" />
      </el-col>
      <el-col :span="3">
        <el-select placeholder="Badges" v-model="badges" :loading="loadingSub">
          <el-option value="">Badges</el-option>
          <el-option v-for="i in badgesSet"
                     :key="i"
                     :value="i"
                     :label="i"></el-option>
        </el-select>
      </el-col>
      <el-col :span="3">
        <el-select placeholder="Body Type" v-model="bodyType" :loading="loadingSub">
          <el-option value="">Body Type</el-option>
          <el-option v-for="i in bodyTypeSet"
                     :key="i"
                     :value="i"
                     :label="i"></el-option>
        </el-select>
      </el-col>
      <el-col :span="3">
        <el-select placeholder="Body Type Config" v-model="bodyTypeConfig" :loading="loadingSub">
          <el-option value="">Body Type Config</el-option>
          <el-option v-for="i in bodyTypeConfigSet"
                     :key="i"
                     :value="i"
                     :label="i"></el-option>
        </el-select>
      </el-col>
      <el-col :span="3">
        <el-select placeholder="Fuel Type" v-model="fuelType" :loading="loadingSub">
          <el-option value="">Fuel Type</el-option>
          <el-option v-for="i in fuelTypeSet"
                     :key="i"
                     :value="i"
                     :label="i"></el-option>
        </el-select>
      </el-col>
    </el-row>
    <el-row :gutter="10">
      <el-col :span="3">
        <el-select placeholder="Transmission" v-model="transmission" :loading="loadingSub">
          <el-option value="">Transmission</el-option>
          <el-option v-for="i in transmissionSet"
                     :key="i"
                     :value="i"
                     :label="i"></el-option>
        </el-select>
      </el-col>
      <el-col :span="3">
        <el-select placeholder="Engine" v-model="engine" :loading="loadingSub">
          <el-option value="">Engine</el-option>
          <el-option v-for="i in engineSet"
                     :key="i"
                     :value="i"
                     :label="i"></el-option>
        </el-select>
      </el-col>
      <el-col :span="3">
        <el-select placeholder="Cylinders" v-model="cylinders" :loading="loadingSub">
          <el-option value="">Cylinders</el-option>
          <el-option v-for="i in cylindersSet"
                     :key="i"
                     :value="i"
                     :label="i"></el-option>
        </el-select>
      </el-col>
      <el-col :span="3">
        <el-select placeholder="Division" v-model="division" :loading="loadingSub">
          <el-option value="">Division</el-option>
          <el-option v-for="i in divisionSet"
                     :key="i"
                     :value="i"
                     :label="i"></el-option>
        </el-select>
      </el-col>
      <el-col :span="3">
        <el-select placeholder="Drive" v-model="drive" :loading="loadingSub">
          <el-option value="">Drive</el-option>
          <el-option v-for="i in driveSet"
                     :key="i"
                     :value="i"
                     :label="i"></el-option>
        </el-select>
      </el-col>
      <el-col :span="3">
        <el-select placeholder="Seat" v-model="seat" :loading="loadingSub">
          <el-option value="">Seat</el-option>
          <el-option v-for="i in seatSet"
                     :key="i"
                     :value="i"
                     :label="i"></el-option>
        </el-select>
      </el-col>
      <el-col :span="3">
        <el-select placeholder="Doors" v-model="doors" :loading="loadingSub">
          <el-option value="">Doors</el-option>
          <el-option v-for="i in doorsSet"
                     :key="i"
                     :value="i"
                     :label="i"></el-option>
        </el-select>
      </el-col>
    </el-row>
    <el-row :gutter="10">
      <el-col :span="3">
        <SliderSelect v-model="odometer" label="Odometer" :min-bar="0" :max-bar="100000" />
      </el-col>
      <el-col :span="3">
        <el-select placeholder="States" v-model="states" :loading="loadingSub">
          <el-option value="">States</el-option>
          <el-option value="NSW">NSW</el-option>
          <el-option value="QLD">QLD</el-option>
          <el-option value="SA">SA</el-option>
          <el-option value="TAS">TAS</el-option>
          <el-option value="VIC">VIC</el-option>
          <el-option value="WA">WA</el-option>
          <el-option value="ACT">ACT</el-option>
          <el-option value="NT">NT</el-option>
        </el-select>
      </el-col>
      <el-col :span="3">
        <el-select placeholder="Sale Category" v-model="saleCategory" :loading="loadingSub">
          <el-option value="">Sale Category</el-option>
          <el-option v-for="i in saleCategorySet"
                     :key="i"
                     :value="i"
                     :label="i"></el-option>
        </el-select>
      </el-col>
      <el-col :span="3">
        <el-select>123</el-select>
      </el-col>
      <el-col :span="3">
        <el-select placeholder="Sort" v-model="sort">
          <el-option value="" disabled class="custom-disabled">Sort</el-option>
          <el-option value="Sort | Sale Date">Sale Date</el-option>
          <el-option value="Sort | Age">Age</el-option>
          <el-option value="Sort | Odometer">Odometer</el-option>
        </el-select>
      </el-col>
      <el-col :span="3">
        <el-select placeholder="Order By" v-model="orderBy">
          <el-option value="" disabled class="custom-disabled">Order By</el-option>
          <el-option value="Order By | Asc">Asc</el-option>
          <el-option value="Order By | Desc">Desc</el-option>
        </el-select>
      </el-col>
    </el-row>
    <el-row>
      <el-col :span="9">
        <el-input
            placeholder="e.g. Metallic Paint,Power front seats,Power Sunroof,..."
            v-model="input"
        />
      </el-col>
      &nbsp;&nbsp;
      <el-button type="primary" @click="this.goToSearch">Apply Filter</el-button>
      <el-button type="primary">Clear Filter</el-button>
      <el-button type="danger">Subscribe to Generate Summary Report</el-button>
    </el-row>
  </div>
</template>

<script>
import data from '../data/data.json';
import SliderSelect from "./SliderSelect.vue";
export default {
  name: "Filter",
  components: {SliderSelect},
  data(){
    return{
      make:'',
      family:'',
      year:[2000,2010],
      minYearBar:1960,
      maxYearBar:2023,
      badges:'',
      bodyType:'',
      bodyTypeConfig:'',
      fuelType:'',
      transmission:'',
      engine:'',
      cylinders:'',
      division:'',
      drive:'',
      seat:'',
      doors:'',
      odometer:[0,100000],
      states:'',
      saleCategory:'',
      saleDate:'',
      sort:'Sort | Sale Date',
      orderBy:'Order By | Asc',
      input:'',
      loadingFamily:false,
      familySet:new Set(),
      badgesSet:new Set(),
      bodyTypeSet:new Set(),
      bodyTypeConfigSet:new Set(),
      fuelTypeSet:new Set(),
      transmissionSet:new Set(),
      engineSet:new Set(),
      cylindersSet:new Set(),
      divisionSet:new Set(),
      driveSet:new Set(),
      seatSet:new Set(),
      doorsSet:new Set(),
      statesSet:new Set(),
      saleCategorySet:new Set(),
      saleDateSet:new Set(),
      loadingSub:false,
    }
  },
  watch: {

    make(newVal) {
      console.log(newVal);
      this.family = '';
      this.familySet.clear();
      this.getFamily();
    },
    family(newVal) {
      this.loadingSub = true;
      console.log(newVal);

      setTimeout(()=>{
        this.getSub("BadgeDescription",this.badgesSet);
        this.getSub("BodyStyleDescription",this.bodyTypeSet);
        this.getSub("FuelTypeDescription",this.fuelTypeSet);
        this.getSub("GearTypeDescription",this.transmissionSet);
        this.getSub("EngineDescription",this.engineSet);
        this.getSub("GearNum",this.cylindersSet);
        this.getSub("Division",this.divisionSet);
        this.getSub("drivedescription",this.driveSet);
        this.getSub("Branch",this.statesSet);
        this.getSub("SaleCategory",this.saleCategorySet);
        this.loadingSub = false;
        },1000
      );
    }
  },
  methods:{
    getFamily(){
      this.loadingFamily = true;
      for (let i in data){
        if (data[i]["Make"] === this.make) this.familySet.add(data[i]["Model"])
      }
      this.loadingFamily = false;
    },
    getSub(attr,set){
      set.clear();
      for (let i in data){
        if (data[i]["Make"] === this.make && data[i]["Model"] === this.family) {
          set.add(data[i][attr] === null ? '(Blank)': data[i][attr]);
        }
      }
    },
    goToSearch(){
      this.$router.push({
        name:'search',
        query:{
          make : this.make,
          family : this.family,
          min_year : this.year[0],
          max_year : this.year[1],
          page : 1,
          badge : this.badge,
          body_type : this.bodyType,
          body_type_config : this.body_type_config,
          fuel_type : this.fuel_type,
          transmission : this.transmission,
          engine :this.engine,
          cylinders : this.cylinders,
          division: this.division,
          drive : this.drive,
          seat : this.seat,
          input : this.input,
        }
      })
    },
    clear(){

    }
  }
}
</script>

<style scoped>
.custom-disabled {
  cursor: default;
}
.block-display div {
  display: block;
}
</style>