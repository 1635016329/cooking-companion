<script setup lang="ts">

import {Component, h, ref} from 'vue'
import type {MenuOption} from 'naive-ui'
import {NIcon} from 'naive-ui'
import {
  BookOutline as BookIcon,
  HomeOutline as HomeIcon,
  PersonOutline as PersonIcon,
  WineOutline as WineIcon
} from '@vicons/ionicons5'
import {RouterLink} from "vue-router";

const activeKey = ref<string | null>(null)
const collapsed = ref(false)

function renderIcon(icon: Component) {
  return () => h(NIcon, null, {default: () => h(icon)})
}

const menuOptions: MenuOption[] = [
  {
    label: () => h(
        RouterLink,
        {
          to: '/'
        },
        {default: () => '首页'}
    ),
    key: 'home',
    icon: renderIcon(HomeIcon)
  },
  {
    label: '用户模块',
    key: 'user-admin',
    icon: renderIcon(BookIcon),
    children: [
      {
        label: () => h(
            RouterLink,
            {
              to: 'users'
            },
            {default: () => '用户'}
        ),
        key: 'users'
      }
    ]
  },
  {
    label: '食谱模块',
    key: 'recipe-admin',
    icon: renderIcon(BookIcon)
  },
  {
    label: '商城模块',
    key: 'product-admin',
    icon: renderIcon(BookIcon),
    children: [
      {
        type: 'group',
        label: '人物',
        key: 'people',
        children: [
          {
            label: '叙事者',
            key: 'narrator',
            icon: renderIcon(PersonIcon)
          },
          {
            label: '羊男',
            key: 'sheep-man',
            icon: renderIcon(PersonIcon)
          }
        ]
      },
      {
        label: '饮品',
        key: 'beverage',
        icon: renderIcon(WineIcon),
        children: [
          {
            label: '威士忌',
            key: 'whisky'
          }
        ]
      },
      {
        label: '食物',
        key: 'food',
        children: [
          {
            label: '三明治',
            key: 'sandwich'
          }
        ]
      },
      {
        label: '过去增多，未来减少',
        key: 'the-past-increases-the-future-recedes'
      }
    ]
  }
]
</script>

<template>
  <div class="layout">
    <n-layout position="absolute" bordered>
      <n-layout-header class="header" bordered>颐和园路</n-layout-header>
      <n-layout has-sider bordered position="absolute" class="content">
        <n-layout-sider
            bordered
            collapse-mode="width"
            :collapsed-width="64"
            :width="240"
            :collapsed="collapsed"
            show-trigger
            @collapse="collapsed = true"
            @expand="collapsed = false"
        >
          <n-menu
              v-model:value="activeKey"
              :collapsed="collapsed"
              :collapsed-width="64"
              :collapsed-icon-size="22"
              :options="menuOptions"
          />
        </n-layout-sider>
        <n-layout content-style="padding: 24px;" :native-scrollbar="false">
          <router-view/>
        </n-layout>
      </n-layout>
      <n-layout-footer class="footer" position="absolute" bordered>成府路</n-layout-footer>
    </n-layout>
  </div>
</template>

<style scoped>
.layout {
  height: 100%;
  width: 100%;
}

.header {
  height: 64px;
  padding: 24px;
  background-color: #f0f2f5;
}

.content {
  top: 64px;
  bottom: 64px;
}

.footer {
  height: 64px;
  padding: 24px;
  background-color: #f0f2f5;
}
</style>