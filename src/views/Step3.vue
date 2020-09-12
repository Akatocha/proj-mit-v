<template>
  <div>
    <div class="content">
      <h1>Would you like to use open or enclosed traller?</h1>
      <div class="wrap-radio">
        <label class="custom-checkbox">
          <span class="title">Open Trailer</span>
          <span class="description">Cost less</span>
          <span class="description"> Vehicle is on open air</span>
          <input type="radio" @change="changeChack" :checked="checked_1" name="traller" value="Open Trailer">
          <span class="checkmark"></span>
        </label>
        <label class="custom-checkbox">
          <span class="title">Enclosed Trailer</span>
          <span class="description">Cost more </span>
          <span class="description">Vehicle is protected from weather</span>
          <input type="radio" @change="changeChack" :checked="checked_2" name="traller" value="Enclosed Trailer">
          <span class="checkmark"></span>
        </label>
      </div>
      <router-link tag="span" class="btn" to="/step4">Next step</router-link>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        checked_1: true,
        checked_2: false,
      }
    },
    methods: {
      changeChack() {
        this.checked_1 = !this.checked_1
        this.checked_2 = !this.checked_2
        localStorage.traller = JSON.stringify(this.traller)
      }
    },
    computed: {
      traller() {
        if (this.checked_1){
          return 'Open Trailer'
        }else{
          return 'Enclosed Trailer'
        }
      }
    },
    created () {
      localStorage.traller = JSON.stringify(this.traller)
    },
  }
</script>

<style lang="scss" scoped>

  .wrap-radio{
      display: flex;
      align-items: center;
      margin-top: 35px;
  }

  .custom-checkbox{
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    text-align: center;
    position: relative;
    width: 270px;
    height: 185px;
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


  @media screen and (max-width: 1460px) {
    .wrap-radio{
      margin-top: 20px;
    }
  }

  @media screen and (max-width: 1000px) {
    .wrap-radio{
      flex-direction: column;
    }
    .custom-checkbox{
      width: 220px;
      height: 155px;
      .title{
        font-size: 17px;
      }
      .description{
        font-size: 13px;
      }
    }
  }


</style>