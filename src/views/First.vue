<template>
  <div>
    <div class="container">
      <div class="first-main">
        <h1>Quickly Compare Cheap Car Shipping Quotes</h1>
        <h4>Save an average of 27% & make a fully informed decision</h4>
        <div class="supra-button-box">
        <div class="buton-box">
          <div 
          @mouseleave="restartZip1"
          class="gray-text-box-1">
          <span class="gray-text">PICKUP FROM</span>
            <input 
              
              @keyup="getZipOne"
              class="zip-text" 
              v-model="zipCityOne" 
              placeholder="Enter ZIP Code or City" 
              type="text">
            <div 
              v-if="showDropdownOne"
              class="dropdown-content">
              <div 
                @click="takeZipOne(region)"
                v-for="region in responseDataOne"
                :key='region.zip'
                class="dd-cell">
                <span>{{region.city}} </span>
                <span>{{region.state}}</span>
              </div>
            </div>
          </div>
          <div @mouseleave="restartZip2"
          class="gray-text-box-1 gray-text-box-2">
            <hr>
            <span class="gray-text">DELIVERY TO</span>
            <input 
              @keyup="getZipTwo"
              class="zip-text" 
              v-model="zipCityTwo" 
              placeholder="Enter ZIP Code or City" 
              type="text">
            <div 
              v-if="showDropdownTwo"
              class="dropdown-content">
              <div 
                @click="takeZipTwo(region)"
                v-for="region in responseDataTwo"
                :key='region.zip'
                class="dd-cell">
                <span>{{region.city}} </span>
                <span>{{region.state}}</span>
              </div>
            </div>
          </div>
          <button @click="goToStep1"
          :disabled='!checkNextStep'  class="btn" >
            Get started
          </button>

        </div>
        <p class="text-second">It will only take 30 seconds</p>
        </div>
      </div>
      <div class="futer">
        <p>In Compliance With:</p>
        <div class="img-container">
          <img src="@/assets/logoBot_1.png" alt="logo">
          <img src="@/assets/logoBot_2.png" alt="logo">
          <img src="@/assets/logoBot_3.png" alt="logo">
          <img src="@/assets/logoBot_4.png" alt="logo" style="max-height: 61px;">
        </div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      z1pick: false,
      z2pick: false,
      zipCityOne: '',
      zipCityTwo: '',
      responseDataOne: null,
      responseDataTwo: null,
    }
  },
  computed: {
    checkNextStep(){
      if(this.z1pick && this.z2pick){
        return true
      }else{
        return false
      }
    },
    showDropdownOne() {
      if(this.zipCityOne.length > 2  && this.responseDataOne !== null){
        return true
      }else{
        return false
      }
    },
    showDropdownTwo() {
      if(this.zipCityTwo.length > 2  && this.responseDataTwo !== null){
        return true
      }else{
        return false
      }
    },
  },
  methods: {
    goToStep1(){
      this.$router.push('/step1')
    },
    restartZip1(){
      if(!this.z1pick){
      this.zipCityOne = ''
      }
    },
    restartZip2(){
      if(!this.z2pick){
      this.zipCityTwo = ''
      }
    },
    getZipOne() {
      if (this.zipCityOne.length > 2){
        this.axios.get(`https://quotebooster.com/api/city/by_query.json?q=${this.zipCityOne}`)
        .then(res => {
          this.responseDataOne = res.data.data
        }).catch(err => console.log(err))
      }
    },
    getZipTwo() {
      if (this.zipCityTwo.length > 2){
        this.axios.get(`https://quotebooster.com/api/city/by_query.json?q=${this.zipCityTwo}`)
        .then(res => {
          this.responseDataTwo = res.data.data
        }).catch(err => console.log(err))
      }
    },
    takeZipOne(region){
      this.zipCityOne =  `${region.city}, ${region.state}`     
      localStorage.setItem('cityOne', JSON.stringify(region))
      this.z1pick = true
      this.responseDataOne = null
    },
    takeZipTwo(region){
      this.zipCityTwo = `${region.city}, ${region.state}`
      localStorage.setItem('cityTwo', JSON.stringify(region))
      this.responseDataTwo = null
      this.z2pick = true
    }
  },
}
</script>

