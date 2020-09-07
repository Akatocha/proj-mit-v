<template>
  <div>
    <div class="content">
      <h1>What car you shipping?</h1>
      <div v-for="repeat in counterArrInput" :key="repeat"
      class="input-box">
        <select v-model="year" class="inp-text">
          <option disabled value="start">Year</option>
          <option
          v-for="(year, key) in yearsArr"
          :key="key"
          :value="year">{{year}} </option>
        </select>
        <!-- <select v-model="make" class="inp-text">
          <option
          v-for="(make, key) in modelData[year]"
          :key="key"
          :value="key">{{key}} </option>
        </select>
        <select v-model="model" class="inp-text">
          <option
          v-for="make in modelData[year][make]"
          :key="make"
          :value="make">{{make}}</option>
        </select> -->
        <div class="checkbox-box">
          <div class="checkbox-container">
            <input type="checkbox">
            <span>Inoperable</span>
          </div>
          <div class="checkbox-container">
            <input type="checkbox">
            <span>Modified</span>
          </div>
          <div class="checkbox-container" v-if="btnShow(repeat)">
            <button @click="addcounterArrInput" >+</button>
            <span>Add another vehicle</span>
          </div>
        </div>
      </div>
        <router-link tag="span" class="btn" to="/step2">Next step</router-link>
    </div>
  </div>
</template>

<script>

  export default {
    data() {
      return {
        counterArrInput: [1],
        year: 'start',
        make: 'Make',
        model: 'Model',


      }
    },
    computed: {
      yearsArr() {
        let years = []
        for (let i = 1917; i <= 2021; i++){
          if(i == 1943){
            i = 1945
          }
          years.push(i)
        }

        return years
      }
    },
    methods: {
      addcounterArrInput(){
        let n = this.counterArrInput.length +1
        this.counterArrInput.push(n)
      },
      btnShow(repeat) {
        let n = this.counterArrInput.length 
        if (repeat == n){
          return true
        }else{
          return false
        }
      }
    },
  }
</script>

<style lang="scss" scoped>
.checkbox-box{
  display: flex;
  width: 100%;
}

.checkbox-container{
  display: flex;
  margin: auto;
}

.inp-text{
  padding: 15px 22px;
  height: 53px;
  background: #F5F5F5;
  border-radius: 5px;
  width: 270px;
  font-family: Poppins;
  font-style: normal;
  font-weight: 600;
  font-size: 17px;
  line-height: 25px;
  letter-spacing: 0.03em;
  color: #717171;
  border: none;
}
</style>