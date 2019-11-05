<template>
  <div>
    <div class="spotlight">
      <div class="spotlight-box member" v-for="team in teams" :key="team.type">
        <h1 class="title symbol"><span>{{ team.type }}</span></h1>
        <div class="spotlight-member">
          <div class="member" v-for="(member, i) in team.members" :key="i">
            <div class="image" :style="{ 'background-image':  'url(' + require(`@/assets/images/team/${member.image}`) + ')'}" alt=""></div>
            <p>{{ member.name }}</p>
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
      teams: [
        {
          type: '總召組',
          members: [
            {
              name: 'HrJ',
              image: 'img31.jpg'
            },
            {
              name: 'Deimos',
              image: 'img04.jpg'
            },
            {
              name: 'Chun',
              image: 'img01.jpg'
            },
            {
              name: 'ws育慈',
              image: 'img05.jpg'
            }
          ]
        },
        {
          type: '場務組',
          members: [
            {
              name: '阿軒',
              image: 'img16.jpg'
            },
            {
              name: '鯉魚',
              image: 'img30.png'
            },
            {
              name: '小草',
              image: 'img18.jpg'
            },
            {
              name: '野足',
              image: 'img26.jpg'
            },
            {
              name: 'Allen Chou',
              image: 'img26.jpg'
            }
          ]
        },
        {
          type: '議程組',
          members: [
            {
              name: 'blu3cat',
              image: 'img56.jpg'
            },
            {
              name: '地瓜',
              image: 'img41.jpg'
            },
            {
              name: '蔥蔥',
              image: 'img33.jpg'
            }
          ]
        },
        {
          type: '財務組',
          members: [
            {
              name: '腦腦',
              image: 'img03.jpg'
            },
            {
              name: '子為',
              image: 'img35.jpg'
            }
          ]
        },
        {
          type: '攝影組',
          members: [
            {
              name: 'Andy',
              image: 'img09.jpg'
            },
            {
              name: '家康',
              image: 'img34.jpg'
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
