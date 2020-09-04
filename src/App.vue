<template>
  <div>
      <img class="logo-right" src="@/assets/logo_transparent_1.svg" alt="logo">
      <img class="phone-left" src="@/assets/Phone.svg" alt="phone">
      <img class="number-left" src="@/assets/number.svg" alt="phone">

    <div class="main-box">
      <div class="step-box">
        <div v-if="checkRoutLeft" class="left-step">
          <!-- <img class="arow" src="@/assets/arow.svg" alt=""> -->
          <router-link tag="span"  :to='routNavigator'
          class="spanL">Previous Step</router-link>
        </div>
        <div v-if="checkRoutRight" class="right-step">
          <span class="spanR">Step 1/4</span>
        </div>
      </div>
        <router-view/>
    </div>
    <div class="main-futer">
      <div class="a-box">
        <a href="#">Privacy Policy</a>
        <a href="#">Terms Of Use</a>
      </div>
    </div>


  </div>
</template>

<script>
export default {
  data() {
    return {
      key: null
    }
  },
  computed: {
    checkRoutLeft() {
      if (this.$route.path !== '/'){
        return true
      }else{
        return false
      }
    },
    checkRoutRight(){
      if (this.$route.path !== '/' && this.$route.path !== '/end'){
        return true
      }else{
        return false
      }
    },
    routNavigator(){
      if (this.$route.path == '/step1'){
        return '/'
      }else if(this.$route.path == '/step2'){
        return '/step1'
      }else if(this.$route.path == '/step3'){
        return '/step2'
      }else if(this.$route.path == '/step4'){
        return '/step3'
      }else{
        return '/step4'
      }

    }
  },
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,200;0,300;0,400;0,500;0,600;0,700;0,800;1,200;1,300;1,400;1,500;1,600;1,700&display=swap');
*, 
::before, 
::after{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
    :focus{
      outline: none;
    }
.arow{
  color: #393939;
  height: 10px;
  background: black;
}
.main-box{
  margin: auto;
  margin-top: 110px;
  max-width: 1140px;
  height: 500px;
  display: flex;
  flex-direction: column;
  align-items: center;

  .step-box{
    height: 22px;
    width: 100%;
    display: flex;
    justify-content: space-between;

    .spanL{
      font-family: Poppins;
      font-style: normal;
      font-weight: normal;
      font-size: 14px;
      line-height: 21px;
      text-align: center;
      color: #393939;
      cursor: pointer;
    }
    .spanR{
      font-family: Poppins;
      font-style: normal;
      font-weight: 600;
      font-size: 16px;
      line-height: 24px;
      color: #5FB763;
      cursor: default;
    }
  }

    h1{
      font-family: Poppins;
      font-style: normal;
      font-weight: bold;
      font-size: 36px;
      line-height: 54px;
      color: #393939;
      margin-top: 135px;
      margin-bottom: 16px;
    }

    h4{
      color: #393939;
      font-family: Poppins;
      font-style: normal;
      font-weight: 500;
      font-size: 22px;
      line-height: 33px;
    }
}

      // ниже найстройка лого с лева и права
.logo-right{
position: absolute;
width: 154px;
height: 84px;
left: 100px;
top: 25px;
}
.phone-left{
position: absolute;
width: 18px;
transform: rotate(-6.14deg);
top: 56px;
right: 238px;
}
.number-left{
position: absolute;
top: 58px;
width: 130px;
right: 100px;
}

.main-futer{
  display: flex;
  flex-direction: column;
  width: 100vw;
}

.a-box{
  position: absolute;
  bottom: 80px;
  left: 38%;
    display: flex;
    justify-content: center;

      a{
        margin: 0 47px;
        display: flex;
        font-family: Poppins;
        font-style: normal;
        font-weight: 500;
        font-size: 14px;
        line-height: 21px;
        text-align: center;
        text-decoration-line: underline;
        color: #393939;
      }
}
</style>
