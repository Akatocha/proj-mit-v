<template>
  <div>
    <div class="content">
      <h1>We`ve found great rates for you!</h1>
      <p class="desc">You`re one click away from viewing your matches.</p>
      <div id="info-form">
        <input type="text" name="name" placeholder="Name" required>
        <input type="text" name="phone" placeholder="Phone number" required>
        <input type="email" name="phone" placeholder="Email" value="mail_user@gmail.com" required>
      </div>
      <router-link tag="span" class="btn without-arrow" to="/end">Get My Car Shipping Quotes</router-link>
    </div>
  </div>
</template>

<script>
  export default {
    
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