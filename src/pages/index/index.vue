<template>
  <div class="box">
    <div class="item">
      <div class="images-box">
        <img class="img-itm" src="../../../static/images/1-1.jpg" alt="">
        <img class="img-itm" src="../../../static/images/1-2.jpg" alt="">
        <img class="img-itm" src="../../../static/images/1-3.jpg" alt="">
        <img class="img-itm" src="../../../static/images/1-4.jpg" alt="">
        <img class="img-itm" src="../../../static/images/1-5.jpg" alt="">
        <img class="img-itm" src="../../../static/images/1-6.jpg" alt="">
        <img class="img-itm" src="../../../static/images/1-7.jpg" alt="">
        <img class="img-itm" src="../../../static/images/1-8.jpg" alt="">
        <img class="img-itm" src="../../../static/images/1-9.jpg" alt="">
      </div>
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

  },

  created () {
    // let app = getApp()
  }
}
</script>

<style lang="scss" scoped>
.box {
  .item {
    .images-box {
      font-size: 0;
      width: 80%;
      // padding: 10px 15px;
      padding: 10px 0.5% 0;
      background: #eee;
      .img-itm{
        display: inline-block;
        margin: 0 1.5% 10px;
        width: 30%;
        height: 140px;
      }
    }
  }
}
</style>
