<template>
    <div class="item">
        <div class="images-i-box">
            <div v-for="(item, i) in filtersItem" :key="i">
                <img class="img-itm" 
                    mode="aspectFill" 
                    :lazy-load="Boolean(true)"
                    :src="item" alt="" 
                    @tap="previewImage(list.data, i)" 
                    @load="imgLoad()"/>
            </div>
        </div>
        <AdItem></AdItem>
    </div>
</template>

<script>
import AdItem from './mainAdItem'

export default {
    props: ['list', 'key'],
    data () {

    },
    components: {
        AdItem
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
        },
        imgLoad (e) {
            console.log('111111', e)
        }
    }
}
</script>

<style lang="scss">
    .item {
        margin-top: 6px;
        background: #eee;
        .than-nine{
            position:relative;
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
            width: 100%;
            padding: 6px 0;
            background: #fff;
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
            width: 100%;
            margin-bottom: 6px;
            border-radius: 4px;
            box-shadow: 2px 0 6px rgba(0, 0, 0, .5);
        }
    }
</style>
