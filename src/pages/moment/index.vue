<template>
  <div class="box">
    <ImgItem v-for="(itl, index) in wallpaperData" :key="index" :list="itl"></ImgItem>
    
  </div>
</template>

<script>
import ImgItem from '@/components/imgItem'

export default {
  data () {
    return {
      userInfo: {
        nickName: 'mpvue',
        avatarUrl: 'http://mpvue.com/assets/logo.png'
      },
      wallpaper: [],
      // init数据
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
      ],
      shareThumb: [
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghg9qagctej31900u0dlo.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghg9q8wnfbj30u0190jw3.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghg9qb1okqj31900u0wiu.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghg9q9sxmaj30u0190djz.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghg9qbpbvpj31900u0afr.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghg9qccs6ej31900u0n0k.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghfxn1nr1dj30qo13yjv6.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghfxn13798j30qo12nwh9.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghfxn2631uj30qo145ju5.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghfxn2n8g1j30qo14zjua.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghfxn3fyjxj30qo14jju7.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghfxn32mb1j30qo13wadq.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghf5gqv8g3j318z0u0gul.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghf5guaaskj30u018zag2.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghf5gsvdogj318z0u0n1w.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghf5gvtptoj318z0u0dkb.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghf5gxc0pmj318z0u043y.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghf5gyq7k7j318z0u078c.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghev5is4r2j30u0190jxo.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghev5jevdgj30u0190wls.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghev5lo7vgj30u0190wmy.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghev5mbtq7j30u0190agx.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghev5khcq7j30u0190jv3.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghev5jx108j30u00vj78z.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghe1ih2rgqj30u0190q6q.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghe1if1jhkj30u0190tca.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghe1ifnpf2j30u0190jw0.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghe1iiatojj30u0190jvk.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghe1igd2o1j30u018zn0b.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghe1iho59yj30u0190ae5.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghdl3bjxp5j30u01c8n20.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghdl3duhfbj30u019042m.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghdl3cz3tnj30u01c80xx.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghdl3ev8l0j30u018yagn.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghdl3g18thj318w0u0n1o.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghdl3hjcd7j30u01e9teg.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcz97lhp7j30u0190ae0.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcz98l9etj30u0190jvs.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcz9840lwj30u0190wil.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcz994pjjj30u0190gpr.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcz99qxbhj30u0167jux.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcz9abglfj30u0190gpo.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghctteqi3ej30u0190gou.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcttg5tlpj30qo10itay.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcttfokgdj30u0190429.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghctth4w7dj31900u0gns.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcttj7ho4j31900u0wha.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghctti36iyj30u01900w2.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcge0xzw2j30qo12u776.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcge017wkj30qo133770.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcge0g2bvj30qo14ljvr.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcge1e4kwj30qo12swht.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcge2bvujj30qo1310vz.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghcge1vsryj30qo12kwht.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghbol5wldnj30u018zaf5.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghbol87r3nj30u018zq7h.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghbol4zq3dj30u018z44u.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghbol33jsrj30u018zn44.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghbol3xo4cj30u018zq71.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghbol7cemej30u018zgte.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghbdr8f5c6j30u018zq7v.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghbdr4ypyij318y0u00xm.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghbdr65f4nj30u018zaf2.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghbdr74kg0j30u018ydme.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghbdrcch39j30u018z0vo.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghbdrf0u31j30u018zgpt.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghanq9le2wj30u018z0x1.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghanqbnlb4j31900u077v.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghanqabkdxj30u018zq7a.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghanqdk2zbj30u018zn0d.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghanqci68tj31900u044c.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghanqb0pmij31900u0whm.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghaj89d9xvj31900u00wv.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghaj8alvuhj31900u0n0i.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghaj88l1y4j30qo0hagnc.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghaj8b3dqaj30qo0gn0ua.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghaj8bjkaej30qo0wgdi8.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1ghaj8byfukj30qo0jumyi.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gha8gbs481j30u0190n3m.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gha8gdg9clj30u0190afv.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gha8gfqxtdj30u0190af8.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gha8gcrzcbj30u0190afk.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gha8gf3f2cj30u0190tfx.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gha8ge7y0cj30u0190jwp.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh9ijrpihdj31930u0wi4.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh9ijsbtfpj30u019341s.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh9ijsvil0j31930u077x.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh9ijun9mmj31930u0gow.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh9ijvk5fpj31930u042a.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh9ijtqfsuj31930u0q6x.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh9e5tewzaj30u018xdk4.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh9e5uaphfj30u018xdj9.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh9e5rrhd0j30u018xae9.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh9e5v892qj30u018x42h.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh9e5sj70sj30u018x77y.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh9e5r4kv2j30u018x41k.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh96b8nvtlj30u018xq6c.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh96b9j8psj30u018x790.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh96baefzrj30u018xafk.jpg',
        'https://wxt.sinaimg.cn/mw1024/005DvLO4gy1gh96bd8yi6j30u018x0wz.jpg'
      ]
    }
  },
  components: {
    ImgItem
  },
  computed: {
    wallpaperData () {
      return this.wallpaper
    }
  },
  beforeMount () {},
  onShareAppMessage (res) {
    console.log(res)
    if (res.from === 'menu') {
      console.log('来自menu转发')
    } else {
      console.log('来自页面内button转发')
    }
    return {
      title: '',
      path: '/pages/index/main',
      imageUrl: this.shareThumb[Math.ceil(Math.random() * 100)]
    }
  },
  onShareTimeline (res) {
    console.log('object', res)
    return {
      title: '世界的美好与你环环相扣',
      query: '',
      imageUrl: this.shareThumb[Math.ceil(Math.random() * 100)]
    }
  },
  mounted () {
    this.getImageData()
    // this.getShanbay()
    wx.showShareMenu({
      withShareTicket: true,
      menus: ['shareAppMessage', 'shareTimeline']
    })
  },
  methods: {
    getImageData () {
      let _this = this
      wx.request({
        // url: 'https://gitee.com/white_/tumengData/raw/master/data.json',
        // url: 'http://qej34q4yf.bkt.clouddn.com/data.json?v=' + new Date().getTime(),
        url: 'https://try.gitea.io/0xYuze/wallpapers/raw/branch/master/albumCover.json?v=' + new Date().getTime(),
        data: {},
        method: 'get',
        header: {
          'content-type': 'application/json'
        },
        success (res) {
          _this.wallpaper = res.data.moments
          console.log('res:::::', res)
          // wx.showToast({
          //   title: '成功',
          //   icon: 'success',
          //   duration: 2000
          // })
        },
        error (err) {
          console.log('error:::', err)
          wx.showToast({
            title: '出错啦0.0~请稍后再试~',
            icon: 'none',
            duration: 2000
          })
        }
      })
    },
    // 获取扇贝每日一句
    getShanbay () {
      wx.request({
        url: 'https://rest.shanbay.com/api/v2/quote/quotes/today/',
        data: {},
        header: {
          'content-type': 'application/json'
        },
        success (res) {
          console.log('res:::', res)
        },
        error (err) {
          console.log('error:::', err)
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
.box {}
</style>
