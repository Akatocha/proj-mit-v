<template>
  <div>
    <div id="main-header">
      <img class="logo" src="@/assets/logo_main.png" alt="QuoteBooster">
      <span class="hide-mobile phone-number">904 - 297 -1778</span>
      <div id="wrap-menu-mobile">
        <input class="menu-btn" type="checkbox" id="menu-btn" />
        <label class="menu-icon" for="menu-btn"><span class="navicon"></span></label>
        <div class="menu">
            <p>Get fast online quote from top-rated companies. Save up to 27% now!</p>
            <span class="phone-number">904 - 297 -1778</span>
        </div>
      </div>
    </div>
    <div class="main-box">
      <div class="step-box">
        <div v-if="checkRoutLeft" class="left-step">
          <!-- <img class="arow" src="@/assets/arow.svg" alt=""> -->
          <router-link tag="span"  :to='routNavigator'
          class="spanL"><i><</i> Previous Step</router-link>
        </div>
        <div v-if="checkRoutRight" class="right-step">
          <span 
          class="spanR">Step {{step}}/4</span>
        </div>
      </div>
        <router-view/>

        <div id="main-footer">
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
    step(){
      if( this.$route.path == '/step1'){
        return 1
      }if( this.$route.path == '/step2'){
        return 2
      }if( this.$route.path == '/step3'){
        return 3
      }if( this.$route.path == '/step4'){
        return 4
      }
    },
    checkRoutLeft() {
      if (this.$route.path !== '/' && this.$route.path !== '/end'){
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
::selection {
  color: #fff;
  background: #B1EFB4;
}
body{
  font-family: Poppins;
  color: #393939;
}
.arow{
  color: #393939;
  height: 10px;
  background: black;
}
.main-box{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  margin: 0 auto;
  max-width: 1140px;
  height: calc(100vh - 280px);

  .content{
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .step-box{
    height: 22px;
    width: 100%;
    display: flex;
    justify-content: space-between;

    .spanL{
      display: flex;
      font-style: normal;
      font-weight: normal;
      font-size: 14px;
      line-height: 21px;
      text-align: center;
      color: #393939;
      cursor: pointer;
      outline: none;
      -moz-user-select: none;
      -khtml-user-select: none;
      user-select: none;

        i{
        font-size: 21px;
        font-style: initial;
        margin-right: 6px;
      }
    }
    .spanR{
      font-style: normal;
      font-weight: 600;
      font-size: 16px;
      line-height: 24px;
      color: #5FB763;
      cursor: default;
    }
  }

    h1{
      font-style: normal;
      font-weight: bold;
      font-size: 36px;
      line-height: 54px;
      color: #393939;
      margin-bottom: 16px;
    }

    h4{
      color: #393939;
      font-style: normal;
      font-weight: 500;
      font-size: 22px;
      line-height: 33px;
      margin-bottom: 53px;
    }
}

#main-header{
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 100px 85px 100px;


  .logo{
    width: 155px;
  }

  .phone-number {
    display: flex;
    align-items: center;
    font-weight: 500;
    font-size: 18px;

    &:before{
      display: block;
      content: ' ';
      width: 18px;
      height: 19px;
      margin-right: 15px;
      background: url("data:image/svg+xml,%3Csvg width='18' height='20' viewBox='0 0 18 20' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M15.5692 13.6097C15.0386 13.061 14.1884 12.2747 13.5316 12.2621C13.132 12.2545 12.7148 12.6366 12.3022 12.999C12.2198 13.0528 11.5908 13.5341 11.5117 13.5673C11.094 13.7392 10.1777 13.8748 9.5655 13.4169C8.97593 12.9746 8.02913 12.1402 7.25405 11.3661C6.50671 10.5631 5.7088 9.58682 5.28883 8.98013C4.8511 8.35176 5.01965 7.44014 5.20435 7.02692C5.23821 6.95248 5.68264 6.37308 5.78167 6.23881L5.80015 6.25705C6.17684 5.85689 6.57253 5.44908 6.57947 5.05272C6.59004 4.39299 5.83579 3.51544 5.30516 2.96561C4.77441 2.41467 3.93923 1.44017 2.97185 1.69481C2.60756 1.79019 2.30269 1.95672 2.00839 2.18055L1.99861 2.17149C1.9824 2.18679 1.96645 2.20237 1.95075 2.21822L1.92508 2.23559L1.92883 2.23968C1.76334 2.40134 1.28944 2.85016 1.23637 2.90981C0.660452 3.55729 -0.15346 5.02383 0.852968 7.396C1.59998 9.15883 3.00517 11.1723 4.83881 13.1644L4.83093 13.1731C4.92057 13.2691 5.01132 13.3549 5.10387 13.4472C5.19121 13.5424 5.27735 13.6365 5.36675 13.7303L5.37681 13.7213C7.30021 15.6262 9.26133 17.1034 10.9931 17.9129C13.3245 19.0018 14.8166 18.2379 15.4843 17.6861C15.5469 17.6333 16.0171 17.1703 16.1769 17.0171L16.1817 17.0211C16.1875 17.0137 16.1909 17.0044 16.1989 16.9968C16.2133 16.983 16.2276 16.9691 16.2418 16.9551L16.2343 16.9469C16.4699 16.6586 16.6513 16.3581 16.7596 15.9924C17.0428 15.0303 16.0999 14.1606 15.5692 13.6097Z' fill='%23393939'/%3E%3C/svg%3E%0A");
      transform: rotate(-6.14deg);
    }
  }
}

#wrap-menu-mobile{
  display: none;
}

#main-footer{
  display: flex;
  justify-content: center;
  bottom: 85px;
  width: 100%;
  margin-top: 70px;
      a{
        margin: 0 45px;
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


.btn{
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Poppins;
  font-weight: 500;
  font-size: 16px;
  margin-top: 60px;
  height: 53px;
  width: 270px;
  background: #5FB763;
  box-shadow: 0 2.77551px 15px #B1EFB4;
  border-radius: 5px;
  cursor: pointer;
  color: #FFFFFF;
  border: none;

  &:after{
    width: 24px;
    font-weight: 100;
    content: '>';
    font-style: initial;
    font-size: 24px;
    margin-left: 4px;
  }

  &.without-arrow:after{
    display: none;
  }
}


.desc{
  font-weight: 500;
  font-size: 22px;
  line-height: 36px;
  text-align: center;
  max-width: 600px;

  .mail-link{
    color: #5FB763;
    text-decoration: none;
  }
}

@media screen and (max-width: 1460px) {
  .btn{
    margin-top: 40px;
  }
  #main-header {
    padding-bottom: 20px;
  }
  #main-footer{
    margin: 20px 0;
  }
  .main-box{
    height: calc(100vh - 118px);
  }

  .futer{
    margin-top: 35px;
  }
}

