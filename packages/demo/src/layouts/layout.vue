<template>
  <ex-layout title="Element Go" homepage="/components/page-header"
    :channels="channels" :menu="menu" :show-header="true" :show-menu="true">
    <template #account>
      <el-button circle size="small" :icon="isDark ? Sun : Moon" @click="toggleDark()" />
    </template>
    <el-main>
      <router-view />
    </el-main>
  </ex-layout>
</template>

<script setup lang="ts">
import type { Menu } from '@core/types'
import { ExLayout } from '@core/index'
import { ElMain, ElButton } from 'element-plus'
import { HamburgerButton, Search, TableFile, Loading, MoreFour, Page } from '@icon-park/vue-next'
import { useDark, useToggle } from '@vueuse/core'
import { Sun, Moon } from '@icon-park/vue-next'
import menu from './menu'

const isDark = useDark()
const toggleDark = useToggle(isDark)
const channels: Array<Menu> = [
  { label: '布局', icon: Page, path: '/components/layout' },
  { label: '页头', icon: HamburgerButton, path: '/components/page-header' },
  { label: '搜索', icon: Search, path: '/components/form-search' },
  { label: '表格', icon: TableFile, path: '/components/table' },
  { label: '加载', icon: Loading, path: '/components/loading' },
  { label: '分页', icon: MoreFour, path: '/components/pagination' },
]
</script>
