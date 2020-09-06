<template>
  <div>
    <div class="calendar-box">
      <center>
        <h4> Сегодня: {{actualDate}} </h4>
        <h3>Выбрано: <b v-if="CURR">{{fixCURR}} {{months[currMonth]}}</b></h3>
        <br>
      </center>
      <div id="calendar">
        <div class="head">
          <b class="ltMonth" @click="ltMonth()">«</b>
          <b>{{months[currMonth]}} {{currYear}} </b>
          <b class="gtMonth" @click="gtMonth()">»</b>
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

      <router-link tag="span" class="btn" to="/step3">
        <span>Get next</span>
        <img src="@/assets/arow.svg" alt="arow">
      </router-link>
  </div>
</template>

<script>

const NOW = new Date();

  export default {
    data() {
      return {
        inst_date: NOW,
        days: ['Пн', 'Вт', 'Ср', 'Чт', 'Пт', 'Сб', 'Вс'],
        months: ['Янв', 'Фев', 'Мар', 'Апр', 'Май', 'Июн', 'Июл', 'Авг', 'Сен', 'Окт', 'Ноя', 'Дек'],
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
[v-cloak] {
  display: none;
}
.menu-container{
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 280px;
  justify-content: center;
}
.select-categories{
  margin-top: 15px;
  padding: 5px 10px;
  border-radius: 15px;
}
.menu-button{
  margin-top: 15px;
  padding: 5px 10px;
  border-radius: 15px;
  border: none;
}
.menu-container *:focus{
  outline: none;
}
.template{
  margin: auto;
  padding-top: 30px;
  /* width: 800px; */
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.calendar-box{
  width: 280;
  margin: auto;
}
.head,
.week,
.days {
  display: -webkit-box;
  display: flex;
}
#calendar{
  box-shadow: 0 1em 10em -2em #000;
  width: 280px;
  text-align: center; 
}
.week{
  border-bottom: 1px solid rgba(204, 204, 204, 0.3);
  line-height: 2em;
}
.week b{
  font-weight: normal;
  color:rgba(204, 204, 204, 0.5);
  width: 40px;
}
.days{
  flex-wrap: wrap;
  line-height: 40px;
}
span,
time{
  width: 40px;
}
time{
  cursor: pointer;
}
time:hover{
  color: white;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.2);
}
.currDay{
  color: white;
  background: none !important;
  border-radius: none !important;
  outline: 2px solid rgba(255, 255, 255, 0.5);
  outline-offset: -5px;
}
.CURR{
  color: #ffd700 !important;
}
.head{
  background: rgba(238, 238, 238, 0.3);
  justify-content: space-between;
  line-height: 40px;
}
.ltMonth,
.gtMonth{
  cursor: pointer;
  padding: 0 1em;
  background: rgba(238, 238, 238, 0.3);
}
.ltMonth:hover,
.gtMonth:hover{
  background: rgba(238, 238, 238, 0.2);
  color: #f00;
}

  //  кнопка меню
.btn{
      height: 53px;
      width: 270px;
      background: #5FB763;
      box-shadow: 0px 2.77551px 15px #B1EFB4;
      border-radius: 5px;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;

      span{
        font-family: Poppins;
        font-style: normal;
        font-weight: 500;
        font-size: 16px;
        line-height: 24px;
        color: #FFFFFF;
      }

      img{
        color: #FFFFFF;
        height: 12px;
        margin-left: 8px;
      }
    }
</style>