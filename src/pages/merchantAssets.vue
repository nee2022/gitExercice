<template>
  <div class="UserAssets-bgcolor">
    <div class="UserAssets-left">
      <div class="UserAssets-logo">
        <span class="LOGO">LOGO</span>
      </div>
      <div class="vive">
        <div class="set">
          <img src="../assets/images/Big Data View.png" />
        </div>
        <span>大数据视图</span>
      </div>
      <el-col :span="12">
        <el-menu
          default-active="2"
          class="el-menu-vertical-demo"
          @open="handleOpen"
          @close="handleClose"
          background-color="#1e69fe"
          text-color="#fff"
          active-text-color="#1e69fe"
          unique-opened
          v-model="option"
        >
          <el-submenu index="1">
            <template slot="title">
              <div class="menu-op">
                <div>
                  <img src="../assets/images/user account.png" />
                </div>
                <span>商户账号</span>
              </div>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">
                <div class="menu-op">
                  <div>
                    <img src="../assets/images/all.png" />
                  </div>
                  所有
                </div>
              </el-menu-item>
              <el-menu-item index="1-2">
                <div class="menu-op">
                  <div>
                    <img src="../assets/images/phone.png" />
                  </div>
                  分润账号
                </div>
              </el-menu-item>
              <el-menu-item index="1-3">
                <div class="menu-op">
                  <div>
                    <img src="../assets/images/alipay.png" />
                  </div>
                  自营账号
                </div>
              </el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="2">
            <template slot="title">
              <div class="menu-op">
                <div>
                  <img src="../assets/images/One cartoon.png" />
                </div>
                <span>财务管理</span>
              </div>
            </template>
            <el-menu-item-group>
              <el-menu-item-group>
                <el-menu-item index="1-1">
                  <div class="menu-op">
                    <div>
                      <img src="../assets/images/all.png" />
                      订单记录
                    </div>
                  </div>
                </el-menu-item>
                <el-menu-item index="1-2">
                  <div class="menu-op">
                    <div>
                      <img src="../assets/images/phone.png" />
                      分成记录
                    </div>
                  </div>
                </el-menu-item>
                <el-menu-item index="1-3">
                  <div class="menu-op">
                    <div>
                      <img src="../assets/images/alipay.png" />
                      提现记录
                    </div>
                  </div>
                </el-menu-item>
              </el-menu-item-group>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="3">
            <template slot="title">
              <div class="menu-op">
                <div>
                  <img src="../assets/images/coupons.png" />
                </div>
                <span>自营网关</span>
              </div>
            </template>
            <el-menu-item-group>
              <el-menu-item-group>
                <el-menu-item index="1-1">
                  <div class="menu-op">
                    <div>
                      <img src="../assets/images/all.png" />
                      支付网关
                    </div>
                  </div>
                </el-menu-item>
                <el-menu-item index="1-2">
                  <div class="menu-op">
                    <div>
                      <img src="../assets/images/phone.png" />
                      发票网关
                    </div>
                  </div>
                </el-menu-item>
                <el-menu-item index="1-3">
                  <div class="menu-op">
                    <div>
                      <img src="../assets/images/alipay.png" />
                      短信网关
                    </div>
                  </div>
                </el-menu-item>
              </el-menu-item-group>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="4">
            <template slot="title">
              <div class="menu-op">
                <div>
                  <img src="../assets/images/The user package.png" />
                </div>
                <span>开放平台</span>
              </div>
            </template>
          </el-submenu>
          <el-submenu index="4">
            <template slot="title">
              <div class="menu-op">
                <div>
                  <img src="../assets/images/The user package.png" />
                </div>
                <span>操作日志</span>
              </div>
            </template>
          </el-submenu>
        </el-menu>
      </el-col>
    </div>
    <div class="UserAssets-right">
      <div class="UserAssets-right-top">
        <div class="user-left">
          <span class="user-word">用户</span>
        </div>
        <div class="user-right">
          <div>
            <img src="../assets/images/help.png" />
          </div>
          <div>
            <img src="../assets/images/set up.png" />
          </div>
          <div class="user-img">
            <img src="../assets/images/bgm.png" />
          </div>
          <span>呢称</span>
        </div>
      </div>
      <div class="UserAssets-right-text">
        <div>
          <select class="select1" v-model="selected" @click="op">
            <option v-for="item in typeList" v-bind:value="item.type">{{
              item.type
            }}</option>
          </select>
        </div>
        <div class="textBox">
          <img src="../assets/images/search.png" class="sear-img" />
          <input
            type="text"
            placeholder="请输入账号、手机号、昵称进行查找"
            class="textWord"
          />
        </div>
        <div>
          <el-button type="primary" icon="el-icon-search">搜索</el-button>
        </div>
        <div>
          <el-button type="primary" icon="el-icon-circle-plus-outline"
            >添加</el-button
          >
        </div>
      </div>
      <div>
        <template>
          <el-table :data="tableData" stripe style="width: 100%">
            <el-table-column prop="id" label="用户ID" width="130">
            </el-table-column>
            <el-table-column prop="username" label="账号" width="180">
            </el-table-column>
            <el-table-column v-if="(telephone = '')" prop="未绑定" label="手机">
            </el-table-column>
            <el-table-column v-else prop="telephone" label="手机">
            </el-table-column>
            <el-table-column prop="state" label="状态"> </el-table-column>
            <el-table-column prop="amount" label="钱包余额"> </el-table-column>
            <el-table-column prop="score" label="积分"> </el-table-column>
            <el-table-column prop="date_created" label="注册时间">
            </el-table-column>
            <el-table-column prop="address" label="操作" width="200">
              <div class="operation">
                <div>
                  <img src="../assets/images/delete.png" />
                </div>
                <div>
                  <el-button type="text" @click="dialogVisible = true"
                    ><img src="../assets/images/compile.png"
                  /></el-button>
                </div>
                <div>
                  <img src="../assets/images/top-up.png" />
                </div>
                <div>
                  <img src="../assets/images/Prepaid phone password.png" />
                </div>
              </div>
            </el-table-column>
          </el-table>
        </template>
      </div>
      <div class="UserAssets-bottom">
        <div class="UserAssets-bottom-left" :data="tableData">
          <span>共{{ total }}条信息</span>
        </div>
        <div class="UserAssets-bottom-right">
          <el-pagination
            background
            :current-page.sync.number="pagenum"
            @current-change="handleCurrentChange"
            :page-size="pagesize"
            layout="prev, pager, next"
            :total="total"
          >
          </el-pagination>
        </div>
      </div>
    </div>
    <!-- 弹出框 -->
    <el-dialog
      title="提示"
      :visible.sync="dialogVisible"
      width="30%"
      :before-close="tcClose"
    >
      <span>添加用户</span>
      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">取 消</el-button>
        <el-button type="primary" @click="dialogVisible = false"
          >确 定</el-button
        >
      </span>
    </el-dialog>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tableData: [],
      option: "",
      total: 1,
      isActive: true,
      dialogVisible: false,
      selected: "所有",
      pagenum: 1,
      token: "",
      pagesize: 14,
      typeList: [
        {
          type: "所有"
        },
        {
          type: "手机"
        },
        {
          type: "支付宝"
        },
        {
          type: "微信"
        }
      ]
    };
  },
  created() {
    this.token = localStorage.getItem("token");
    console.log(this.token);
    this.getUserMes();
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
      console.log(this.option);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    },
    //获取用户信息列表
    getUserMes() {
      this.$axios
        .get(
          "http://49.64.169.6:8010/admin/api/users/?token=cb308adc8f920fb27b166f6f5f40c7d4&page=" +
            this.pagenum +
            "&row=14"
        )
        .then(res => {
          console.log(res.data);
          console.log(res.status);
          if (res.status == 200) {
            this.tableData = res.data.users;
            this.total = res.data.total;
            console.log(this.tableData);
            var pn = this.pagenum;
          }
        });
    },
    //弹出框
    tcClose(done) {
      this.$confirm("确认关闭？")
        .then(_ => {
          done();
        })
        .catch(_ => {});
    },
    //监听页码值改变
    handleCurrentChange(newPage) {
      console.log(newPage);
      this.pagenum = newPage;
      this.getUserMes();
    },
    op() {
      console.log(this.token);
    }
  }
};
</script>

