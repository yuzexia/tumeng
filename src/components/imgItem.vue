<template>
    <div class="item">
      <div class="date">
        <p>
          {{list.title}}
        </p>
      </div>
      <div class="images-box">
        <div class="images-i-box">
          <div v-for="(item, i) in filtersItem" :key="i">
            <img class="img-itm" :class="{ 'than-nine' : i == 8}" mode="aspectFill" lazy-load="true" :src="item" alt="" @tap="previewImage(list.data, i)" v-if="i < 9">
            <i v-if="i == 8">+{{list.data.length - 9}}</i>
          </div>
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
            return this.list.data.slice(0, 9)
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
            padding-left: 20px;
            width: 100%;
            height: 30px;
            line-height: 30px;
            font-size: 14px;
            color: #999;
            box-sizing: border-box;
            // background: red;
            p{
                position: relative;
                text-indent: 15px;
                border-left: 1px solid #C0C0C0;
                // background: red;
                &:before{
                content: '';
                position: absolute;
                top: calc(50% - 4px);
                left: -5px;
                display: inline-block;
                width: 7px;
                height: 7px;
                background: #fff;
                border: 1px solid #c0c0c0;
                border-radius: 7px;
                }
            }
        }
        .images-box {
            position: relative;
            width: 95%;
            // padding: 10px 0 0;
            padding:0 0 15px 35px;
            font-size: 0;
            box-sizing: border-box;
            &:before {
                content: '';
                position: absolute;
                top: 0;
                left: 20px;
                bottom: 0;
                width: 1px;
                height: auto;
                background: #c0c0c0;
            }
            .than-nine{
                position:relative;
                // position: absolute;
                // top: 50%;
                // left: 50%;
                font-size: 16px;
                color: #f00;
                &:before{
                    content: '';
                    position: absolute;
                    top: 0;
                    left: 0;
                    width: 100%;
                    height: 100%;
                    background: rgba(0, 0, 0, .5);
                }
            }
            .images-i-box{
                // position: relative;
                width: 100%;
                padding-top: 10px;
                background: #fff;
                // background: green;
                & > div{
                    position: relative;
                    display: inline-block;
                    width: 30%;
                    height: 50px;
                    margin-left: 2.5%;
                }
                i {
                    position: absolute;
                    top: 50%;
                    left: 50%;
                    transform:translate(-50%, 50%);
                    -webkit-transform:translate(-50%, 50%);
                    -moz-transform:translate(-50%, 50%);
                    -ms-transform:translate(-50%, 50%);
                    width: 100%;
                    text-align: center;
                    pointer-events: none;
                    font-size: 20px;
                    color: #fff;
                }
            }
            .img-itm{
                // display: inline-block;
                width: 100%;
                height: 120px;
                margin-bottom: 10px;
                background: gray;
            }
        }
    }
</style>
