<template>
<div>
  <div class="first-main">
    <h1>Quickly Compare Cheap Car Shipping Quotes</h1>
    <h4>Save an average of 27% & make a fully informed decision</h4>
    <div class="supra-button-box">
    <div class="buton-box">
      <div class="gray-text-box-1">
      <span class="gray-text">PICKUP FROM</span>
        <input class="zip-text" placeholder="Enter ZIP Code or City" type="text">
      </div>
      <div class="gray-text-box-2">
        <hr>
        <span class="gray-text">DELIVERY TO</span>
        <span class="number-tex">80124</span>
      </div>
      <div class="btn">
        <span>Get started</span>
        <img src="@/assets/arow.svg" alt="arow">
      </div>

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
</template>

<script>
export default {
  data() {
    return {
      zipCity: 'start',
      zipCityArr: ['ua', 'dsa', 'udcx']
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
    box-shadow: 0px 4px 20px rgba(0, 0, 0, 0.1);
    border-radius: 5px;

    .gray-text-box-1{
      width: 274px;
      display: flex;
      flex-direction: column;
    }

    .gray-text-box-2{
      position: relative;
      display: flex;
      flex-direction: column;
      padding-left: 80px;
      margin-right: 52px;

      .number-tex{
        font-family: Poppins;
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

    .btn{
      height: 53px;
      width: 270px;
      background: #5FB763;
      box-shadow: 0px 2.77551px 15px #B1EFB4;
      border-radius: 5px;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;

      span{
        font-family: Poppins;
        font-style: normal;
        font-weight: 500;
        font-size: 16px;
        line-height: 24px;
        color: #FFFFFF;
      }

      img{
        color: #FFFFFF;
        height: 12px;
        margin-left: 8px;
      }
    }
    
    .zip-text{
      font-family: Poppins;
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
      font-family: Poppins;
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
      font-family: Poppins;
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
  width: 100vw;
  padding: 0 85px;

  p{
    margin: 90px 0 15px 0;
    font-family: Poppins;
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
}
</style>