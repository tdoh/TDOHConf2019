<template>
  <div>
    <div class="spotlight">
      <div class="spotlight-box spotlight-table">
        <div class="event desktopTime" v-for="(time, i) in agenda.time" :key="`time-${time}`" :style="{ 'grid-area': `time-${i}` }">
          <p>{{ time }}</p>
        </div>
        <div class="event main" v-for="main in agenda.main" :key="`main-${main.id}`" :style="{ 'grid-area': `${main.id}` }">
          <p>{{ main.name }}</p>
        </div>
        <div class="event room" v-for="room in agenda.room" :key="`room-${room.id}`" :style="{ 'grid-area': `room-${room.id}` }">
          <p>{{ room.name }}</p>
        </div>
        <div class="event session" v-for="(session, index) in agenda.session" :key="`session-${session.id}`" @click="session.summary[0] ? nowFocusSessionIndex = index : null" :style="{ 'grid-area': `session-${session.id}` }">
          <div class="info">
            <div class="box">
              <p class="room tag">{{ agenda.room.filter(e => (e.id === session.id[1]))[0].name }}</p>
              <p v-if="session.time" class="time">{{ session.time }} 分鐘</p>
            </div>
            <p>{{ session.name }}</p>
            <p class="speaker" v-if="session.speaker"><span>{{ session.speaker }}</span></p>
          </div>
        </div>
        <div class="event break" :class="`break-${breaks.id}`" v-for="breaks in agenda.breaks" :key="`break-${breaks.id}`" :style="{ 'grid-area': `break-${breaks.id}` }">
          <p @click="$route.query[' '] ? egg() : null">{{ $route.query[' '] ? '莫風徵伴侶' : breaks.name }}</p>
        </div>
        <div class="event mobileTime" v-for="(time, i) in agenda.mobileTime" :key="`time-${i}`" :style="{ 'grid-area': `time-${i}` }">
          <p>{{ time }}</p>
        </div>
        <div class="event blank"></div>
      </div>
    </div>
    <div class="fullscreen-container" v-if="nowFocusSessionIndex !== ''">
      <div class="container">
        <div class="fullscreen-close" @click="nowFocusSessionIndex = ''">
          <img src="@/assets/images/icon/close.svg">
        </div>
        <div class="fullscreen-header">
          <div class="border" :style="{ 'background-image': 'url(' + `${require('@/assets/images/icon/menu-active-gold.png')}` + ')'}"></div>
          <div class="image">
            <div class="photo" :style="{ 'background-image': 'url(' + require(`@/assets/images/speaker/${agenda.session[nowFocusSessionIndex].image}`) + ')' }"></div>
            <h1><span>{{ agenda.session[nowFocusSessionIndex].speaker }}</span></h1>
          </div>
        </div>
        <div class="fullscreen-content">
          <div class="fullscreen-spliter">
            <p><span>議程介紹</span></p>
          </div>
          <h1><span>{{ agenda.session[nowFocusSessionIndex].name }}</span></h1>
          <p v-for="(paragraph, i) in agenda.session[nowFocusSessionIndex].summary" :key="`summary-${i}`">
            <span v-if="paragraph.match(/(\$html\[)+(.)+(\])/)">
              {{ paragraph.substring(0, paragraph.match(/(\$html\[)+(.)+(\])/).index) }}
              <a
                :href="JSON.parse(paragraph.match(/({)+(.)+(})/)[0]).link"
                target="_brank">{{ JSON.parse(paragraph.match(/({)+(.)+(})/)[0]).text }}</a>
              {{ paragraph.substring(paragraph.match(/(\$html\[)+(.)+(\])/).index + paragraph.match(/(\$html\[)+(.)+(\])/)[0].length) }}
            </span>
            <span v-else>{{ paragraph }}</span>
          </p>
          <div class="fullscreen-spliter" v-if="agenda.session[nowFocusSessionIndex].link">
            <p><span>簡報連結</span></p>
          </div>
          <p v-if="agenda.session[nowFocusSessionIndex].link">
            <a :href="agenda.session[nowFocusSessionIndex].link" target="_blank">
              <span>{{ agenda.session[nowFocusSessionIndex].link }}</span>
            </a>
          </p>
          <div class="fullscreen-spliter">
            <p><span>關於講者</span></p>
          </div>
          <h1><span>{{ agenda.session[nowFocusSessionIndex].speaker }}</span></h1>
          <p v-for="(paragraph, i) in agenda.session[nowFocusSessionIndex].bio" :key="`bio-${i}`">
            <span v-if="paragraph.match(/(\$html\[)+(.)+(\])/)">
              {{ paragraph.substring(0, paragraph.match(/(\$html\[)+(.)+(\])/).index) }}
              <a
                :href="JSON.parse(paragraph.match(/({)+(.)+(})/)[0]).link"
                target="_brank">{{ JSON.parse(paragraph.match(/({)+(.)+(})/)[0]).text }}</a>
              {{ paragraph.substring(paragraph.match(/(\$html\[)+(.)+(\])/).index + paragraph.match(/(\$html\[)+(.)+(\])/)[0].length) }}
            </span>
            <span v-else>{{ paragraph }}</span>
          </p>
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
      nowFocusSessionIndex: '',
      agenda: {
        time: [
          '10:30',
          '11:00',
          '11:10',
          '11:50',
          '12:00',
          '12:40',
          '12:45',
          '13:05',
          '13:10',
          '13:50',
          '13:55',
          '14:15',
          '14:20',
          '14:40',
          '14:45',
          '15:05',
          '15:10',
          '15:50',
          '15:55',
          '16:35',
          '17:05',
          '17:20'
        ],
        mobileTime: [
          '10:30',
          '11:00',
          '11:10',
          '11:50',
          '12:00',
          '12:40',
          '12:45',
          '13:05',
          '13:10',
          '13:50',
          '13:55',
          '14:15',
          '14:20',
          '14:40',
          '14:45',
          '15:05',
          '15:10',
          '15:50',
          '15:55',
          '16:35',
          '17:05',
          '17:20'
        ],
        main: [
          {
            name: '入場',
            id: 'admission'
          },
          {
            name: '開場',
            id: 'start'
          },
          {
            name: '論壇：月亮跟著禿子走；資安跟著大師走',
            id: 'panel-discussion'
          },
          {
            name: '閃電講',
            id: 'lighting'
          },
          {
            name: '閉幕',
            id: 'closing'
          },
          {
            name: '大會結束',
            id: 'ending'
          }
        ],
        room: [
          {
            name: '吉姆老爹啤酒工廠2F',
            id: 'A'
          }
        ],
        session: [
          {
            name: 'Chip Off Forensics',
            summary: ['Chip Off Forensics'],
            link: '',
            image: 'speaker1a.png',
            speaker: 'Captain',
            bio: ['Forensics Ninja'],
            time: '40',
            id: '1A'
          },
          {
            name: 'JiuWei: a Cross Platform and Multi Architecture Executor',
            summary: ['Functioning as the first-stage in an exploitation, shellcode play an important role in successfully triggering software vulnerability. Since this part of payload is written in low-level machine code, understanding how it works is not trivial for analysis.', 'This presentation introduces JiuWei, a cross-platform and multi architecture machine code analyzer. Based on Unicorn emulator (http://unicorn-engine.org), our tool is able to execute & analyze all kind of shellcodes, regardless of Operating System (Windows, Mac, Linux, Android, etc) or CPU architectures (Intel, Arm, Aarch64, Mips). ', 'Thanks to a powerful instrumentation engine, the output report can show what the shellcode does inside, in a friendly high-level output format.', 'In this talk, we will give a brief introduction on the design & implementation of JiuWei, some technical challenges we had to solve, and some cool live demo on some modern shellcode.'],
            link: '',
            image: 'speaker2a.jpg',
            speaker: 'xwings',
            bio: ['KaiJern (xwings), is Lab Director of The ShepherdLab, of JD Security. His research topic mainly on embedded device, hardware security, blockchain security, reverse engineering and various security topics. He presented his findings in different international security conferences like Defcon, HITB, Codegate, QCon, KCon, Brucon, H2HC and etc. He conducted hardware Hacking course in various places around the globe. He is also the owner of hackersbadge.com and actively involved in Unicorn (http://unicorn-engine.org) development. '],
            time: '40',
            id: '2A'
          },
          {
            name: '揭露某影像監控系統廠商RCE漏洞',
            summary: ['介紹漏洞並分享發現的心路歷程，展示目前尚未公開的PoC。'],
            link: '',
            image: 'speaker3a.png',
            speaker: 'GrayOD',
            bio: ['一介資安工程師，偶爾搞搞滲透，偶爾搞搞逆向，偶爾搞搞隊友(疑?)。'],
            time: '20',
            id: '3A'
          },
          {
            name: '掛很多,你們想要我講啥 ?',
            summary: ['TBD'],
            link: '',
            image: 'speaker4a.jpg',
            speaker: 'X1/資安黑武士',
            bio: ['著名想分享一切所知卻受束縛的資安人，深怕打開潘朵拉盒子', '這會引起殺生之禍／查水表／歡樂送／失業 !!', '只能蒙上面具，以黑武士奉獻自己的淺學'],
            time: '40',
            id: '4A'
          },
          {
            name: 'Bluetooth Sexploit: 通往性駭客的大門',
            summary: ['介紹藍芽漏洞', '介紹其在性犯罪上的應用', '並探討資安以及性的新興議題'],
            link: '',
            image: 'speaker7a.jpg',
            speaker: 'Kevin',
            bio: ['哈囉我是Kevin', '目前是苦命大四生', '目前正往物連網安全的領域探索中'],
            time: '20',
            id: '5A'
          },
          {
            name: 'BFKinesiS 戰隊參加 DEFCON CTF 決賽之解題分享',
            summary: ['此次分享主要著重於 DEFCON CTF 賽制介紹以及今年度的題目解析，對於想踏足 CTF 競賽的新手們，可以藉此機會一窺駭客聖殿的真面目，並了解參賽選手們在賽前如何準備、賽中面對未知題目時如何思考、以及攻擊時所使用的策略等只有參賽選手們知道的秘辛。'],
            link: '',
            image: 'speaker6a.png',
            speaker: 'BFKinesiS 戰隊',
            bio: ['BFKinesiS 是由台大 Balsn、交大 BambooFox、中央 DoubleSigma、中科院 KerKerYuan 所組成的 CTF 戰隊聯隊，成員大多為學生，曾兩度參加世界駭客大賽 DEFCON CTF 取得世界第 12 (2018) 以及世界第 2 (2019) 的成績。'],
            time: '20',
            id: '6A'
          },
          {
            name: '數位制腦權',
            summary: ['從科技整合的角度來看不實訊息與假新聞的應對攻防'],
            link: '',
            image: 'speaker5a.jpg',
            speaker: '林穎佑',
            bio: ['國立中正大學戰國所助理教授'],
            time: '20',
            id: '7A'
          },
          {
            name: '聯網裝置漏洞自動化探索',
            summary: ['我們將整理與說明過去的研究，包含現代挖掘漏洞技術以及自動化路由器分析的建構。從說明現代挖掘漏洞技術(特別是二進制)到說明現代的開發工具與架構。接著說明自動化路由器的分析建構，這個目標是能達到大規模測試。最後說明我們如何使用現代挖掘漏洞技術建構在自動化路由器分析上。最後我們將展示如何使用我們建構的專案在嵌入式網路服務找漏洞的案例分析。'],
            link: '',
            image: 'speaker8a.jpg',
            speaker: 'AjMaChInE',
            bio: ['AjMaChInE works in Funny Systems as Chief Researcher, has 5 years of experience in the security research and his main interests are in program reverse engineering, APT, RAT, firmware implant, hardware implant, side-channel attack. He has been working on writing AV bypass, UEFI implant, hardware implant over SPI bus and automatic vulnerability tools. His SlideShare is https://www.slideshare.net/aj0612.'],
            time: '20',
            id: '8A'
          },
          {
            name: '交易所安全漫談',
            summary: ['交易所安全漫談'],
            link: '',
            image: 'speaker9a.jpg',
            speaker: 'Tim Hsu',
            bio: ['著名駭客會議 HITCON 創辦人，同時也是台灣駭客技術社群 CHROOT 創辦人。', '目前為台灣多家加密貨幣交易所資安顧問，包含幣託 (BitoPro) 、OTCBTC 等。'],
            time: '40',
            id: '9A'
          }
        ],
        breaks: [
          {
            name: '休息',
            id: '1'
          },
          {
            name: '休息',
            id: '2'
          },
          {
            name: '休息',
            id: '3'
          },
          {
            name: '休息',
            id: '4'
          },
          {
            name: '休息',
            id: '5'
          },
          {
            name: '休息',
            id: '6'
          },
          {
            name: '休息',
            id: '7'
          },
          {
            name: '休息',
            id: '8'
          }
        ]
      }
    }
  },
  components: {
    ...layout
  },
  methods: {
    egg () {
      window.open('https://ioan.isalways.one/', '_blank')
    }
  }
}
</script>
