<template>
  <div class="snap-box">
    <div class="item" v-for="(itl, index) in emoticonData" :key="index">
      <div class="date">
        <p>
          {{itl.title}}
        </p>
      </div>
      <div class="images-box">
        <div class="images-i-box">
          <img class="img-itm" mode="scaleToFill" lazy-load="true" v-for="(item, i) in itl.data" :key="i" 
              :src="item"
              @tap="previewImage(itl.data, i)">
        </div>
        <div class="banner-ad">
          <ad unit-id="adunit-8ce1d72d244ab333"></ad>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data () {
    return {
      emoticon: [],
      imgUrls: [
        {
          'title': '搞笑表情包实在太赞啦',
          'data': [
            'https://mmbiz.qpic.cn/mmbiz_gif/G6q4IkX6uRWF2kib0hTJ4JvGLyQNF6OAa9qtsWvj3YY4ocl5fMy8GI0AvjFtGAMTyD7XPLOQsBqxkKPBhEX0wdQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/1qrDNexAdLibocWN3bibC8RYVeHw2hicmKRKNvLcicbecgeKle1nBY8HoFmbicia3oqXmegmubtEXuAPPKbqPGtme3ibw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/1qrDNexAdLibocWN3bibC8RYVeHw2hicmKRNqMtSMV23NHPhgJiar8MlqorAfgvjTfFBicQHFPVZVZGM1VyC8zYCricQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/1qrDNexAdLibocWN3bibC8RYVeHw2hicmKRkZJXdu2Lz5rh8icg4E5BkBlhKbynX2X12tFIiaFJqCoz0vO1JE68I3rw/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagpYJ2EzwXnXYUhTQN9JmYBHMXDHzI9T63p9yKPBk3sHZOek3xePZo1Q/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tag5Zej6GbNR2TZchKjCYFsP7rq5pXEqibBnSq5CYKn6dZ8ny18icTYO1Fg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagObgAJhnZNeSNJcaicx22N90L7nmTWZMJpcOTNfmyyYJEI9qt18MDiaEw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagSAXa2J7e7ibQ7Yga9N32JNT4WkyuekL6p0VicSPJUAZkHsu9pMiaSLXaQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tag20IAudQJiaFcJQlnwINScnH73ich6OhlZ6s4F40hm0TwSNNsQlV6ovAg/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1taguvu27HKtAJh87gPsSQpWV2dfqex5H8zjXtjIUj6VLuPSIelPNabTSg/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagvrFialvCSqAcVZicOrYKGUHPCvv3N9IibAjSNCWngDsD6NjO5TY6GVU0A/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagVTUnAjUAPiajmhiaiclCYrqmURRYo97KsQLxTLmRm7FBojicpicGzNBPLHA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagdQicVu3l7X5HXrMwLAvmT9WG51HibxeibRTxEghadpNgEAGQ8iahVoTMUQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagv9exfzjOQ2YfUYseSEuSD8s7L2PcSlIxYFiajd8gGBhk1ezce5V8hrA/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagPhcDSfJNJ9DDfSSBXUxQVHb1nwEShT90AicpXtbHmTeOiaBzWlCpwNjA/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagsJiaRaKibIIFCNdcaOkI3PQU6ktlR7u95RYmpo8HJaPjyiaAzQQjI9ib6w/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagh2aDW4DgWPKjlEc9j3PVHeiaTicZsgoibD2DuVicfeA61B0g0yCDU9doLA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tageKvyKWYV8yMUxBtmXjDjUEwKzA7ThdFpZm2O7Fkicf1yhH6QHiaDY0DA/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagkthLdtuF4wnib1Nu7nkicgb89HFRqsoYe6bdNQBaqsCpAHUXhxnBe7aQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tag1A2cYD3MicmxX96NGt7N6VwK41ib4qdNNE7yWVtgpx3VHJMicYr26oT0g/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tag6pX20Jzld7dKVmqvgV3vAXERz7S87JkTfbyQ8YOXLBzR3Ml0DUIia2w/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagzpj2upyFLQ1jzpziciadAmXEqqcDic6wHLKmnCcEb8jbZyiaU4iac3cibGTA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagC4AKCdqSXtalHnWlQAiciasnqfVfoT4cef7PqvJrJNUX45Lml2V0uo5w/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagxp7HqMuGXGlqSp5UmrmicKlGCG7AgDSedMTicHvibxnafR6M0zibYgmHKQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagXZoiam23zDguibkKia333iahzXt1icZhk0VV0ft5R2KWfoAghjDOFUbP5Pw/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagEEtianwKFrRysphUdeLM9j4adgZcI2Z18ERDqMeWWSc6RicicWuBKIjCA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagdjwv8fUNlvyPP1RdefPdRiaANFV3qT9ko2TmcbXgUF0grVIT1KjZF2Q/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagRuFiar6Zs2dATxfYhnWfnN0JGTfWWUy7YwjU4CpsCDFxX1JhqfR8U5w/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagf8V4CgreJM6wYqA1qnfMMmDpHwg3YIZPBpiaOenWORvAhIbTW3C19NQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagKhvIUdrpiaxNdaS3ibJRoQny1edVYMsicvg52hFUZ3iaCMguEZYXia7pptg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagJibpqb0fRLBK0MAYc1XCgnyDaib2DpGDrW2n7PKDiaEe90l84Mot18s3A/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Y2uPXMia9icasePfibmicLyhKRtm3YwVPqg3PkUbxhfPyBdY4x14cBmHLkQKxpX8qs2ibkIicX9AKMFJAwq1qFj4YHZw/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagpG6j4n4giaz0rBk2z2wzsthaWUaWs8YZODiazDs10nwVzMVbc2llG89g/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tag9sFLfg02Dv0LicGnLp2GxiaSS545y03g5Tqu0EQcybfHwuKVWMDIBKCg/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagzMB8DicvgrU6IWv59QUfz9iaicsRYJn3DUDlXzXIzKKBvyT4p7M1iaQrLg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagG0l1YUNnL4dQibEMLCkDqwAHtK5m4qonbiaic5QOsPSicPtzp5ZV8ic5DRQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tag1BOVEwLJChPgH4eJOVUqcjDEXia5E9HkUDPul9ZIGkyH3kg8U7rBFNQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagmpC2mGwic9eyWTEstGNpa6K5Gyuy1sMOib3UOqVVOJnmogJtjQ6GOAtQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagqL7iaWo6VmiaaV9loTe1a2OT4nNnU9eL9Giczdl93f3ZJGpptRLNAuFCg/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tag5yc8vhmJibkWdEdSPNmezfpEAyDFibvfmOMq8fkHJFj9Cb24qXUOSgmQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagUsymZgU0LrTnEu24MaHialNbHIMtcx7icVvAWu3GI006c9qwxOgQCffQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagqB4icaD8toTYiabjQtagclamiazMfDGn6qvv6nRYDricjzub1icCbTlnDCw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagalibyRIdE9Hosw6HcLB4n6vkISpkkgIbqM6dpql4aAYXyhKZmsnOnEg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tag8GC8ntHfman8OPvic1bHXPtQkR9qR6qEbn3MphQe27DRmeD5XbibGjNA/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagZrXKTVmuibhSVI1tdiczYVaX2Ticou7SBJxJjK8gSpHENmnicIgsLjfMicw/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagGeBiaCwx2eibkibb1mo5KYagkFx5oxhq3FEqMwPZq7nWbiafQcP0iaYYb2g/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagSqBlaYfIJn2bfRZmqZS3OvyuvNIp4qnViakK5wfzhRLBTaBfFGg1iazA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tag8BFiapODsfpOhxwGHytqqlESMvjRLqp8drcv5EAGuKdlP9qpdT2R43g/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1taglCicRPSibVOgbicpCpZLCoLScDUJDztm8Z3MFGdic9Jk5YjicUqEXtyc7Ew/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagNMJKCJCbCW0LXUtmjD27jgeYa1UNxXibAow4AhzuUKVdfhWicH4PAwpQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagDrMyUonO7Aic6mYjKvVw6VsQicCrgkksIA0vkKtfwXGH1ekmY6dTMQkg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/Y2uPXMia9icasePfibmicLyhKRtm3YwVPqg3fVO46SqwhRLib7qTFmGhlQ9IQh6vcG3jHZKyeMF0icsAhOBlDzWHZqHg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XNXcj9ibyfnPudmXtmoSMmqmicGniaTic0blqDC94voZ3QVFPJCI6RY4KfQuKKuBm60umSVEFI03TombQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XNXcj9ibyfnPudmXtmoSMmqmM3AdjEUiaD4sBCzlXhs23xlULvrEkyQFwAclMfDRfz2lq0ictrxXHF6A/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagd7M4pOuH8fVkTrmAnaCV5C8qTZWiawDmlyhqX3a4WbR8PYckVc2qBJQ/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagunWuJ6IhTm2xL2P5PweGBx1W1aT35XpCKkOAqXW3Be1v9gvLukhvMQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagaQ8D5ibD4wib0nOjknEzXwtXEricQVjqiabqYjM8xKyBYkjKBcpibVLvSIA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagYt6yuicGtwP623Vs4rNibMvlOlOibkwsckbZvy3WcsfdB1e7Q4elOxHAg/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagH9icdTTib0NKD2J7j0c3ibxiaDaJvicIS4AibbwoOpPGJibDb7OcM1L42AovA/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagjfjxI1L6Mk0Uz5wMZ1QIvcg5OvUKpWVL4FBe5JcToQOwpoqZEZTDgA/640',
            'https://mmbiz.qpic.cn/mmbiz_jpg/zBHYn5VU4XOh3ia86JtMMGm7xmheX1tagaAunpc6hY5nUn9WFibLthGboIfAlJy4iceoVG5fgRII0uA6O6x0f7yIw/640'
          ]
        },
        {
          'title': '来康康敲可爱表情包',
          'data': [
            'https://mmbiz.qpic.cn/mmbiz_gif/G6q4IkX6uRUy8bib2GzmulImN6x49d9bUe3llC7ek23I7ediaVSE1y72Y3cZgWvgORa93VYfF4g78rgRZxLicnGhQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvEm1TJ0dpKvD92U8ezE59SIltfeuw8ib0JGhgATP6KErFu1stEArFaug/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cvzygen6bbIlcClAYAYnQkpaoUtKnRGOS1rcVtw37FvY3oQMyA2k2LZA/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvVWwBwGbfL7ib9gia5xSZGMnicRA84A8LMj8wWHiap5fkEDo4pia8icmrbqwg/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvLDOwKcZSic9UWq7lVjH0lBMDP90QQ9sIPWCXKSgOVYLhA9XkqXuI8KQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cve53ib3rHAFibu2FjAhfuxhjX490OqWuhoqyDILlWeKjwM0n7kX54eWnA/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cvd4RawqdicrByynb46O4vF52QCwhUHV0BpDfAmIrFdzhH5hbQPx2qBsA/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cv4P3yPowMfaWoib9ibLLJGfrRf7XWb9y8tbb188M910gWJibAxIlmZBQuQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvEtrztl7Rf1QseyV5eUYHtWKTL9RliagATicuLIhf1L9s7cBnGq4dEyBA/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvUeeLOC6btgQdOfiav8ic2cYNP2icSCREY7TlMV1nOhG9TNLa3jkMTILuQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvaIbtJy4U7RYqCt6OT3Ldf3SOCd37cf8pJaXBIx2qXv4rG2aRBYhJiaA/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvfDiaqu7y4W0KQdyWTG7g8P3ITiazmib3icCqyMokIuloNl792kCiaJ7ln9A/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvHLvzsRysxJFArjI5oB8iayKmUtcYlYeDbjn7KVCmK5MQQ1UMqtDrLrQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cvy6rVhJY2mXnCVicwdNfghyZanjy1afbA1eiaaTUHia9DumiapQ0lyQTpfQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvdOUNWia49o8IEJlnibOSaSOmgpkt6qDREfiaiagdeCCian9a1Kuo8iau29iaw/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvahhficbrcIMLQaqZmRib0JkE50QumQJiasbiaWDT86qLwd2FoKKnib7wzCw/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cv0yopicFydPYqgkj7ynRSmwHY4BqSgC3dO437RZTRRXXZeAYW2tKia0pQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cv0WUzYibhmQiaA4ZP9OZJibgVhj5DuDnR2KrjQxIZ3yNEjHcrMTeQCBDPg/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvHNgk7M501QOWECye9gDelNvr3Pmz4KaFAnHrvEHKgsBf7hYTPDpB9w/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvibuviaLpUpM7BiaA4PebBribAxhltG3Dk2pg1svAcj5ib7pXZ0oOIUpO6cQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cv3ibpMCTibgxaKBnpAqAxj7iazfbUFPAlqCDcvWue28zBhAXB1cth7RNibg/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvDmDPGeDfLO6ZMwJwZEeJycmXQZnXqSsagGNY962Wicic5IfEPPX8r5Ag/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvejLmXt8GApP0icCzvPBPcO3ibxkDjbIrnHlamALrW1qtUdczQ61byBTQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvDFibrxvxia9jVg3z58tEYrGwV2N8OuveQMQUp3h3IibSjcQVXgicLhu5oQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cv4MlQqNQSIPFmcIZTd6sdhDmW86etA9rCngKE8lWA47Ctib8WR0ImQkQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvXsgqSq1K7Dj0zB8OITW5xpoVugv8icueYQllKHmictX5BZNgdtPh56lw/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvVpAeDqItCNkn8KBVE41doib1DMgib9YLD6HBiaOJElibO4YL5HXxcsunnA/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cv0ibEBOiajichu53FhT0ib2uImEB9cO1YjyUS5uWNJQ9WRplCWKn8SGfibjA/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cvibob198ia42AkxjCteAsX6yPZ7hT81p3ia73QgKpDAODC7ZMrGcMluzRA/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cv9pNjAOHcdZ7CJ95WQYmicEQ2bgTdnfK31pQP12JniaO6F6pib4d9QBptw/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvibgrkRE4otHZcj3PdDxRbmow2OU9jfjia5HudibKfVP3bQFaFic9cFC2Sw/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cv85PErN7SwuFET28naXvJVuzGy2DQYDQKwE9mtoqA7flgAZSoRI3vfg/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cvtw7kia9xV1VibktaWXzia3zdWWWY4VJtq7JIfFb7KrRhXg9dVSDiakGMiag/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvK9ewQmWA28RhvAryHs5g2XpX5sSspO6dH3ib0ePEjOGvfD2aK9qoRIw/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cvl2rflmU6CiaWElhIrHBuZvrSZncwIFI3XhRDIcauhcYwhJwia2O4ReFQ/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cvu1zooF27lThVHibRUHw1AuicIib83E7OIg3dyWVdic9jnNcicNFM79qQQ6Q/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvicGzWADavGRjdLibDYnWJozSc8ibicWPiafRWl5nHBqLTIqIVOVT0ZBOQxg/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9CvTntBs22JRPwvvjL7aAoYd6iaC3LLZE9kUZSb1k4G5hyRwMeYRThOtqw/640',
            'https://mmbiz.qpic.cn/mmbiz_gif/Gg2r8wnwlP2HJhS4aR0yd9OwKUeFX9Cv23XM70407QsVDBtvLAr3seIWvVMtmLiaqk87FDGhiaDgegzaKN97vxSw/640'
          ]
        }
      ]
    }
  },
  computed: {
    emoticonData () {
      return this.emoticon
    }
  },
  components: {},
  created () {
    // this.$cookie.set('test', 'hello world', 1)
    // console.log(Vue)
  },
  mounted () {
    this.getEmoticon()
    wx.showShareMenu({
      withShareTicket: true,
      menus: ['shareAppMessage', 'shareTimeline']
    })
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
    getEmoticon () {
      let _this = this
      wx.request({
        url: 'https://code.aliyun.com/392958774/tumengimg/raw/master/emoticon.json?v=' + new Date().getTime(),
        data: {},
        method: 'GET',
        header: {
          'content-type': 'application/json'
        },
        success (res) {
          _this.emoticon = res.data.emoticon
        },
        error (err) {
          console.log('error:::', err)
        }
      })
    }
  }
}
</script>

<style lang="scss">
.snap-box {
  .item {
    background: #eee;
    .date{
      width: 100%;
      height: 35px;
      line-height: 35px;
      p{
        position: relative;
        font-size: 14px;
        text-indent: 10px;
        color: #FF88AF;
      }
    }
    .images-box {
      position: relative;
      width: 100%;
      font-size: 0;
      box-sizing: border-box;
      .images-i-box{
        padding-top: 10px;
        background: #fff;
      }
      .img-itm{
        display: inline-block;
        margin: 0 0 10px 2.5%;
        width: 30%;
        height: 120px;
        border-radius: 5px;
        box-shadow: 2px 0 5px rgba(0, 0, 0, .5);
      }
      .banner-ad{
        padding: 5px;
        background: #FF88AF;
      }
    }
  }
}
</style>
