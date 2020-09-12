<template>
  <div>
    <div class="content">
      <div class="wrap-success">
        <img src="@/assets/success.svg" alt="success icon">
        <h1>Thank you!</h1>
        <p class="desc">
          Your quotes are calculated right now and will be sent
          to you the email address you indicated<br>
          <a class="mail-link" href="mailto:mail_user@gmail.com">{{user.email}}</a>
        </p>
        <router-link tag="span" class="btn without-arrow" to="/">Create another application</router-link>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
       user: null,
       date: null,
       traller: null,
       citi_1: null,
       citi_2: null,
      }
    },
    created () {
      this.user = JSON.parse(localStorage.user)
      this.traller =  JSON.parse(localStorage.traller)
      this.date =  JSON.parse(localStorage.Date)
      this.citi_1 =  JSON.parse(localStorage.cityOne)
      this.citi_2 =  JSON.parse(localStorage.cityTwo)
    },
  }
</script>

<style lang="scss" scoped>
  .wrap-success{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    h1{
      margin-top: 40px;
    }
  }
  .decs{
    margin: 0 0 50px 0;
  }
  .btn{
    margin-top: 55px;
  }


  @media screen and (max-width: 1460px) {

    .wrap-success h1{
      margin: 0;
    }

    .btn{
      margin-top: 25px;
    }
  }
  @media screen and (max-width: 1000px) {
    .wrap-success{
      img{
        width: 65px;
      }

      h1{
        margin-top: 10px;
      }

    }

    .desc{
      margin-top: 10px;
      font-size: 16px;
      line-height: 24px;
    }
  }

</style>