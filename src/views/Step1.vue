<template>
  <div>
    <div class="content">
      <h1>What car you shipping?</h1>

        <InputBox v-for="i in repeatCoutn" :key="i"
        :i='returnI(i)'
        :repeatCoutn='repeatCoutn'
        @valid='upValid'
        @deleteInp='deleteInp'
        @addInput="addInput"
        @catchDataFromInput='catchDataFromInput'></InputBox>
      <button :disabled='!validTrue' @click="goTostep2"  class="btn">Next step</button>
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
        satusValidInp: false,
        statusParent: true,
      }
    },
    computed: {
      validTrue() {
        if(this.satusValidInp == true && this.statusParent == true){
          return true
        }else{return false}
      }
    },
    methods: {
      goTostep2(){
        this.$router.push('/step2')
      },
      upValid(state, i){
         console.log(state)
         this.satusValidInp = state
         this.statusParent = true
      },
      returnI(i){
        return i
      },
      catchDataFromInput(year, makeId, modelId){
        // console.log(year, makeId, modelId)
        
        this.ArrayData[this.repeatCoutn-1] = modelId
      },
      addInput(){
        this.repeatCoutn = this.repeatCoutn +1
        this.statusParent = false
      },
      deleteInp(){
        this.repeatCoutn --
        this.statusParent = true
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

  @media screen and (max-width: 1000px) {
      .btn{
        margin-top: 30px;
        width: 90%;
      }
  }
</style>