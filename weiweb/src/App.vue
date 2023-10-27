<template>
  <!-- <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header> -->

  <!-- <RouterView /> -->

  <div>
    <el-header> </el-header>

    <el-container>
      <el-aside width="200px">
        <el-scrollbar>
          <el-menu
            default-active="2"
            class="el-menu-vertical-demo"
            @open="handleOpen"
            @close="handleClose"
            router
          >
            

            <!-- 用script產生目錄 -->
            <el-sub-menu v-for="item in menu" :key="item.id" :index="item.path">
              <template #title>
                <el-icon>
                  <Edit />
                </el-icon>
                <span>{{ item.name }}</span>
              </template>
              <el-menu-item v-for="app in item.app" :key="app.id" :index="app.path">
                <span>{{ app.name }}</span>
              </el-menu-item>
              
            </el-sub-menu>
          </el-menu>
        </el-scrollbar>
      </el-aside>

      <el-main style="width: 800px">
        <RouterView />
      </el-main>
    </el-container>
  </div>
</template>

<script lang="ts" setup>
import { Document, Menu as IconMenu, Location, Setting } from "@element-plus/icons-vue";
const handleOpen = (key: string, keyPath: string[]) => {
  console.log(key, keyPath);
};
const handleClose = (key: string, keyPath: string[]) => {
  console.log(key, keyPath);
};

// menu 首頁 關於 APP
const menu = [
  {
    id: "1",
    name: "首頁",
    path: "/",
    icon: "Document",
    app: [{ id: "1-1", name: "1-1", path: "/" }],
  },
  { id: "2", name: "關於", path: "/about", icon: "Location",app: [{ id: "2-1", name: "關於", path: "/about" }],},
  { id: "3", name: "APP", path: "/app", icon: "Setting" },
];
</script>
