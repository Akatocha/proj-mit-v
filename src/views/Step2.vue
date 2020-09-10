<template>
  <div>
    <div class="content">
      <h1>When do you need to your vehicle to be shipped?</h1>
      <div class="calendar-box">
        <div id="calendar">
          <div class="head">
            <b class="ltMonth" @click="ltMonth()"></b>
            <b class="selected-date" v-if="CURR">{{months[currMonth]}} {{fixCURR}}, {{currYear}} </b>
            <b class="gtMonth" @click="gtMonth()"></b>
          </div>
          <div class="week">
            <b v-for="day in days"  >{{day}}</b>
          </div>
          <div class="days"><span v-for="blank in nullWeek" >&nbsp;
            </span>
            <time
            :class="{currDay: i == currDay, CURR: i == CURR}"
            @click="CURR = i"
            v-for="i in daysInMonth" >{{i}} </time>
          </div>
        </div>
      </div>

      <router-link tag="span" class="btn" to="/step3">Next step</router-link>
    </div>
  </div>
</template>

<script>

const NOW = new Date();

  export default {
    data() {
      return {
        inst_date: NOW,
        days: ['Mo', 'Tu', 'We', 'Th', 'Fr', 'Sa', 'Su'],
        months: ['January', 'February','March','April','May','June', 'July','August','September', 'October', 'November', 'December'],
        CURR: NOW
      }
    },
    computed: {
      actualDate(){
        return new Date().toLocaleDateString()
      },
      fixCURR(){
        return (this.CURR <= this.daysInMonth) ? this.CURR : this.daysInMonth
      },
      currYear(){
        return this.inst_date.getFullYear() 
      },
      currMonth(){
        return this.inst_date.getMonth() 
      },
      currWD() {
        return this.inst_date.getDay() 
      },
      currDay(){
        if(this.inst_date.getMonth() == NOW.getMonth() 
          && this.inst_date.getFullYear() == NOW.getFullYear()) {
            return NOW.getDate()
          }
        return
      },
      daysInMonth(){
        return new Date(this.currYear, this.currMonth+1,0).getDate()
      },
      nullWeek(){
        return new Date(this.currYear, this.currMonth, 0).getDay()
      }
    },
    methods: {
      ltMonth() {
        this.inst_date = new Date(this.currYear, this.currMonth-1)
      },
      gtMonth() {
        this.inst_date = new Date(this.currYear, this.currMonth+1)
      }
    },
  }
</script>

<style lang="scss" scoped>
 .calendar-box {
    width: 320px;
    margin: auto;

    [v-cloak] {
      display: none;
    }

    .head,
    .week,
    .days {
      display: -webkit-box;
      display: flex;
    }
    #calendar {
      background: #FFFFFF;
      box-shadow: 0 4.41px 16.56px rgba(0, 0, 0, 0.05);
      border-radius: 5px;
      width: 100%;
      text-align: center;
    }
   .selected-date{
     font-weight: 500;
     font-size: 15px;
     color: #393939;
   }
    .week{
      position: relative;
      line-height: 2em;
      padding: 0 10px;
      :after{
        content: '';
        display: block;
        position: absolute;
        bottom: 0;
        left: 14px;
        height: 1px;
        width: calc(100% - 28px);
        background-color:  #EDEDED;
      }
    }

    .week b {
      width: 40px;
      margin: 2px;
      font-size: 14px;
      font-weight: 300;
      color: #393939;
      text-align: center;
    }
    .days {
      flex-wrap: wrap;
      line-height: 40px;
      padding: 10px 5px;
    }
    span,
    time {
      width: 40px;
      margin: 2px;
      border-radius: 2px;

    }
    time {
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
    }

    .currDay {
      color: #5FB763;
      border: 1px solid #5FB763;
      box-sizing: border-box;
    }

    time:hover,
   .CURR {
      background: #5FB763;
      box-shadow: 0 4px 33.6px rgba(177, 239, 180, 0.54);
      color: #fff;
    }
    .head {
      background: rgba(238, 238, 238, 0.3);
      justify-content: space-between;
      line-height: 40px;
    }
    .ltMonth,
    .gtMonth {
      cursor: pointer;
      padding: 20px;
      width: 6px;
      height: 12px;
      background: url("data:image/svg+xml,%3Csvg width='7' height='12' viewBox='0 0 7 12' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M5.1806 0.00154678C5.38043 0.00115675 5.57409 0.0707521 5.72796 0.198254C5.81456 0.27005 5.88615 0.358228 5.93862 0.457733C5.99109 0.557239 6.02341 0.666117 6.03374 0.778134C6.04407 0.890152 6.0322 1.00311 5.99881 1.11053C5.96541 1.21795 5.91116 1.31773 5.83914 1.40415L2.00764 5.98827L5.7023 10.5809C5.77334 10.6684 5.8264 10.7691 5.85841 10.8771C5.89042 10.9852 5.90077 11.0985 5.88884 11.2106C5.87692 11.3226 5.84297 11.4312 5.78894 11.5301C5.73491 11.629 5.66187 11.7163 5.57402 11.7868C5.48553 11.8647 5.3819 11.9234 5.26964 11.9593C5.15738 11.9952 5.0389 12.0076 4.92166 11.9955C4.80441 11.9835 4.69091 11.9473 4.5883 11.8893C4.48569 11.8313 4.39616 11.7528 4.32536 11.6586L0.194517 6.52708C0.0687256 6.37404 -4.09762e-05 6.18209 -4.09589e-05 5.98399C-4.09416e-05 5.7859 0.0687257 5.59394 0.194517 5.44091L4.47075 0.309436C4.55654 0.205936 4.66553 0.124121 4.78887 0.0706252C4.9122 0.0171308 5.04641 -0.00653562 5.1806 0.00154678Z' fill='%23393939'/%3E%3C/svg%3E%0A") center no-repeat;
    }

   .gtMonth{
     transform: rotate(-180deg);
   }

   .ltMonth:hover{
     transform: scale(2);
    }

   .gtMonth:hover {
     transform: scale(2) rotate(-180deg);
   }
 }


 .btn{
   margin-top: 60px;
 }


 @media screen and (max-width: 1460px) {
   .wrap-radio{
     margin-top: 20px;
   }
   .btn{
     margin-top: 40px;
   }
 }

 @media screen and (max-width: 1000px) {
   .calendar-box{
     width: 220px;

     .selected-date{
       font-size: 12px;
     }

     .week {
       padding: 0 5px;
       b {
         width: 34px;
       }
     }

     span, time{
       width: 34px;
       margin: 1px;
      font-size: 12px;
     }

     .days{
       line-height: 34px;
       padding: 5px 0;
     }
   }
 }

</style>