<template>
  <div>
    <h1>What car you shipping?</h1>
    <div class="input-box">
      <select class="inp-text">
        <option  value="start">Year</option>
        <option value="srt">1896</option>
      </select>
      <select class="inp-text">
        <option   value="Make">Make</option>
        <option value="srt">1896</option>
      </select>
      <select class="inp-text">
        <option  value="Model">Model</option>
        <option value="srt">1896</option>
      </select>
    </div>
  </div>
</template>

<script>
  export default {
    
  }
</script>

<style lang="scss" scoped>
.inp-text{
  padding: 15px 22px;
  height: 53px;
  background: #F5F5F5;
  border-radius: 5px;
  width: 270px;
  font-family: Poppins;
  font-style: normal;
  font-weight: 600;
  font-size: 17px;
  line-height: 25px;
  letter-spacing: 0.03em;
  color: #717171;
  border: none;
}
</style>