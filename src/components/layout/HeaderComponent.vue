<script lang="ts">/*eslint-disable*/ 
import { Vue, Component } from "vue-property-decorator";
@Component({})
export default class HeaderComponent extends Vue {
  menuIsActive: boolean = false;

  menuNav() {
    this.menuIsActive = !this.menuIsActive;
  }
}
</script>
<template>
  <el-header height="auto">
    <el-row type="flex" class="row-bg" justify="space-between">
      <el-col class="header-logo" :span="12">
        <a href="#">
          <!--все картинки в папке assets*/ -->
          <img src="@/assets/img/header-logo.svg" alt="logo" />
        </a>
      </el-col>
      <el-col :span="12"
        ><div>
          <el-button plain size="mini" class="mobile-nav" @click="menuNav"
            ><i v-if="menuIsActive" class="el-icon-menu"></i><i class="el-icon-close"></i
          ></el-button>
          <el-menu
            :default-active="activeIndex"
            mode="horizontal"
            v-bind:class="{ '': !menuIsActive, ' isOpen': menuIsActive }"
          >
            <el-menu-item index="1"><router-link to="/">Home</router-link></el-menu-item>
            
            <el-menu-item index="3" disabled>Info</el-menu-item>
            <el-menu-item index="4">
              <router-link to="/about">About</router-link></el-menu-item
            >
          </el-menu>
          <el-radio-group v-model="radio4" disabled size="mini">
      <el-radio-button label="ru">RU</el-radio-button>
      <el-radio-button label="en">Eng</el-radio-button>  
      </el-radio-group>
      <el-button size="mini" type="info"><i class="el-icon-upload el-icon-right"></i>Logout</el-button>
        </div></el-col
      >
    </el-row>
  </el-header>
</template>
<style lang="scss" scroped>
.el-header {
  padding: 0;
  position: relative;
}
.el-menu--horizontal.el-menu {
  border: none;
  .el-menu-item {
    background: transparent;
    a {
      font-size: 16px;
      text-decoration: none;
    }
    &.is-active {
      border: none;
    }
  }
  @media (max-width: 768px) {
    display: none;
    opacity: 0;
    background: #585757;
  }
  &.isOpen {
    position: absolute;
    width: 100%;
    top: 60px;
    display: block;
    opacity: 1;
  }
}
</style>