@media screen and (max-width: 1000px) {

  .hide-mobile {
    display: none !important;
  }
  .btn{
    width: 220px;
    margin-top: 35px;
    font-size: 14px;
  }
  #main-header {
    padding: 30px;
    justify-content: center;
  }
  .menu {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      width: 100%;
      background-color: #fff;
      margin-top: 80px;
      max-height: 0;
      transition: max-height .2s ease-out;
      overflow: hidden;
      box-shadow: 0 16px  2px -2px rgba(0, 0, 0, 0.05);

      p{
          text-align: center;
          font-size: 14px;
      }
      .phone-number{
          margin-top: 40px;
      }
  }


    #wrap-menu-mobile{
    position: absolute;
    display: block;
    right: 0;
    top: 30px;
    width: 100%;

    .menu-icon {
      cursor: pointer;
      display: inline-block;
      float: right;
      padding: 28px 20px;
      position: relative;
      user-select: none;
      .navicon {
          background: #393939;
          display: block;
          height: 2px;
          position: relative;
          transition: background .2s ease-out;
          width: 18px;
          &:before,
          &:after {
              background: #393939;
              content: '';
              display: block;
              height: 100%;
              position: absolute;
              transition: all .2s ease-out;
              width: 100%;
          }
          &:before { top: 5px; }
          &:after  { top: -5px; }
        }
    }

    .menu-btn {
      display: none;
      &:checked ~ .menu {
        max-height: 240px;
        padding: 35px;
      }

      &:checked ~ .menu-icon .navicon {
        background: transparent;
      }

      &:checked ~ .menu-icon .navicon:before {
        transform: rotate(-45deg);
      }

      &:checked ~ .menu-icon .navicon:after {
        transform: rotate(45deg);
      }

      &:checked ~ .menu-icon:not(.steps) .navicon:before,
      &:checked ~ .menu-icon:not(.steps) .navicon:after {
        top: 0;
      }
    }
  }

  .main-box{
    width: 100%;
    padding: 20px;
    box-sizing: border-box;
    min-height: calc(100vh - 140px);

    h1{
      font-size: 20px;
      line-height: 30px;
      margin-top: 25px;
      text-align: center;
    }
  }


  #main-footer{
    align-items: center;
    justify-content: space-around;
    a{
      margin: 0;
      font-size: 12px;
    }
  }
}
</style>
