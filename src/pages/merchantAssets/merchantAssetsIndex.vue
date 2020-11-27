<template>
  <div class="wrapper">
    <aside>
      <el-menu
        default-active="2"
        class="el-menu-vertical-demo"
        @open="handleOpen"
        @close="handleClose"
      >
        <el-submenu index="1">
          <template slot="title">
            <i class="el-icon-location"></i>
            <span>商户账号</span>
          </template>
          <el-menu-item index="1-1">所有</el-menu-item>
          <el-menu-item index="1-2">分润账号</el-menu-item>
          <el-menu-item index="1-3">自营账号</el-menu-item>
        </el-submenu>
        <el-submenu index="2">
          <template slot="title">
            <i class="el-icon-location"></i>
            <span>财务管理</span>
          </template>
          <el-menu-item index="1-1">订单记录</el-menu-item>
          <el-menu-item index="1-2">分成记录</el-menu-item>
          <el-menu-item index="1-3">提现记录</el-menu-item>
        </el-submenu>
        <el-submenu index="3">
          <template slot="title">
            <i class="el-icon-location"></i>
            <span>自营网关</span>
          </template>
          <el-menu-item index="1-1">支付网关</el-menu-item>
          <el-menu-item index="1-2">发票网关</el-menu-item>
          <el-menu-item index="1-3">短信网关</el-menu-item>
        </el-submenu>
        <el-submenu index="4">
          <template slot="title">
            <i class="el-icon-location"></i>
            <span>开放平台</span>
          </template>
        </el-submenu>
        <el-submenu index="5">
          <template slot="title">
            <i class="el-icon-location"></i>
            <span>操作日志</span>
          </template>
        </el-submenu>
      </el-menu>
    </aside>
    <section>
      123
    </section>
  </div>
</template>

<script>
export default {
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    }
  }
};
</script>

<style lang="stylus" scoped>
px(a)
   a*(1440/1920) px
*
  margin 0
  padding 0

aside
  float left
  // border 1px solid black
  width px(280)
  height 100vh
  background #1E69FE

section
  float right
  // border 1px solid black
  width  px(1640)
  height 100vh
</style>
