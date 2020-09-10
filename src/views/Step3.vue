<template>
  <div>
    <div class="content">
      <h1>Would you like to use open or enclosed traller?</h1>
      <div class="wrap-radio">
        <label class="custom-checkbox">
          <span class="title">Open Trailer</span>
          <span class="description">Cost less</span>
          <span class="description"> Vehicle is on open air</span>
          <input type="radio" checked="checked" name="traller" value="Open Trailer">
          <span class="checkmark"></span>
        </label>
        <label class="custom-checkbox">
          <span class="title">Enclosed Trailer</span>
          <span class="description">Cost more </span>
          <span class="description">Vehicle is protected from weather</span>
          <input type="radio" name="traller" value="Enclosed Trailer">
          <span class="checkmark"></span>
        </label>
      </div>
      <router-link tag="span" class="btn" to="/step4">Next step</router-link>
    </div>
  </div>
</template>

<script>
  export default {
    
  }
</script>

<style lang="scss" scoped>

  .wrap-radio{
      display: flex;
      align-items: center;
      margin-top: 40px;
  }

  .custom-checkbox{
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    text-align: center;
    position: relative;
    width: 270px;
    height: 187px;
    margin: 10px;
    background: #FFFFFF;
    color: #393939;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.05);
    border-radius: 5px;
    cursor: pointer;
    padding: 40px;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;

    .title{
      font-size: 18px;
      margin-bottom: 10px;
      font-weight: 600;
    }

    .description{
      font-size: 16px;
    }
    input {
      position: absolute;
      opacity: 0;
      cursor: pointer;
    }

    .checkmark {
      position: absolute;
      top: 12px;
      right: 12px;
      height: 20px;
      width: 20px;
      border-radius: 50%;
      background-color: #fff;
      border: 1px solid #DDDDDD;
      box-sizing: border-box;

    }

    &:hover input ~ .checkmark {
      background-color: #ccc;
    }

    input:checked ~ .checkmark {
      background-color: #fff;
    }

    input:checked ~ .checkmark:after {
      display: block;
    }

    .checkmark:after {
      content: "";
      position: absolute;
      display: none;
      top: 2px;
      left: 2px;
      width: 14px;
      height: 14px;
      border-radius: 50%;
      background: #5FB763;
    }
  }

  .btn{
    margin-top: 60px;
  }


  @media screen and (max-width: 1460px) {
    .wrap-radio{
      margin-top: 20px;
    }
    .btn{
      margin-top: 60px;
    }
  }

</style>