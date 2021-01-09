<template>
    <div class="images-ad" :class="{unshow: adShow}">
        <ad class="ad-conent" 
        unit-id="adunit-9febccf65acb2006" 
        ad-type="video" 
        ad-theme="white"
        ad-intervals="30"
        @load="adLoad()" 
        @error="adError()" 
        @close="adClose()"
        ></ad>
    </div>
</template>

<script>
export default {
    data () {
        return {
            adShow: false
        }
    },
    mounted () {
        // console.log(this)
        // console.log(this._person)
    },
    methods: {
        adLoad () {
            console.log('广告加载成功~~~')
        },
        adError () {
            console.log('广告加载失败~~~')
            this.adShow = true
        },
        adClose () {
            console.log('广告被关闭~~~')
        }
    }
}
</script>

<style lang="scss">
    .images-ad{
        width: 100%;
        margin-top: 6px;
        padding: 6px;
        box-sizing: border-box;
        background: #fff;
        .ad-conent {
            display: inline-block;
            width: 100%;
            border-radius: 50%;
        }
    }
    .unshow{
        display: none;
    }
    
</style>