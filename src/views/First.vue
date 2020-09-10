<template>
  <div>
    <div class="container">
      <div class="first-main">
        <h1>Quickly Compare Cheap Car Shipping Quotes</h1>
        <h4>Save an average of 27% & make a fully informed decision</h4>
        <div class="supra-button-box">
        <div class="buton-box">
          <div class="gray-text-box-1">
          <span class="gray-text">PICKUP FROM</span>
            <input 
              @keydown="getZipOne"
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
          <div class="gray-text-box-1 gray-text-box-2">
            <hr>
            <span class="gray-text">DELIVERY TO</span>
            <input 
              @keydown="getZipTwo"
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
          <router-link tag="span" class="btn" to="/step1">
            Get started
          </router-link>

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
          <img class="img-4" src="@/assets/logoBot_4.png" alt="logo">
        </div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      zipCityOne: '',
      zipCityTwo: '',
      zipCityArr: ['ua', 'dsa', 'udcx'],
      responseDataOne: null,
      responseDataTwo: null,
    }
  },
  computed: {
    showDropdownOne() {
      if(this.zipCityOne !== '' && this.responseDataOne !== null){
        return true
      }else{
        return false
      }
    },
    showDropdownTwo() {
      if(this.zipCityTwo !== '' && this.responseDataTwo !== null){
        return true
      }else{
        return false
      }
    }
  },
  methods: {
    getZipOne() {
      // console.log('zip')
      this.axios.get(`https://quotebooster.com/api/city/by_query.json?q=${this.zipCityOne}`)
      .then(res => {
        this.responseDataOne = res.data.data
      }).catch(err => console.log(err))
    },
    getZipTwo() {
      // console.log('zip')
      this.axios.get(`https://quotebooster.com/api/city/by_query.json?q=${this.zipCityTwo}`)
      .then(res => {
        this.responseDataTwo = res.data.data
      }).catch(err => console.log(err))
    },
    takeZipOne(region){
      this.zipCityOne =  `${region.city}, ${region.state}`
      this.responseDataOne = null
    },
    takeZipTwo(region){
      this.zipCityTwo = `${region.city}, ${region.state}`
      this.responseDataTwo = null
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
    max-width: 850px;
    padding: 31px;
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
        width: 304px;
        background: white;
        top: 100%;
        position: absolute;
        height: 300px;
        overflow: scroll;
        .dd-cell{
          cursor: pointer;
          display: flex;
          justify-content: space-between;
          padding: 5px;
          &:hover{
            background: rgb(204, 204, 204);

          }
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
      
      font-style: normal;
      font-weight: 600;
      font-size: 17px;
      line-height: 25px;
      letter-spacing: 0.03em;
      color: #717171;
      border: none;
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
  max-width: 1200px;
  margin: 0 -200px;

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
    justify-content: space-around;
    align-items: center;
    .img-4{
      height: 61px;
    }
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
</style>