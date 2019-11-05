<template>
  <div>
    <div class="spotlight">
      <div class="spotlight-box spotlight-map">
        <img class="map" src="../assets/images/paper.png" alt="">
        <iframe src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d14498.166836582535!2d121.683639!3d24.7082762!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0xfdb3ea0c37a6128a!2z5ZCJ5aeG6ICB54i55ZWk6YWS5bel5aC0IEppbSAmIERhZCdzIEJyZXcgQ29tcGFueQ!5e0!3m2!1sen!2stw!4v1572959410305!5m2!1sen!2stw" width="600" height="450" frameborder="0" style="border:0;" allowfullscreen=""></iframe>
      </div>
      <div class="spotlight-box">
        <h1 class="title symbol"><span>大眾運輸資訊</span></h1>
        <div class="content">
          <p><a href="http://www.kamalan.com.tw/752.html">葛瑪蘭客運752公車 宜蘭轉運站 –> 下深溝 (蜂采館) 站</a></p>
          <p><a href="http://www.kingbus.com.tw/ticketPriceResult.php?sid=5">葛瑪蘭客運752公車 宜蘭轉運站 –> 下深溝 (蜂采館) 站</a></p>
          <p><a href="http://e-landbus.tw/timetable/%E7%B6%A012%E5%BE%80.pdf">綠12 宜蘭轉運站 –> 蜂采館站</a></p>
        </div>
      </div>
      <div class="spotlight-box">
        <h1 class="title symbol"><span>臺鐵</span></h1>
        <div class="content">
          <p>搭乘至 宜蘭火車站 下車：</p>
          <ul>
            <li><a href="http://e-landbus.tw/timetable/%E7%B6%A012%E5%BE%80.pdf">往宜蘭轉運站方向轉乘綠12前往蜂采館站，步行抵達吉姆老爹啤酒工場。</a></li>
          </ul>
        </div>
      </div>
      <div class="spotlight-box">
        <h1 class="title symbol"><span>客運</span></h1>
        <div class="content">
          <p>宜蘭轉運站週邊有多家客運業者提供客運服務，路線遍及各縣市</p>
          <ul>
            <li>國光客運</li>
            <li>葛瑪蘭客運</li>
          </ul>
        </div>
      </div>
      <div class="spotlight-box">
        <h1 class="title symbol"><span>開車</span></h1>
        <div class="content">
          <ul>
            <li>
              高速公路：<br />
              走國道5號經雪山隧道，在38-宜蘭出口下交流道，朝宜蘭/192縣道/壯圍前進，走191縣道經宜18-2鄉道前往員山鄉的北橫公路/員山路二段/台7線即可抵達吉姆老爹啤酒工場。
            </li>
          </ul>
        </div>
      </div>
      <div class="spotlight-box">
        <h1 class="title symbol"><span>航空</span></h1>
        <div class="content">
          <p>到達桃園國際機場後，前往台北轉運站或台北車站轉乘前往宜蘭車站，轉乘綠12前往蜂采館站，步行抵達吉姆老爹啤酒工場。</p>
        </div>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import layout from '@/components/layout'
export default {
  components: {
    ...layout
  }
}
</script>
