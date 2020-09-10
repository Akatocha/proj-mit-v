<template>
  <div>
    <div class="content">
      <h1>What car you shipping?</h1>

        <InputBox v-for="i in repeatCoutn" :key="i"
        @addInput="addInput"
        @catchDataFromInput='catchDataFromInput'></InputBox>
      <router-link tag="span" class="btn" to="/step2">Next step</router-link>
    </div>
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



  .btn{
    margin-top: 40px;
  }


  @media screen and (max-width: 1460px) {
    .btn{
      margin-top: 60px;
    }
  }
</style>