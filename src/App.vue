<template>
  <div>
      <img class="logo-right" src="@/assets/logo_transparent_1.svg" alt="logo">
      <img class="phone-left" src="@/assets/Phone.svg" alt="phone">
      <img class="number-left" src="@/assets/number.svg" alt="phone">

    <div class="main-box">
      <div class="step-box"></div>
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

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,200;0,300;0,400;0,500;0,600;0,700;0,800;1,200;1,300;1,400;1,500;1,600;1,700&display=swap');
*, 
::before, 
::after{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
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
