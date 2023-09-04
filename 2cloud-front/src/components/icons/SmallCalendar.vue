<template>
  <div class="small-calendar-main">
    <div class="icon-container">
      <svg id="event-24px" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
        <path id="Path_14" data-name="Path 14" d="M17,12H12v5h5ZM16,1V3H8V1H6V3H5A1.991,1.991,0,0,0,3.01,5L3,19a2,2,0,0,0,2,2H19a2.006,2.006,0,0,0,2-2V5a2.006,2.006,0,0,0-2-2H18V1Zm3,18H5V8H19Z" fill="#0098dc"></path>
      </svg>
    </div>
    Sold<span class="sold-date">&nbsp;&nbsp;{{formatDateToMonthYear(date)}}</span>
  </div>
</template>

<script>
export default {
  name: "SmallCalendar",
  props:{
    date:''
  },
  methods: {
    formatDateToMonthYear(dateString) {
      const options = {year: 'numeric', month: 'short'};
      const date = new Date(dateString);
      return date.toLocaleDateString('en-US', options);
    }
  }
}
</script>

<style scoped>
.small-calendar-main {
  display: flex;
  align-items: center;
  font-size: 12px;
  font-family: Inter, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif;
}

.icon-container {
  align-items: center;
  padding-top: 5px;
  margin-right: 8px;
}

.sold-date {
  font-weight: bold;
}

</style>