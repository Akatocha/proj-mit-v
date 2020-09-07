<template>
  <div>
    <select @change="selectYear" v-model="year" class="inp-text">
      <option disabled value="start">Year</option>
      <option
      v-for="(year, key) in yearsArr"
      :key="key"
      :value="year">{{year}} </option>
    </select>

    <select @change="selectMake" v-model="makeId" class="inp-text">
      <option disabled value="start">Make</option>
      <option
      v-if="responseMake"
      v-for="(make, key) in responseMake"
      :key="key"
      :value="make.id">{{make.value}} </option>
    </select>

    <select @change="selectModel" v-model="modelId" class="inp-text">
      <option disabled value="start">Model</option>
      <option
      v-if="responseModel"
      v-for="(model, key) in responseModel"
      :key="key"
      :value="model.id">{{model.value}} </option>
    </select>

    <div class="checkbox-box">
      <div class="checkbox-container">
        <input type="checkbox">
        <span>Inoperable</span>
      </div>
      <div class="checkbox-container">
        <input type="checkbox">
        <span>Modified</span>
      </div>
      <div class="checkbox-container" >
        <button @click="addInput" >+</button>
        <span>Add another vehicle</span>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        year: 'start',
        makeId: 'start',
        modelId: 'start',
        responseMake: null,
        responseModel: null,
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
      selectModel(){
        // console.log(this.modelId)
        this.$emit('catchDataFromInput', this.modelId)
      },
      selectMake(){
        let idMake = this.makeId
        this.axios.get(`https://quotebooster.com/api/model/by_make_id.json?make_id=${idMake}`)
        .then((response) => {
          // console.log(response.data)
          this.responseModel = response.data
        }).catch(err => console.log(err))
      },
      selectYear(){
        let year = this.year
        this.axios.get(`https://quotebooster.com/api/make/by_year.json?year=${year}`)
        .then((response) => {
          // console.log(response.data)
          this.responseMake = response.data
        }).catch(err => console.log(err))
      },
      addInput(){
        this.$emit('addInput')
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