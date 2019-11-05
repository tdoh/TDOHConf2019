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
              image: 'img00.jpg'
            },
            {
              name: 'Deimos',
              image: 'img01.jpg'
            },
            {
              name: 'Chun',
              image: 'img02.jpg'
            },
            {
              name: 'ws育慈',
              image: 'img03.jpg'
            }
          ]
        },
        {
          type: '場務組',
          members: [
            {
              name: '阿軒',
              image: 'img10.jpg'
            },
            {
              name: '鯉魚',
              image: 'img11.jpg'
            },
            {
              name: '小草',
              image: 'img12.jpg'
            },
            {
              name: '野足',
              image: 'img13.jpg'
            },
            {
              name: 'Allen Chou',
              image: 'img14.jpg'
            }
          ]
        },
        {
          type: '議程組',
          members: [
            {
              name: 'blu3cat',
              image: 'img20.jpg'
            },
            {
              name: '地瓜',
              image: 'img21.jpg'
            },
            {
              name: '蔥蔥',
              image: 'img22.jpg'
            }
          ]
        },
        {
          type: '財務組',
          members: [
            {
              name: '腦腦',
              image: 'img30.jpg'
            },
            {
              name: '子為',
              image: 'img31.png'
            }
          ]
        },
        {
          type: '攝影組',
          members: [
            {
              name: 'Andy',
              image: 'img40.jpg'
            },
            {
              name: '家康',
              image: 'img41.png'
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
