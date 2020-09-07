<template>
  <div>
    <div class="content">
      <h1>What car you shipping?</h1>

        <InputBox v-for="i in repeatCoutn" :key="i"
        @addInput="addInput"
        @catchDataFromInput='catchDataFromInput'></InputBox>

    </div>
      <router-link tag="span" class="btn" to="/step2">Next step</router-link>
  </div>
</template>

<script>

import InputBox from '../components/inputBox'


  export default {
    components: {
      InputBox,
    },
    data() {
      return {
        ArrayData: [
        ],
        repeatCoutn: 1,
      }
    },
    methods: {
      catchDataFromInput(modelId){
        console.log(modelId)
        
        this.ArrayData[this.repeatCoutn-1] = modelId
      },
      addInput(){
        this.repeatCoutn = this.repeatCoutn +1
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