<template>
  <el-container>
    <el-aside :width="isCollapse ? '64px' : '200px'">
      <el-menu
        default-active="this.$route.path"
        class="el-menu-vertical-demo"
        background-color="#304156"
        text-color="#BFCBD9"
        active-text-color="#329EF2"
        style="height: 100%"
        router
        :collapse="isCollapse"
        :collapse-transition="false"
      >
        <el-menu-item index="home">
          <i class="el-icon-s-home"></i>
          <span slot="title">首页</span>
        </el-menu-item>
        <!-- 后续这里取消注释，这里是动态菜单栏 -->
        <el-submenu
          v-for="(value, key) in adminMenuList"
          :key="key"
          :index="key"
        >
          <template slot="title">
            <i class="myicon myiconyanchu" style="font-size: 20px"></i>
            <span slot="title"> {{key}}</span>
          </template>
          <el-menu-item :index="menu.name" v-for="menu in value" :key="menu.id">
            <i class="el-icon-tickets"></i>
            <span slot="title">{{ menu.title }}</span></el-menu-item
          >
        </el-submenu>
        <!-- 后续这里取消注释，这里是动态菜单栏 -->
        <!-- <el-submenu index="show">
          <template slot="title">
            <i class="myicon myiconyanchu" style="font-size: 20px"></i>
            <span slot="title"> 演出</span>
          </template>

          <el-menu-item index="show">
            <i class="el-icon-tickets"></i>
            <span slot="title">演出列表</span></el-menu-item
          >
          <el-menu-item index="addShow">
            <i class="myicon myicontianjiaxiangqing"></i>
            <span slot="title" style="margin-left: 5px">
              添加演出</span
            ></el-menu-item
          >
          <el-menu-item index="category">
            <i class="myicon myiconmulu"></i>
            <span slot="title" style="margin-left: 5px">
              目录管理</span
            ></el-menu-item
          >
        </el-submenu>
        <el-submenu index="order">
          <template slot="title">
            <i class="myicon myiconicon--copy" style="font-size: 20px"></i>
            <span slot="title"> 订单</span>
          </template>
          <el-menu-item index="order">
            <i class="myicon myiconicon--copy" style="font-size: 20px"></i>
            <span slot="title"> 订单列表</span></el-menu-item
          >
        </el-submenu>
        <el-submenu index="promo">
          <template slot="title">
            <i class="myicon myiconicon--copy" style="font-size: 20px"></i>
            <span slot="title">活动管理</span>
          </template>
          <el-menu-item index="Promo">
            <i class="myicon myiconicon--copy" style="font-size: 20px"></i>
            <span slot="title"> 活动列表</span></el-menu-item
          >
          <el-menu-item index="AddPromo">
            <i class="myicon myiconicon--copy" style="font-size: 20px"></i>
            <span slot="title"> 添加活动</span></el-menu-item
          >
        </el-submenu>
        <el-submenu index="user">
          <template slot="title">
            <i class="el-icon-user-solid"></i>
            <span slot="user">权限管理</span>
          </template>
          <el-menu-item index="user">
            <i class="myicon myiconyonghuliebiao" style="font-size: 20px"></i>
            <span slot="title" style="margin-left: 5px">
              用户列表</span
            ></el-menu-item
          >
          <el-menu-item index="Role">
            <i class="myicon myiconyonghuliebiao" style="font-size: 20px"></i>
            <span slot="title" style="margin-left: 5px">
              角色管理</span
            ></el-menu-item
          >
          <el-menu-item index="Resource">
            <i class="myicon myiconyonghuliebiao" style="font-size: 20px"></i>
            <span slot="title" style="margin-left: 5px">
              资源管理</span
            ></el-menu-item
          >
          <el-menu-item index="Menu">
            <i class="myicon myiconyonghuliebiao" style="font-size: 20px"></i>
            <span slot="title" style="margin-left: 5px">
              菜单管理</span
            ></el-menu-item
          >
        </el-submenu> -->
      </el-menu>
    </el-aside>
    <el-main style="padding: 0px">
      <el-breadcrumb
        separator-class="el-icon-arrow-right"
        style="padding: 20px"
      >
        <el-breadcrumb-item
          v-for="(item, index) in list"
          :key="index"
          :to="{ path: item.path }"
        >
          {{ item.name }}
        </el-breadcrumb-item>
        <el-dropdown @command="handleCommand">
          <span class="el-dropdown-link">
            <i class="el-icon-user-solid" style="font-size: 25px"></i
            ><i class="el-icon-arrow-down el-icon--right"></i>
          </span>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item command="logout">退出</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
      </el-breadcrumb>
      <el-divider></el-divider>
      <router-view :key="$route.fullPath"></router-view>
    </el-main>
  </el-container>
</template>

<style scoped>
.el-menu {
  border-right-width: 0;
}

.el-footer {
  background-color: #b3c0d1;
  color: #333;
  text-align: center;
  line-height: 60px;
}
.el-divider {
  margin: 0px;
}
.el-aside {
  background-color: #304156;
  color: #333;
  text-align: center;
  line-height: 200px;
}

.el-main {
  background-color: #ffffff;
  color: #333;
  text-align: center;
  /* line-height: 100px; */
  padding: 0px;
}

.el-container {
  height: 100%;
}

.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
  line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 320px;
}

.toggle-button {
  background: #e9eef3;
  color: #329ef2;
  font-size: 10px;
  line-height: 24px;
  text-align: center;
  letter-spacing: 0.2em;
  cursor: pointer;
  width: 10px;
  height: 60px;
}

.el-dropdown-link {
  cursor: pointer;
  color: #409eff;
  padding-left: 1100px;
}
</style>

<script>
import axios from "axios";
import api from "@/assets/api.js";
export default {
  data() {
    return {
      isCollapse: false,
      breadList: [], // 路由集合
      list: [], //面包屑动态生成所用集合
      adminMenuList: [], //当前管理员能看到的菜单栏列表
    };
  },
  watch: {
    $route() {
      this.bread();
    },
  },
  async mounted() {
    console.log("pageContainermounted");
    try {
      const res = await axios.post(`${api.API_URL}/login/AdminMenu`, {
        headers: {
          Authorization: "Bearer " + sessionStorage.getItem("token"),
        },
      });
      console.log("/login/AdminMenu", res.data.data);
      if (res.data.code == 200) {
        this.adminMenuList = res.data.data;
      } else {
        this.$message.error("获取AdminMenu失败");
      }
      console.log("this.adminMenuList", this.adminMenuList);
    } catch (err) {
      console.log(err);
      this.$message.error("获取AdminMenu失败");
    }
  },
  methods: {
    // 点击切换左侧菜单的折叠与展开
    toggleCollapse() {
      this.isCollapse = !this.isCollapse;
    },
    handleCommand(command) {
      if (command === "logout") {
        window.sessionStorage.clear();
        this.$router.push("/login");
      }
    },
    //面包屑动态生成
    bread() {
      let matched = this.$route.matched.filter((item) => item.name);
      let first = matched[0];
      if (first && first.name !== "home") {
        console.log(first);
        // 我在这里是判断的是name，渲染的是name，但是可以使用其他的字段
        matched = [{ path: "/home", name: "首页" }].concat(matched);
      }
      for (let element of matched) {
        if (element.name == "main" || element.path == "/home") {
          var index = matched.indexOf(element);
          if (index > -1) {
            matched.splice(index, 1);
          }
        }
      }
      this.list = matched;

      console.log(this.list);
    },
  },
  created() {
    this.bread();
  },
};
</script>