<style>
body {
  background-color: #1e69fe;
}

.el-table td {
  padding: 0 0;
}

.active {
  background-color: white;
}

.operation {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 70px;
  margin: 0 auto;
}

.el-table__footer-wrapper,
.el-table__header-wrapper {
  margin-top: 10px;
  background-color: #edf1f5;
}

.textWord {
  width: 390px;
  height: 30px;
  border: none;
}

/*  .is-opened>div::nth-child(1) {
    background-color: white !important;
  } */

.cell {
  text-align: center;
  font-size: 16px;
  display: -webkit-box;
  overflow: hidden;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 1;
}

.el-table .cell {
  line-height: 44px;
}

.UserAssets-bgcolor {
  width: 100%;
  display: flex;
  flex-direction: row;
}

.UserAssets-right {
  display: flex;
  flex: 1;
  flex-direction: column;
  background-color: white;
  border-top-left-radius: 50px;
  border-bottom-left-radius: 50px;
}

/* 顶部按钮 */
.el-button--primary {
  border-radius: 10px;
  height: 37px;
}

.el-table {
  color: #908e8e;
}

.UserAssets-right-top {
  display: flex;
  flex-direction: row;
  width: 95%;
  margin: 20px auto;
  margin-top: 40px;
}

.UserAssets-left {
  display: flex;
  flex-direction: column;
  width: 280px;
  height: 935px;
  background-color: #1e69fe;
}

