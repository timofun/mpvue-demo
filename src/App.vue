<script>
import { get } from './util'
export default {
  async created () {
    // 同步
    const res = await get('/weapp/demo')
    console.log(res)

    // 异步
    // get('/weapp/demo').then(res => {
    //   console.log(res)
    // })

    // wx.request({
    //   url: config.host + '/weapp/demo', // 仅为示例，并非真实的接口地址
    //   header: {
    //     'content-type': 'application/json' // 默认值
    //   },
    //   success: function (res) {
    //     console.log(res)
    //   }
    // })

    console.log('app created and cache logs by setStorageSync')
  }
}
</script>

<style>
.container {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  padding: 200rpx 0;
  box-sizing: border-box;
}
/* this rule will be remove */
* {
  transition: width 2s;
  -moz-transition: width 2s;
  -webkit-transition: width 2s;
  -o-transition: width 2s;
}
</style>
