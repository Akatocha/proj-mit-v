<template>
  <div>
    <h1>What car you shipping?</h1>
    <div class="input-box">
      <select v-model="year" class="inp-text">
        <option 
        v-for="(year, key) in modelData" 
        :key="key"
        :value="key">{{key}} </option>
      </select>
      <select v-model="make" class="inp-text">
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
      </select>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        year: 'Year',
        make: 'Make',
        model: 'Model',
        modelData: {
          'Year': {
            'Make':{
              'Model': 'Model'
            }
          },
          '1862': {
            'Toyota': {
              'toyota_1': 'toyota_1', 
              'toyota_2': 'toyota_2', 
              'toyota_3': 'toyota_3', 
              'toyota_4': 'toyota_4', 
            },
            'Bmv': {
              'bmv_1': 'bmv_1', 
              'bmv_2': 'bmv_2', 
              'bmv_3': 'bmv_3', 
              'bmv_4': 'bmv_4', 
            },

          },
          '1922':{
            'Mers': {
              'mers_1': 'mers_1', 
              'mers_2': 'mers_2', 
              'mers_3': 'mers_3', 
              'mers_4': 'mers_4', 
            },
          }
        }

      }
    },
  }
</script>

<style lang="scss" scoped>
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