<template>
  <div>
    <div class="content">
      <h1>We`ve found great rates for you!</h1>
      <p class="desc">You`re one click away from viewing your matches.</p>
      <div id="info-form">
        <input v-model="name" type="text" name="name" placeholder="Name" required>
        <input class="number" v-model="phone" type="number" name="phone" placeholder="Phone number" required>
        <input v-model="email" type="email" name="phone" placeholder="Email" required>
      </div>
      <button :disabled='!valid' @click="goToNextStep"
       class="btn without-arrow" >Get My Car Shipping Quotes</button>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        name: '',
        phone: '',
        email: ''
      }
    },
    computed: {
      valid() {
        if(this.name !== '' && this.phone !== '' && this.validMail == true){
          return true
        }else {return false}
      },
      validMail(){
        let reg = /^([A-Za-z0-9_\-\.])+\@([A-Za-z0-9_\-\.])+\.([A-Za-z]{2,4})$/
        if (reg.test(this.email)){
          return true
        }else{return false}
      }
    },
    methods: {
      goToNextStep() {
        localStorage.user = JSON.stringify({name: this.name, phone: this.phone, email: this.email})
        this.$router.push('/end') 
      }
    },
  }
</script>

<style lang="scss" scoped>

  #info-form{
    width: 270px;
    margin-top: 35px;

  }

  #info-form input{
    font-family: Poppins;
    width: 100%;
    padding: 15px 20px;
    margin-top: 15px;
    border-radius: 5px;
    font-size: 16px;
    background: #F5F5F5;
    color: #393939;
    border: none;
  }

  #info-form input::placeholder{
    line-height: 24px;
    color: #B9B9B9;
  }

  input[type='number'] {
    -moz-appearance:textfield;
  }

  input::-webkit-outer-spin-button,
  input::-webkit-inner-spin-button {
    -webkit-appearance: none;
  }

  @media screen and (max-width: 1000px) {
    #info-form
    {
      width: 220px;
      margin-top: 25px;
      input{
      font-size: 14px;
      }
    }
  }

</style>