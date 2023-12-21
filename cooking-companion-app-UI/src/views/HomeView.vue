<script setup lang="ts">
import { ref } from 'vue'

const search = ref('')
const activeTab = ref(1)
const activeTabbar = ref(0)
const icon = {
  active: 'https://fastly.jsdelivr.net/npm/@vant/assets/user-active.png',
  inactive: 'https://fastly.jsdelivr.net/npm/@vant/assets/user-inactive.png'
}

const icons = [
  { active: 'wap-home', inactive: 'wap-home-o' },
  { active: 'star', inactive: 'star-o' },
  { active: 'wap-home', inactive: 'wap-home-o' },
  { active: 'chat', inactive: 'chat-o' },
  { active: 'contact', inactive: 'contact-o' }
]

icon
</script>

<template>
  <div class="home-view">
    <div class="header">
      <van-icon class="menu" color="#333333" name="wap-nav" size="20" />
      <van-search
        v-model="search"
        shape="round"
        width="500"
        class="search"
        placeholder="搜索菜谱、用户"
      />
      <van-icon class="chat" color="#555555" name="bell" size="20" />
    </div>
    <div class="tabs">
      <van-tabs color="#333333" swipeable line-width="25" v-model:active="activeTab">
        <van-tab title="关注">关注</van-tab>
        <van-tab class="tab-item" title="推荐">
          <van-grid :column-num="2">
            <van-grid-item
              class="grid-item"
              v-for="value in 100"
              :key="value"
              icon="photo-o"
              text="文字"
            >
              <van-image
                radius="10"
                class="img"
                src="https://img.zcool.cn/community/0130985fd05d1a11013fdcc7ae7b97.jpg@1280w_1l_2o_100sh.jpg"
              />
              <div class="title">土豆炒鸡蛋</div>
              <div class="footer">
                <div class="info">
                  <van-image
                    width="20px"
                    class="avatar"
                    src="https://tse1-mm.cn.bing.net/th/id/OIP-C.ZtrvDWpDrJNiyRQj6DwPvwAAAA?rs=1&pid=ImgDetMain"
                    radius="10"
                  ></van-image>
                  <div class="writer">清蒸大白菜</div>
                </div>
                <van-icon size="20" name="ellipsis" />
              </div>
            </van-grid-item>
          </van-grid>
        </van-tab>
        <van-tab title="商店">商店</van-tab>
      </van-tabs>
    </div>
    <van-tabbar fixed v-model="activeTabbar" active-color="#333333" inactive-color="#858585">
      <van-tabbar-item :icon="activeTabbar === 0 ? icons[0].active : icons[0].inactive"
        >首页
      </van-tabbar-item>
      <van-tabbar-item :icon="activeTabbar === 1 ? icons[1].active : icons[1].inactive"
        >收藏
      </van-tabbar-item>
      <van-tabbar-item>
        <van-button icon="plus" size="small" color="#fb6650" class="plus" />
      </van-tabbar-item>
      <van-tabbar-item :icon="activeTabbar === 3 ? icons[3].active : icons[3].inactive"
        >消息
      </van-tabbar-item>
      <van-tabbar-item :icon="activeTabbar === 4 ? icons[4].active : icons[4].inactive"
        >我
      </van-tabbar-item>
    </van-tabbar>
  </div>
</template>

<style scoped>
.header {
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin-top: 5px;
  padding: 10px;
  height: 40px;
}

.menu {
}

.search {
  width: 300px;
}

.chat {
}

.tab-item {
  height: 658px;
  overflow: auto;
  overscroll-behavior: contain;
}

:deep(.van-tabs__line) {
  bottom: 20px;
}

.plus {
  font-size: 20px;
  border-radius: 15px;
  height: 40px;
  margin-bottom: 5px;
}

.grid-item {
  align-items: normal;
}

.title {
  padding: 10px;
  font-weight: 700;
  font-size: 16px;
}

.footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 12px;
  padding-left: 10px;
  color: #858585;
}

.writer {
  margin-left: 10px;
  font-size: 12px;
  color: #858585;
}

.avatar {
}

:deep(.van-grid-item__content--center) {
  align-items: normal;
}

.info {
  display: flex;
  align-items: center;
}


</style>