.UserAssets-logo {
  text-align: center;
  margin: 30px 0px;
}

.LOGO {
  width: 67px;
  height: 20px;
  font-family: MyriadPro-Regular;
  font-size: 40px;
  font-weight: normal;
  font-stretch: normal;
  line-height: 44px;
  letter-spacing: 0px;
  color: #ffffff;
}

.el-col-12 {
  width: 100%;
  text-align: center;
}

/* 字体 */
.vive {
  font-size: 20px;
  color: white;
  text-align: center;
  display: flex;
  flex-direction: row;
  margin: 20px 55px;
}

.el-submenu__title {
  font-size: 20px;
  width: 100%;
}

/* 按钮字体 */
.el-button {
  font-size: 16px;
}

.el-menu-item {
  font-size: 16px;
  color: #dbdbdb;
}

.menu-op {
  display: flex;
  flex-direction: row;
  width: 100%;
  margin-left: 8%;
}

.menu-op div {
  padding: 0px 15px;
  width: 40px;
}

.user-word {
  width: 47px;
  height: 23px;
  font-family: PingFangSC-Regular;
  font-size: 24px;
  font-weight: normal;
  font-stretch: normal;
  line-height: 24px;
  letter-spacing: 1px;
  color: #000000;
}

.user-left {
  width: 90%;
}

.user-right {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
}

.user-right {
  width: 10%;
}

.user-right span {
  color: #8a9199;
}

.user-img {
  height: 40px;
  width: 40px;
  overflow: hidden;
  border-radius: 100%;
}

.el-menu-item.is-active {
  border-radius: 400px;
  background-color: white !important;
}

.el-menu-item.is-active:hover {
  background-color: #1e69fe;
}

.UserAssets-right-text {
  width: 52%;
  margin-left: 40px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.select1 {
  width: 200px;
  height: 34px;
  border-radius: 10px;
  border: solid 1px #1e69fe;
  font-size: 16px;
  padding: 0 2%;
  margin: 0;
}

.textBox {
  width: 422px;
  height: 34px;
  border-radius: 10px;
  border: solid 1px #1e69fe;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}

.UserAssets-bottom {
  display: flex;
  flex-direction: row;
  width: 95%;
  margin: 30px auto;
}

.UserAssets-bottom-left {
  width: 50%;
}

.UserAssets-bottom-right {
  width: 50%;
  text-align: right;
}

.UserAssets-bottom-left span {
  width: 137px;
  height: 18px;
  font-family: PingFangSC-Regular;
  font-size: 16px;
  font-weight: 600;
  font-stretch: normal;
  line-height: 20px;
  letter-spacing: 0px;
  color: #333333;
}

.set {
  width: 40px;
}

.select1 option {
  text-align: center;
}

.sear-img {
  width: 15px;
  height: 15px;
}

/* 第一行数据类型 */
.el-table thead {
  color: black;
}
</style>
