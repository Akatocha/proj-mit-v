<template>
  <div>
    <div class="content">
      <h1>When do you need to your vehicle to be shipped?</h1>
      <div class="calendar-box">
        <div id="calendar">
          <div class="head">
            <b class="ltMonth" @click="ltMonth()"><</b>
            <b v-if="CURR">{{months[currMonth]}} {{fixCURR}}, {{currYear}} </b>
            <b class="gtMonth" @click="gtMonth()">></b>
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

      <router-link tag="span" class="btn" to="/step4">Next step</router-link>
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
        CURR: null
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
    width: 280px;
    margin: auto;

    [v-cloak] {
      display: none;
    }
    .menu-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      width: 280px;
      justify-content: center;
    }
    .select-categories {
      margin-top: 15px;
      padding: 5px 10px;
      border-radius: 15px;
    }
    .menu-button {
      margin-top: 15px;
      padding: 5px 10px;
      border-radius: 15px;
      border: none;
    }
    .menu-container *:focus {
      outline: none;
    }
    .template {
      margin: auto;
      padding-top: 30px;
      /* width: 800px; */
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
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
    .week {
      border-bottom: 1px solid rgba(204, 204, 204, 0.3);
      line-height: 2em;
    }
    .week b {
      font-weight: normal;
      color: rgba(204, 204, 204, 0.5);
      width: 40px;
    }
    .days {
      flex-wrap: wrap;
      line-height: 40px;
    }
    span,
    time {
      width: 40px;
    }
    time {
      cursor: pointer;
    }
    time:hover {
      color: white;
      border-radius: 50%;
      background: rgba(255, 255, 255, 0.2);
    }
    .currDay {
      color: #5FB763;
    }
    .CURR {
      background: #5FB763;
      box-shadow: 0 4px 33.6px rgba(177, 239, 180, 0.54);
      border-radius: 2px;
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
      padding: 0 1em;
      background: rgba(238, 238, 238, 0.3);
    }
    .ltMonth:hover,
    .gtMonth:hover {
      background: rgba(238, 238, 238, 0.2);
      color: #f00;
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
</style>