<script lang="ts" setup>
import { Avatar } from '@element-plus/icons-vue'
import { useStore } from '~/store/store';
import { useRouter } from 'vue-router';

const props = defineProps<{ switchLang: any, logout: any, userName: string }>();

const router = useRouter();

const goto = (url: string) => {
  router.replace({path: url})
}

</script>
<template>
  <div class="header">
    <div class="left-box">
      <div class="logo">
        <a class="goto" @click="goto('/')"><img width="60" height="60" src="../../assets/logo.png"></a>
      </div>
    </div>
    <div class="menu-box">
    <el-menu
      default-active="2"
      class="el-menu-vertical-demo"
      mode="horizontal"
      :ellipsis="false"
      router
    >
    <el-sub-menu index="1">
      <template #title>
        <el-icon><notebook /></el-icon>
        <span>{{$t('side_bar.create_settlement')}}</span>
      </template>
      <el-menu-item-group>
        <template #title><span>{{$t('side_bar.settlement')}}</span></template>
        <el-menu-item index="/apply-settlement">{{$t('side_bar.create_settlement')}}</el-menu-item>
        <el-menu-item index="/history-settlement">{{$t('side_bar.settlement_history')}}</el-menu-item>
      </el-menu-item-group>
    </el-sub-menu>
    <el-menu-item index="/statistical-analysis">
      <template #title>{{$t('side_bar.merchant_order')}}</template>
    </el-menu-item>
    <el-menu-item index="/bank-management">
      <template #title>{{$t('side_bar.bank_management')}}</template>
    </el-menu-item>
    <el-menu-item index="'/merchant-paylist">
      <template #title>{{$t('side_bar.transaction_history')}}</template>
    </el-menu-item>
    <el-menu-item index="'/payoutmerchant-order">
      <template #title>{{$t('side_bar.payoutmerchant_order')}}</template>
    </el-menu-item>
    <el-menu-item index="'/">
      <template #title>{{$t('side_bar.merchant_info')}}</template>
    </el-menu-item>
  </el-menu>
    <el-menu class="el-menu-demo" mode="horizontal" :ellipsis="false">
      <!-- <el-menu-item index="/">Merchant</el-menu-item> -->
      <el-sub-menu index="2">
        <template #title>{{$t("header_menu.language")}}</template>
        <el-menu-item index="2-1" @click="props.switchLang('ch')">中文</el-menu-item>
        <el-menu-item index="2-2" @click="props.switchLang('en')">English</el-menu-item>
      </el-sub-menu>
      <el-sub-menu index="3">
        <template #title>{{props.userName}}</template>
        <el-menu-item index="3-1" @click="props.logout()">{{$t("header_menu.logout")}}</el-menu-item>
      </el-sub-menu>
    </el-menu>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.goto {
  cursor: pointer;
}
.header {
  width: 100%;
  display: flex;
  // justify-content: space-between;
  border-bottom: solid 1px #dcdfe6;
}
.left-box {
  // width: calc(100% - 100px);
}
.logo {
  display: flex;
  align-items: center;
  a {
    display: inline-block;
    img {
      vertical-align: middle;
    }
  }
}
.el-menu--horizontal {
  border-bottom: none;
}
.el-menu {
  // width: 330px;
  // margin-right: -100px;
}
.tool {
  float: right;
}
.menu-box {
   width: calc(100% - 100px);
  display: flex;
  justify-content: space-between;
}
</style>
