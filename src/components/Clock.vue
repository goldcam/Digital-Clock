<template>
  <div id="clock"> 
<div id="main">
  <div id="time">
    <span id="hours">{{hours}}</span><span id="min">{{minutes}}</span><span id="sec">{{sec}}</span> <span id="ampm">{{ampm}}</span>
  </div>
  <div id='days'>
    <div class="days" v-for="day in days" :key="day.id" v-bind:class="{active:day.active}">{{day.text}}</div>
  </div>
  <div id="fullDate">
    <span id="month">{{month}}</span>&nbsp;<span id="date">{{date}}</span>&nbsp;<span id="year">{{year}}</span>
  </div>
</div> 
</div>
</template>

<script>
export default {
  name: 'Clock',
  props: {

  },
  data: function (){
    return {
    days: [
      {text:"sun", active: false, id:0},
      {text:"mon", active: false, id:1},
      {text:"tue", active: false, id:2},
      {text:"wed", active: false, id:3},
      {text:"thu", active: false, id:4},
      {text:"fri", active: false, id:5},
      {text:"sat", active: false, id:6}
    ],
   months: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
   ampm:'',
   hours: '',
   minutes:'',
   sec: '' ,
   month:'',
   date: '',
   year: ''
    }
  },
  methods:{
    startClock:function(){
      const THIS = this;
      
      setInterval(function () {
        let 
            b = new Date,
            c = b.getHours(),
            d = b.getMinutes(),
            e = b.getSeconds(),
           
            h = b.getDay(),
            i = 12 <= c ? 'PM' : 'AM',
            j = b.getMonth(),
            k = b.getDate(),
            l = b.getFullYear();
           
        THIS.ampm = i;
          12 < c && (c %= 12), 
          0 == c && (c = 12), 
          9 >= e && (e = '0' + e), 
          9 >= d && (d = '0' + d), 
          THIS.hours = c, 
          THIS.minutes = `:${d}:`, 
          THIS.sec = e, 
          THIS.month = THIS.$data.months[j], 
          THIS.date = k, 
          THIS.year = l;
          THIS.days[h].active = true;
    }, 100)
    }
  },
  created: function() {
   this.startClock();
  }
}
</script>

<style scoped >
@import url(https://fonts.googleapis.com/css?family=Orbitron:700,900,500,400);

#clock {
  width: 100%;
  height: auto;
}
#clock #time {
  width: 40%;
  margin: 0 auto;
  text-align: center;
  font-size: 2.5em;
  text-shadow: 0px 2px 25px rgba(144, 244, 253, 0.6);
}
#clock #time #ampm {
  font-size: 0.5em;
}
#clock #days, #clock #fullDate {
  width: 25%;
  margin: 0 auto;
  display: flex;
  text-align: center;
  align-items: center;
  justify-content: center;
}
#clock .days {
  flex: 1;
  color: #444444;
  text-align: center;
}
#clock .active {
  color: paleturquoise;
  text-shadow: 0px 2px 25px rgba(144, 244, 253, 0.6);
}
#clock #fullDate {
  margin-top: 0.25em;
  text-shadow: 0px 2px 25px rgba(144, 244, 253, 0.6);
}
#clock #sec {
  display: inline-block;
  width: 70px;
}

</style>
