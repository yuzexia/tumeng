<template>
  <div class="box">
    <div class="item" v-for="(itl, index) in imageUrls" :key="index">
      <div class="date">
        <p>
          {{itl.title}}
        </p>
      </div>
      <div class="images-box">
        <div class="images-i-box">
          <!-- <div v-for="(item, i) in itl.data" :key="i" :class="{ 'than-nine' : i == 8}"> -->
          <div v-for="(item, i) in itl.data" :key="i">
            <!-- <p style="font-size: 12px;color:eee;margin:5px;background:blue;">
              i: {{i}}- Number(i): {{i == 8}}
            </p> -->
            <img class="img-itm" :class="{ 'than-nine' : i == 8}" mode="aspectFill" :src="item" alt="" @tap="previewImage(itl.data, i)" v-if="i < 9">
            <i v-if="i == 8">+{{itl.data.length - 9}}</i>
          </div>
        </div>
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
      },
      imageUrls: [
        {
          'title': '文字朋友圈背景图 | 7.30',
          'data': [
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DtMpfdbj7txe0UQib2IgzRaUT7VULWthpEUXD1wwDO54F6F6Q9iakb15Q/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DaGT0VJKC60fx9v2R4nywxVRRtA8ycJ8EPdTJwdCc0cj8R2DQ6flOUA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8D1AIxwpmjxJLXrAXHnpuxQF5OGCGXDg7eImCINsAibZbCibwpI2YC6ib1g/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DfiaP03gnYEpeFXoodnicUMYNicpIyrKxAJOem5psicjianNIbPt4ZyuZH7A/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DicJzwiaDcWRlzLMO6AgT2HHRAtgXRelDNvU6mjoRvQvZsfkf1N1oT2lQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DTb0nwue0IyzK4p10AZdw1IeicGYo0fqzQSicduOWU0efLVv1aGf5o49g/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8D8wojyYZGD55rLnCXVXcN4mQcibsR0W404CMveQotRTz36n8QDlX039A/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DI9vX5txvqYHicYUaXx5LbyopKibjk1gfjj7jLxJNS90FudHlzwoW5dpg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DiaZbW27tW77Oz3UkMqbVsyibFuYfOXIiaaETJt4cH0Y2XeQDBS7mqXUnQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DfteF5gpensGYI8bsXh4xfhud6wG53o91n44maCP6rXXxE5yhxAkwyQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DibWSoWXuESyGYEkyt5nldjS0NEJ4GL7VdRBMpwrYfxHYgIDGu6SqQjg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DNpIC85QtFXOXECEqnZKYtqebTIVjiccRwvovP6iadSOTWJ21CmUJiaQrA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DF3Ct0BtIrFLzuFzya9rpw3Te21gbqEruvWiaVco9lAZavcNQrAW3NRg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DVNdsNWse12QvBnQdpXlSQSuCOOY81vQ3LEdQGtibzy4S2SnKBUeBvibQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DEm7kfWeIlTwGS5PW41u4RoaYeQic74ic34RCDhbZG9ibJk0kAy3BR0dUg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DUyX9IkptM177TkoTcLGV2hicKCJu8kkUMI5LgcnQVQbibWRNEAZicZGBQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DUW5ecouW3UzaTv4QXUKHtwTbOCNh8751ezpYAHB4lePPFcmqsBuPmQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DQibUgm2wlIROIys53ZH2YcIZLwyDn4RVicwBFJsm0ibwaicibJ7m5qXZkFw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8D1ayT9usq9Y8JCNicQnt8Bs5Y6ayHZYlp1HVvmQJnrKETaE0c2ItgFBg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DLtVUcN7EnU1SgictmIUiaxhiaVB2JOvxX40uWL7drIAibXKlCeF4EMmoWQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8D8KLrJu96hqqK1ibD001qLdic2ibia6oicNP2TJJpK8bWdOMUpwHk9A4q9iaw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DE5VMc5eSibzSrGOibU2rof1XjdUYpSFHn0YxiahbOyrD296Fhn1LBvETQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DjicyWKGpYvPpce1ylUbgkj1gJiad4PymDs0E4t8LwMGibatSS9Y1tkiaaA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DicJlgN0NURP5hM4Tt61qryicQibLTVvB8ia54tJialWzKdXBCxv8scGeuiaw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8D0gEPc6ibjaQibtibDUiaKeYKVQVcj9mWlUnM2r62iaiaV0cssFYGsuxyicjjw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DLlRB9WCKKMqp2JibSrXHwYCvrYEqlP7xRpYpTQ3m0gwjico6ibd3m2AYg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DcicNI8b9s8leMUALoQqgWIRibYX0vicAgwGzv1vs0zY1F4ZkhQeuK40kA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DXb2ZDAuQy24C63cKCfvibmzianrkkhGLLjtgMicHGtEtglJCk4SWt7Wkg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DnGRS1ZeC3ojl4WCUQqUINegDQkz6vmarkhHMXttl9Rsbw5ic315kNMg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8D9F75T8DAdZv5O5iaUClIUdJSvpibgm7sZXibVLAR3yQn3QeepKiaJoU2uw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DpiagPOAJicdILtUZqoeVd2zJvTlJB2ObJQzqoflDU4zVt9Xic18EFVvTw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DAc8ChDEQjV6bMGIPFVPUtVCaUUBCqU5EHGBNbWSRC4Gqdemg55hvnw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DG8ZmhqEHiaLojMmSd5z3bNjQ9AzBCLnKt7iagp6O5VlDg3xL1LUymficA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8Dk2lMFicleefT3DCaLoSVPhMVQ3o09reqdNlW1U4HI6Ya0GVRcFJMvlw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZdgdaglLQF04lQfg77DGh8DlaqJPIHJEODcmlJfOq8WplUmWwyca8hIJ20ibKwibmELCWNHxpaKZFxA/640']
        },
        {
          'title': '文字朋友圈背景图 | 7.29',
          'data': [
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjrLIbXonUXKx1ES9Hf5c7j4jojlnspaHiaibWFV3CvMeCaYr3zcUSoU1w/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjOz2uHaBc02ppohWAO2wuaibrlL1PgEehkY5gKiamdIyA6laiba6hOp2JQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjSfh0UY6GrBrMqwnSQiaVx9su8JuNz2O6OOF0H8UOvTibON4Jg5CLH6Tw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjlJvH5D6QpafCvTJF0EKPicyBP6vlgaStic5gbkbkeW6JtIRodP6SkDaw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjAjbGvZBlWCMHC3PB7yicOxtml0rD9uREVTuLe5ia1gicUnjOAfETguhsw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjFjNHL7srRfQPTbMbMDF7JKl4NribzoIpgGsY6I27nvmeg0cbXfqe3Bw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjZpcfdj54DbGTVtic7viaicV4b5IzwvIdvJasfNqECJoE12cZUibuTiaPftA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjR68iaibNsB3E5ZGUyPF2fM35ldBDy9zoJh1dGnFBiaLZJSiaYgGHUMm1vQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8Qtj43kd6UQUTiaOtHr8jMcnsan5HYlIN07LaicZic5EXr7JxzGkdsQYds5lw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8Qtja6x60GN0qNfQ29ACBVDTrp2ibaHMbs4nZ18RcH8AQHTQFs2ZdQGsUug/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8Qtj2HpMpzRSvXqP3RkxSiaIiaHsEtQ5DiaPz5hFjLiaPd7Rlic4JZyXicEs5C8w/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjCAnvltPRm1EdxwY87DCxhOJksb3kgia80M5hjWBQu71DmIxYD07qwibQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjqHhZg7C2UFBBqAL2lSfy3Tich8shjTiboPgH5qCDib95cTDYqpbRmiaZ3g/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8Qtjpf6kHn0fdEzs67ibAZP5t1yH9UP9X8hy4Wibt7twLnQQDYI8gw54HKOA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8Qtjuh6VatrrGkib03JMebXEHbfEB2nygpoktC22HBddibwbhcMk16Ms1mUg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjxUaemmEpniazrqDOxdpsaB8Lras4fCN1YVf8UzBDicNQlzZRibAhffBdw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8Qtj82VicSKISLmMg731FkuaVtDAgsEG0xEtBCDnlhaR0DjcTibZwgjzXOXg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8Qtjelny0QeyueKY6gnYSqlKvMiaTibMGAuZR6kY2K87nrgSwuOK1ZrHI9dw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8Qtj5rmCoQ4h1qCFz4ESKaIC7EsyBONXiaiaibicMKPAXicvDic80OwhInQlzyRQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjWTTqziavMdpRgxb911zT3xALdY81NicIYmy2k0HxUqZUU9ateiaTODZLQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjEHxK7VFJZ1h7qZ35rdTPxV3v0hr0UpZK5nXsJkBuMspyIV4nrSTyYg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjUztiayiap8HibRHnSEcQedja1waDAsZFP3d5pU6e80Cb22T13RhIc0mQg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8Qtjf8iasWrUdmK1TH6Riac1XEZnpswArMpMJ3mR4HT5RVgczEFZRCsQfpaA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjQHyymDePwibWvN3qN9VnPw8E2tWo6UrzwGqy3Zsyx9KAzP2d3uIhE9g/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjXyZWbDg9CKFxKqGrcuorvLQnBGANtrGlibpicy4XUYcJLOGyPoO8XmtQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjpGMk6tpySRoC8kKicGne1h7OxCWKBibYng4uCFIOnibibtmqEyjmzbgF6Q/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8Qtjrxy3QWJGoibRDmWmlFavFf1RFGXqgLGC86T0hlS0rAribtPFFia0SSUow/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjtlepGvPGWEoFTOIzC7at3liabiadeaFCXpVP5cKJCJHgzdZLHHND6CGA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjdZe4d9eas0L1NBia9nCzNEia4iaWYGSf08TQgibYNf3diata8ibHesemBphA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjbBdCWdIEMhr398GGiaH24BQekzbeCSRn8n7R7OY5P55gDiapBTT3JusA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjGMndCibia1A7yl6ibrzKCAQiantCeAcFiaQvxeSQLVicHFoyH7bnULE40CEA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8QtjOZ2yKlkFbOhhqgPgdCYGeV2717OTV8QFO6bM5emBA8mec5fkBbROOQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/AQSficibdQHZf6piaPB1YAVNh8eBHUib8Qtj93YJFFHU8M6gCl8Aa4HwHITaUDeF6pT3Y08wJh15JPUZGicIria8O8LA/640'
          ]
        },
        {
          'title': '周杰伦Q版专辑封面',
          'data': [
            'https://mmbiz.qpic.cn/mmbiz_jpg/8lGciciaNn9R9W7FBmw3SShD6JajNjCwTCicVDgOCCDEpPHGRKjxicPWiblrPOgpckyznIpAOj7cwKYlficZbcp9n9YA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Up6TXOHtwgIdYXZicevYbFYPh4dFZ32aQY6ogib1fmRdUSRDZpge8KS2DyibWzVXBhLzFCpd87iao97iaA43oiaaQkQw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Up6TXOHtwgIdYXZicevYbFYPh4dFZ32aQpOTZ8fOyMEdZVwdRNWfahI5lHvyVib3ygNnl7lk2g7n0R3F67lbhexg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Up6TXOHtwgIdYXZicevYbFYPh4dFZ32aQia0pURUaFjZ5eFD0581MqQQ0AIyclEuMicYfEMoA8Mn9s5wonGGJFbkQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Up6TXOHtwgIdYXZicevYbFYPh4dFZ32aQ6ibibTicDgDRKIbk81YvHwl3lK8a6Pv18ruvdL9gaQeYPrOjq3udCaib0g/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Up6TXOHtwgIdYXZicevYbFYPh4dFZ32aQ7ZyR4gThhicsicN3VmAibI1GbkzAKGF2XCHcEgZNdc01evaI1ezbRv5Mw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Up6TXOHtwgIdYXZicevYbFYPh4dFZ32aQ7d7nufC3ib5d3lRQ1qearFgV96YfApZom8nblb0lG2vibibILic1TO8dzw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Up6TXOHtwgIdYXZicevYbFYPh4dFZ32aQcSEsrjm5gfmr0KIuMSh0KU2ylcicLxOECpjRF5GrfWW2ChLdYDylYjA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Up6TXOHtwgIdYXZicevYbFYPh4dFZ32aQcTIWnichAL5NNKWfLJn4xuMOjyQQgxh5rta0OjDEFiaicXqyyDYzCsV3A/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Up6TXOHtwgIdYXZicevYbFYPh4dFZ32aQPB5JMu2icEmfEGgXElrDOqB4zPxJtywZX18Zr06NUsafltCxFqplCCA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Up6TXOHtwgIdYXZicevYbFYPh4dFZ32aQxiaZjibs8rWBEGdxOvSLuP0JMwB8oxUv10YBKEVTpicxwqleibHfufpDIQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Up6TXOHtwgIdYXZicevYbFYPh4dFZ32aQXbxUBu5YHRSQEcosFRbCPVNJtTtII6tFXNibNncqvZUBrOnJyyukS3Q/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Up6TXOHtwgIdYXZicevYbFYPh4dFZ32aQU9LyO2YlEroees9mdX6xRiaED2ejnk0HRJVGDWD1cWa27CnaFicCPSrw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Up6TXOHtwgIdYXZicevYbFYPh4dFZ32aQz06n37ibEUyvX6LJLRL4u27ubWLB7ETITB6iaAO5kWKib5Pt7lKJypg5w/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Up6TXOHtwgIdYXZicevYbFYPh4dFZ32aQoFVAib5PNapic8qLvOEVzo7WAvwM5PGlFXalxGtjCGlSlUE45jicZcgvA/640'
          ]
        },
        {
          'title': '壁纸',
          'data': [
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAaia9P88cRJ2U6ckcskudYiaLaEuAvzaSpdC9exvIqUR7OjfcGcPd1xnJQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAa15xVyz47wRffL8mSMBlicJFQaaykGgurUbbKKWZ7D7rdD9o0apeFsCA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAaCEVUd9dicybUibgpyOVwR6h5LG7SgdT7l66GgQRz9ZHVqrfh9xJYPVPQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAaf5ePzmwyrU3Tjsc2oA0x9tn8qdE8fZPanRMiciaHfKiawDfAl7LH68gicg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAaZMCjkdC4MS3LcD6MlUQOcXA9vheadw7j3YXbNHhca57WAf7HJCTIyw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAaW39GHvGDaz5FIVhibwz0JLQNgBv39xxSmhEqtZe1EldSpkFmAwUT2fQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAaFIqhWMaThNO9QrPA8MicwkghZpNKPL1mDRjrPGAT06KlAB3D1HN6BMg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAatGzpfrPaCT06333Yx5bkOmwGPVWQFV41LH3EL5oTJY7XLKGo2mrUrg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAaf7H5hutvqRXadYWGvmXNk8lEtLcXXevudicqfAVusjh94lmJbeGRB8w/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAaP1FicjNqHlkNyic4Yzb2Qc6GMOSpiboeo7TGW9XuuiaMzQmUhG6qZIPLoA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAagd1ej1Eg6mSB9M2YxT8icg20PpBkH7KhawovpDJ8ybEDfsOndEAaUvA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAaM2In892Rc1j8agcsQhZ8lUZCOX0ZLDoUIFdXdMZJzwKvTyv6tONAMA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAaJiaEiaR9ZspLibxyk9uiaWPDMqQRDtmFTx6vKk35MmMgKvRYAthT7HKWdg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAaCc9OMYXicDdg0tI6OgS5lyJ0uTeWw1bAiaatHnzcyYYb7G0F2yJEGvog/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAasd1EibfKqpPGnCwME2ricGvWsB3EXwvjicd9fiaKR49H8kNPiaJGCp44picA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAauX7SicnmSg7cw6R964FH0K2Kiaodichgh1qvCcRInNxZuFNUshFibeswBQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAa4JrmuroAjnae0ZIPhhx3uaOjlhpe0cwabXdHG0wUB0QrdHf5tulkwQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAa1Z7sKw4dHTBia9aPm7hvwFdPjDA6s94OUjdUrpThfoGAJBV0nOUFetA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAayZ9Obn2mZHHZqt0WlanXibNu9WgHBibibf1Nfz5Tpe2I8aJSeicmMnHXtg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAagWqXgvcmxaRvuiaNO7t6mENYcrQa8zYcYg8kDg9AaAsDbPJJA2GaOeg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAaKT4qgpgmXl9JgETQdBW0sQUbJ8giavhgG5mMgDDBSRFbjbTxEz8oFPg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAaAthmNk9nsvhpnh42cICkGI1Tbjn1kYamP5f0KCiaHEa80xYb2yQ3rHg/640'
          ]
        }
      ]
    }
  },

  components: {
    card
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
  },
  created () {
    // let app = getApp()
  }
}
</script>

<style lang="scss" scoped>
.box {
  // box-sizing: border-box;
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
          margin-left: 2.5%;
        }
        i {
          position: absolute;
          top: 50%;
          left: 50%;
          transform:translate(-50%,-50%);
          -webkit-transform:translate(-50%,-50%);
          -moz-transform:translate(-50%,-50%);
          -ms-transform:translate(-50%,-50%);
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
}
</style>
