<template>
  <div class="container">
    <div class="userinfo" @click='login'>
      <img :src="userinfo.avatarUrl" alt="">
      
    </div>
    <YearProgress></YearProgress>

    <!-- <button open-type="getUserInfo" @click='login' class='btn'></button>  -->

    <button v-if='userinfo.openId' @click='scanBook' class='btn'>添加图书</button>

    <button v-if='!userinfo.openId&&canIUse'  open-type='getUserInfo' class='btn' @getuserinfo='login'>点击登录</button>
  </div>
</template>
<script>
import qcloud from 'wafer2-client-sdk'
import YearProgress from '@/components/YearProgress'
import { showSuccess } from '@/util'
import config from '@/config'
export default {
  components: {
    YearProgress
  },
  data () {
    return {
      userinfo: {
        avatarUrl: '../../../static/img/default-avatar.png',
        nickName: '点击登录'
      },
      canIUse: wx.canIUse('button.open-type.getUserInfo')
    }
  },
  methods: {
    scanBook () {
      wx.scanCode({
        success: (res) => {
          if (res.result) {
            console.log(res.result)
          }
        }
      })
    },
    login () {
      let user = wx.getStorageSync('userinfo')
      const self = this
      if (!user) {
        qcloud.setLoginUrl(config.loginUrl)
        qcloud.login({
          success: function (userinfo) {
            qcloud.request({
              url: config.userUrl,
              login: true,
              success (userRes) {
                showSuccess('登录成功')
                wx.setStorageSync('userinfo', userRes.data.data)
                self.userinfo = userRes.data.data
              }
            })
          },
          fail: function (err) {
            console.log('登录失败', err)
          }
        })
      }
    }
  },
  onShow () {
    let userinfo = wx.getStorageSync('userinfo')
    if (userinfo) {
      this.userinfo = userinfo
    }
  }
}
</script>

<style lang='scss'>
.container{
  padding:0 30rpx;

}  
.userinfo{
  margin-top:100rpx;
  text-align:center;
  img{
    width: 150rpx;
    height:150rpx;
    margin: 20rpx;
    border-radius: 50%;
  }
}


</style>
