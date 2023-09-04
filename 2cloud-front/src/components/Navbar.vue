<template>
  <nav class="navbar">
    <div class="inner">
      <div class="navbar-logo">
        <PricesPeopleSayIcon />
      </div>
      <div class="navbar-menu" :class="{ 'collapsed': menuCollapsed }">
        <div v-for="item in menuItems" :key="item.id" class="navbar-menu-item">{{ item.text }}</div>
        <el-button type="danger" class="navbar-menu-item navbar-menu-item-last">Sign In</el-button>
      </div>
    </div>

  </nav>
</template>

<script>
import PricesPeopleSayIcon from "./icons/PricesPeopleSayIcon.vue";
export default {
  components: {PricesPeopleSayIcon},
  data() {
    return {
      menuItems: [
        { id: 1, text: "About" },
        { id: 2, text: "Pricing" },
        { id: 3, text: "Search" },
        { id: 4, text: "Car2Cash" },
        { id: 5, text: "Valuations" },
        { id: 6, text: "Blog" },
        { id: 7, text: "Contact us" },
      ],
      menuCollapsed: false
    };
  },
  methods: {
    toggleMenu() {
      this.menuCollapsed = !this.menuCollapsed;
    }
  }
};
</script>

<style>
.navbar {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  padding-top: 20px;
  padding-bottom: 20px;
  background-color: white;
  box-shadow: 0 0 15px #6372824d;
}

.navbar-logo {
  font-size: 24px;
  width: 273px;
  height: 66px;
}

.inner {
  width: 1400px;
  padding-right: 10px;
  padding-left: 10px;
  margin-right: auto;
  margin-left: auto;
  display: flex;
  justify-content: space-between!important;
  align-items: center;
}
.navbar-menu {
  display: flex;
  align-items: center;
}

.navbar-menu-item {
  margin-right: 20px;
  cursor: pointer;
}

.navbar-menu-item.has-submenu {
  position: relative;
}


.navbar-menu-item.has-submenu:hover .submenu {
  display: block;
}

.navbar-menu-item-last {
  margin-right: 0;
}
@media (max-width: 768px) {
  /* 当宽度小于768px时应用以下样式 */
  .navbar-menu {
    display: none; /* 隐藏菜单项 */
  }

  .navbar-menu.collapsed {
    max-height: 1000px; /* 确保折叠状态下可以展开下拉菜单 */
  }

  .navbar-menu-item,
  .navbar-menu-item-last {
    display: none; /* 隐藏菜单项 */
  }

  .navbar-mobile-button {
    display: block;
  }
}
</style>