<style lang="scss" scoped>
.first-main{
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;

  .buton-box{
    padding: 30px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    border-radius: 5px;

    .gray-text-box-1{
      width: 274px;
      display: flex;
      flex-direction: column;
      position: relative;

      .dropdown-content{
        z-index: 2;
        width: 270px;
        background: white;
        top: 100%;
        position: absolute;
        max-height: 300px;
        overflow: auto;
        box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        padding: 10px 5px;

        .dd-cell{
          cursor: pointer;
          display: flex;
          justify-content: space-between;
          padding: 5px;
          &:hover{
            background: #5FB763;
            color: #fff;
          }
        }

        &::-webkit-scrollbar {
          width: 10px;
        }
        &::-webkit-scrollbar-track {
          box-shadow: inset 0 0 5px #B1EFB4;
          border-radius: 2px;
        }
        &::-webkit-scrollbar-thumb {
          background: #5fb763ad;
          border-radius: 2px;
        }
        &::-webkit-scrollbar-thumb:hover {
          background: #5FB763;
        }
      }
    }

    .gray-text-box-2{
      position: relative;
      display: flex;
      flex-direction: column;
      padding-left: 80px;
      margin-right: 52px;

      .number-tex{
        
        font-style: normal;
        font-weight: 600;
        font-size: 17px;
        line-height: 25px;
        letter-spacing: 0.03em;
        color: #393939;
      }

      hr {
        position: absolute;
        top: 50%;
        left: -40px;
        width: 81px;
        height: 2px;
        color: black;
        transform: rotate(90deg);
      }
    }

    .zip-text{
      font-size: 17px;
      font-style: normal;
      font-weight: 600;
      line-height: 25px;
      letter-spacing: 0.03em;
      border: none;
      color: #393939;
    }
    &::placeholder {
      color: #717171;
    }
    :focus{
      outline: none;
    }


    .gray-text{
      
      font-style: normal;
      font-weight: 500;
      font-size: 17px;
      line-height: 174%;
      letter-spacing: 0.05em;
      color: #CCCCCC;
    }
  }

  .supra-button-box{
    display: flex;
    flex-direction: column;
  }
  .text-second{
      
      font-style: normal;
      font-weight: normal;
      font-size: 15px;
      line-height: 22px;
      color: #BBBBBB;
      margin-top: 15px;
      align-self: flex-end;
    }
}

.futer{
  display: flex;
  flex-direction: column;
  margin: 120px -200px 0 -200px;

  p{
    margin-bottom: 15px;
    
    font-style: normal;
    font-weight: 500;
    font-size: 16px;
    line-height: 24px;
    text-align: center;
    color: #393939;
  }



  .img-container{
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .a-box{
    margin-top: 120px;
    display: flex;
    justify-content: center;

      a{
        margin: 0 47px;
        display: flex;
        font-style: normal;
        font-weight: 500;
        font-size: 14px;
        line-height: 21px;
        text-align: center;
        text-decoration-line: underline;
        color: #393939;
      }
  }
}

.btn{
  border: none;
  outline: none;
  margin-top: 0;
}

@media screen and (max-width: 1460px) {
  .futer{
    margin: 65px 0 0;
  }
}

@media screen and (max-width: 1000px) {
  .main-box h4{
    font-size: 16px;
    text-align: center;
    margin-bottom: 30px;
  }
  .first-main{
    .supra-button-box{
      width: 280px;
    }

    .buton-box{
      padding: 0 30px 30px;

      hr{
        display: none;
      }

      .gray-text{
        font-size: 12px;
      }

      .gray-text-box-1{
        position: relative;
        width: 100%;
        padding: 30px 0;

        .dropdown-content{
          width: 100%;
          margin-top: -30px;
          max-height: 200px;
          .dd-cell{
            font-size: 15px;
          }
        }

        &:first-child:after{
          content: '';
          display: block;
          position: absolute;
          bottom: 0;
          height: 1.5px;
          width: 100%;
          background-color:  #EDEDED;
        }
        .zip-text{
          font-size: 12px;
        }
      }
    }
    .text-second{
      text-align: center;
      width: 100%;
      font-size: 18px;
    }

  }

  .futer{
   .img-container{
     justify-content: center;
     flex-direction: column;
     img{
       margin: 15px 0;
       max-width: 90%;
       height: auto;
     }
   }
  }
}
</style>