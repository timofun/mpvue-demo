<script>
// import { get } from './util'
export default {
  async created () {
    // // 同步
    // const res = await get('/weapp/demo')
    // console.log(res)

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
    console.log('启动小程序')
  }
}
</script>

<style>
.text-footer{
  text-align: center;
  font-size: 12px;
  margin-bottom:5px;
}
.text-primary{
  color:#EA5149;
}
.btn{
  color:white;
  background:#EA5A49;
  margin-bottom: 10px;
  padding-left: 15px;
  padding-left: 15px;
  border-radius: 2px;
  font-size: 16px;
  line-height: 40px;
  height: 40px;
  width: 100%;
}
.btn:active{
  background: #FA5A49;
}
</style>
