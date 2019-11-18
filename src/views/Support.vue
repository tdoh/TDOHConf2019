<template>
  <div>
    <div class="spotlight">
      <div class="spotlight-box" v-for="(support, index) in supports" :key="index">
        <h1 class="title symbol"><span>{{ support.type }}</span></h1>
        <div class="content" v-for="(item, index) in support.list" :key="index">
          <div class="card">
            <a :href="item.link ? item.link : null" target="_blank">
              <img v-if="item.image" :src="require(`@/assets/images/support/${item.image}`)" alt="">
              <p>{{ item.title }}</p>
            </a>
          </div>
        </div>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import layout from '@/components/layout'
export default {
  data () {
    return {
      supports: [
        {
          type: '主辦單位',
          list: [
            {
              title: 'The Declaration of Hacker - TDOHacker',
              image: 'TDOH.jpg',
              link: 'https://blog.tdohacker.org/'
            }
          ]
        },
        {
          type: '承辦單位',
          list: [
            {
              title: '社團法人臺灣校園資訊安全推廣暨駭客培育協會'
            }
          ]
        },
        {
          type: '協辦單位',
          list: [
            {
              title: '教育部資訊安全人才培育計畫之子計畫4：資安產業與社群鏈結交流計畫'
            },
            {
              title: '資安前瞻創新研發專案推動計畫',
              image: '資安前瞻創新研發專案推動計畫.jpg'
            },
            {
              title: '教育部資訊安全人才培育計畫',
              image: 'ISIP.jpg'
            }
          ]
        },
        {
          type: '贊助單位',
          list: [
            {
              title: 'Hacks In Taiwan Conference',
              image: 'HITCON.jpg'
            },
            {
              title: 'KlickKlack Communications',
              image: 'KlickKlack.jpg'
            },
            {
              title: 'TREND MICRO 趨勢科技',
              image: 'TrendMicro.jpg'
            },
            {
              title: '財團法人電信技術中心 TELECOM TECHNOLOGY CENTER',
              image: 'TTC.jpg'
            },
            {
              title: 'TWCHACKER',
              image: 'TWCHacker.jpg'
            },
            {
              title: 'ZUSO Generation',
              image: 'Zuso.jpg'
            }
          ]
        }
      ]
    }
  },
  components: {
    ...layout
  }
}
</script>
