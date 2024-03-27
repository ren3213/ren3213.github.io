<template>
  <div>
    <el-container style="background-color: #000000">
      <el-header text-align="center">
        <el-menu
          mode="horizontal"
          :collapse="isCollapse"
          @select="handleSelect"
          background-color="#000000"
          text-color="#00FF00"
          active-text-color="#000000"
          style="display: flex; justify-content: center; align-items: center"
        >
          <RouterLink to="/" style="text-decoration: none"
            ><el-menu-item index="1" v-if="!isCollapse">
              <i class="el-icon-menu"></i>
              <span slot="title" color="#000000">首页</span>
            </el-menu-item></RouterLink
          >
          <el-submenu index="2" v-if="!isCollapse" width="100px">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span slot="title">技术</span>
            </template>
            <el-menu-item-group width="100px">
              <el-menu-item index="2-1" width="100px">选项1</el-menu-item>
              <el-menu-item index="2-2" width="100px">选项2</el-menu-item>
              <el-menu-item index="2-3" width="100px">选项3</el-menu-item>
            </el-menu-item-group>
            <el-submenu index="2-4">
              <span slot="title">选项4</span>
              <el-menu-item index="2-4-1" width="100px">选项1</el-menu-item>
            </el-submenu>
          </el-submenu>
          <el-menu-item index="3" v-if="!isCollapse">
            <i class="el-icon-document"></i>
            <span slot="title" v-if="!isCollapse">导航三</span>
          </el-menu-item>
          <RouterLink to="/img" style="text-decoration: none">
            <el-menu-item index="4" v-if="!isCollapse">
              <i class="el-icon-setting"></i>
              <span slot="title" v-if="!isCollapse">img</span>
            </el-menu-item>
          </RouterLink>
        </el-menu>
        <el-menu
          mode="horizontal"
          :collapse="isCollapse"
          @select="handleSelect"
          background-color="#545c64"
          text-color="#fff"
          active-text-color="#ffd04b"
          style="
            display: flex;
            justify-content: flex-start;
            align-items: center;
          "
        >
          <el-submenu index="1" v-if="isCollapse">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span slot="title"></span>
            </template>
            <el-menu-item-group>
              <RouterLink to="/" style="text-decoration: none"
                ><el-menu-item index="2-1">首页</el-menu-item></RouterLink
              >
              <el-menu-item index="2-2">技术</el-menu-item>
              <RouterLink to="/img" style="text-decoration: none"
                ><el-menu-item index="2-3">img</el-menu-item></RouterLink
              >
            </el-menu-item-group>
            <el-submenu index="2-4">
              <span slot="title">选项4</span>
              <el-menu-item index="2-4-1">选项1</el-menu-item>
            </el-submenu>
          </el-submenu>
        </el-menu>
      </el-header>
      <el-container>
        <el-main class="maina"> <router-view /></el-main>
        <el-aside width="200px">Aside</el-aside>
      </el-container>
      <el-footer>Footer</el-footer>
    </el-container>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      isCollapse: false, // 是否折叠菜单
      windowWidth: window.innerWidth,
    };
  },
  mounted() {
    window.addEventListener("resize", this.handleResize);
    this.handleResize(); // 初始加载时判断窗口大小
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.handleResize);
  },
  methods: {
    handleResize() {
      this.windowWidth = window.innerWidth;
      this.isCollapse = this.windowWidth < 768; // 在小屏幕下折叠菜单
    },
    handleSelect(index) {
      // 处理菜单选中事件
    },
  },
};
</script>

<style>
.el-header,
.el-footer {
  background-color: transparent;
  color: #333;
  text-align: center;
  line-height: 60px;
}
.el-header {
  padding: 0 0;
}
.el-aside {
  background-color: transparent;
  color: #333;
  text-align: center;
  line-height: 200px;
}
.el-menu.el-menu--horizontal {
  border-bottom: 0;
  background-color: transparent;
}
.el-main {
  background-color: transparent;
  color: #333;
  text-align: center;
  height: 800px;
  /* line-height: 160px; */
}

body > .el-container {
  margin-bottom: 40px;
}

.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
  line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 320px;
}
</style>
