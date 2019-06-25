<template>
  <div>
    <div @click="clickHandle">
      <div class="userinfo" @click="bindViewTap">
        <img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl" background-size="cover" />
        <img class="userinfo-avatar" src="/static/images/user.png" background-size="cover" />
        <div class="userinfo-nickname">
          <card :text="userInfo.nickName"></card>
        </div>
      </div>
    </div>
    <div class="url-wrap">
      <a href="/pages/counter/main" class="counter">去往Vuex示例页面</a>
    </div>
    <div class="btn-wrap">
      <van-button type="primary" @click="vantButton">测试vant</van-button>
    </div>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      motto: 'Hello miniprograme',
      userInfo: {
        nickName: 'mpvue',
        avatarUrl: 'http://mpvue.com/assets/logo.png'
      }
    }
  },
  components: {
    card
  },
  methods: {
    bindViewTap () {
      const url = '../logs/main'
      if (mpvuePlatform === 'wx') {
        mpvue.switchTab({ url })
      } else {
        mpvue.navigateTo({ url })
      }
    },
    clickHandle (ev) {
      console.log('clickHandle:', ev)
      // throw {message: 'custom test'}
    },
    vantButton () {
      console.log('vant button is click')
    }
  },
  created () {
    // let app = getApp()
  }
}
</script>

<style scoped>
.userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.userinfo-avatar {
  width: 128rpx;
  height: 128rpx;
  margin: 20rpx;
  border-radius: 50%;
}

.userinfo-nickname {
  color: #aaa;
}



.counter {
  background: green;
  width: 600rpx;
  margin: 0 auto;
  padding: 10rpx 0;
}

.btn-wrap,
.url-wrap {
  text-align: center;
  margin: 20rpx 0;
}
</style>
