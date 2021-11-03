<template>
    <div class="item">
      <!-- <div class="date">
        <p>
          {{list.title}}
        </p>
      </div> -->
      <div class="images-box">
        <div class="images-i-box">
          <div v-for="(item, i) in filtersItem" :key="i">
            <img class="img-itm" 
                mode="aspectFill" 
                lazy-load="true" 
                :src="item" alt="" 
                @tap="previewImage(list.data, i)">
          </div>
        </div>
        <div class="banner-ad">
            <ad unit-id="adunit-8ce1d72d244ab333"></ad>
        </div>
      </div>
    </div>
</template>

<script>
export default {
    props: ['list', 'key'],
    data () {

    },
    computed: {
        filtersItem () {
            return this.list.data
        }
    },
    mounted () {
        // console.log(this)
        // console.log(this._person)
    },
    methods: {
        previewImage (data, i) {
            wx.previewImage({
                current: data[i], // 当前显示图片的http链接
                urls: data, // 需要预览的图片http链接列表,
                success: () => {
                console.log('success')
                },
                fail: () => {
                console.log('fail')
                }
            })
        }
    }
}
</script>

<style lang="scss">
    .item {
        background: #eee;
        .date{
            width: 100%;
            height: 35px;
            line-height: 35px;
            font-size: 14px;
            color: #FF88AF;
            box-sizing: border-box;
            p{
                position: relative;
                text-indent: 15px;
            }
        }
        .images-box {
            position: relative;
            width: 100%;
            font-size: 0;
            .images-i-box{
                width: 100%;
                padding: 0 10px 10px 10px;
                font-size: 0;
                box-sizing: border-box;
                background: #fff;
                & > div{
                    display: inline-block;
                    width: 49%;
                    &:nth-of-type(even) {
                        margin-left: 2%;
                    }
                }
            }
            .img-itm{
                width: 100%;
                margin-top: 10px;
                border-radius: 5px;
                box-shadow: 2px 2px 5px rgba(0, 0, 0, .5);
            }
            .banner-ad{
                padding: 5px;
                background: #FF88AF;
            }
        }
    }
</style>
