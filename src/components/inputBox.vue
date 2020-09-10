<template>
  <div>
      <div class="wrap-input-group">
          <div class="input-group">
            <select @change="selectYear" v-model="year" class="inp-text">
              <option disabled value="start">Year</option>
              <option
              v-for="(year, key) in yearsArr"
              :key="key"
              :value="year">{{year}} </option>
            </select>

              <label class="checkbox-container">
                  <input type="checkbox">
                  <span class="checkbox-custom"></span>
                  <span class="label">Inoperable</span>
                  <span class="bottom-desc">Doesn`t Run</span>
              </label>
          </div>
          <div class="input-group">
            <select @change="selectMake" v-model="makeId" class="inp-text">
              <option disabled value="start">Make</option>
              <option
              v-if="responseMake"
              v-for="(make, key) in responseMake"
              :key="key"
              :value="make.id">{{make.value}} </option>
            </select>
              <label class="checkbox-container">
                  <input type="checkbox">
                  <span class="checkbox-custom"></span>
                  <span class="label">Modified</span>
                  <span class="bottom-desc">Lift kits, large tires, extra weight, ets.</span>
              </label>
          </div>
          <div class="input-group">
            <select @change="selectModel" v-model="modelId" class="inp-text">
              <option disabled value="start">Model</option>
              <option
              v-if="responseModel"
              v-for="(model, key) in responseModel"
              :key="key"
              :value="model.id">{{model.value}} </option>
            </select>

              <div class="checkbox-container add-button-container">
                <button
                v-if="showButton"
                :disabled='!buttonEnabled'
                @click="addInput" >Add another vehicle</button>

              </div>
          </div>
          <span class="button-delete"></span>
      </div>
    </div>

</template>

<script>
  export default {
    data() {
      return {
        year: 'start',
        makeId: 'start',
        modelId: 'start',
        responseMake: null,
        responseModel: null,
        buttonEnabled: false,
        showButton: true,
      }
    },
    computed: {
      yearsArr() {
        let years = []
        for (let i = 2021; i >= 1917; i--){
          if(i == 1943 || i == 1944){
            continue;
          }
          years.push(i)
        }
        return years
      }
    },
    methods: {
      selectModel(){
        this.buttonEnabled = true
        // console.log(this.modelId)
        this.$emit('catchDataFromInput', this.modelId)
      },
      selectMake(){
        let idMake = this.makeId
        this.axios.get(`https://quotebooster.com/api/model/by_make_id.json?make_id=${idMake}`)
        .then((response) => {
          // console.log(response.data)
          this.responseModel = response.data
        }).catch(err => console.log(err))
      },
      selectYear(){
        let year = this.year
        this.axios.get(`https://quotebooster.com/api/make/by_year.json?year=${year}`)
        .then((response) => {
          // console.log(response.data)
          this.responseMake = response.data
        }).catch(err => console.log(err))
      },
      addInput(){
        this.$emit('addInput')
        this.showButton = false
      }
    },
  }
</script>

<style lang="scss" scoped>

    .wrap-input-group{
        position: relative;
        display: flex;
        width: 100%;
        justify-content: space-between;
        .input-group{
            width: 285px;
            padding: 10px;
        }

        .button-delete {
            position: absolute;
            right: -40px;
            top: 20px;
            width: 32px;
            height: 32px;
            opacity: 0.5;
            cursor: pointer;

            &:first-child{
                display: none;
            }

            &:hover {
                opacity: 1;
            }
            &:before, &:after {
                position: absolute;
                left: 15px;
                content: ' ';
                height: 33px;
                width: 2px;
                background-color: #5FB763;
            }
            &:before {
                transform: rotate(45deg);
            }
            &:after {
                transform: rotate(-45deg);
            }
        }
    }
    .content > div:nth-child(2) .button-delete{
        display: none;
    }

  .checkbox-container{
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    cursor: pointer;
    width: 100%;
    margin: 0 10px;

    input[type="checkbox"]{
      display: none;
    }
    .checkbox-custom {
      position: relative;
      width: 22px;
      height: 22px;
      border: 1px solid #BABABA;
      box-sizing: border-box;
      border-radius: 2px;

      &:before {
        content: "";
        display: block;
        position: absolute;
        top: -5px;
        left: 5px;
        width: 0;
        height: 0;
        opacity: 0;
        background-image: url("data:image/svg+xml,%3Csvg width='26' height='20' viewBox='0 0 26 20' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M8.48226 15.8949L8.63679 16.0408L8.78121 15.8849L23.2205 0.298968L25.0566 2.03232L8.61801 19.4912L0.359295 11.6947L2.19615 9.96066L8.48226 15.8949Z' fill='%235FB763' stroke='white' stroke-width='0.421053'/%3E%3C/svg%3E%0A");
        background-repeat: no-repeat;
        visibility: hidden;
        transition: width 0.6s ease-in-out, width 0.6s ease-in-out, visibility 0.3s ease-in-out, opacity 0.3s ease-in-out;
      }
    }



    &:hover .checkbox-custom:before,
    input[type="checkbox"]:checked + .checkbox-custom:before{
      width: 25px;
      height: 22px;
      opacity: 1;
      visibility: visible;
    }
    &:hover .checkbox-custom:before{
        background-image: url("data:image/svg+xml,%3Csvg width='26' height='20' viewBox='0 0 26 20' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M8.48226 15.8949L8.63679 16.0408L8.78121 15.8849L23.2205 0.298968L25.0566 2.03232L8.61801 19.4912L0.359295 11.6947L2.19615 9.96066L8.48226 15.8949Z' fill='%23BABABA' stroke='white' stroke-width='0.421053'/%3E%3C/svg%3E%0A");
    }
    input[type="checkbox"]:checked + .checkbox-custom:before{
        background-image: url("data:image/svg+xml,%3Csvg width='26' height='20' viewBox='0 0 26 20' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M8.48226 15.8949L8.63679 16.0408L8.78121 15.8849L23.2205 0.298968L25.0566 2.03232L8.61801 19.4912L0.359295 11.6947L2.19615 9.96066L8.48226 15.8949Z' fill='%235FB763' stroke='white' stroke-width='0.421053'/%3E%3C/svg%3E%0A");
    }

    .label{
      font-size: 16px;
      font-weight: 500;
      color: #393939;
      margin-left: 8px;
    }
    .bottom-desc{
      font-size: 15px;
      margin-top: 8px;
      color: #BBBBBB;
      width: 100%;
    }

  }

  .inp-text{
    padding: 15px 20px;
    height: 50px;
    background: #F5F5F5;
    border-radius: 5px;
    width: 100%;
    margin-bottom: 10px;
    font-family: Poppins;
    font-size: 16px;
    line-height: 25px;
    letter-spacing: 0.03em;
    color: #393939;
    font-weight: 500;
    border: none;
    option {
        font-size: 16px;
        line-height: 25px;
        letter-spacing: 0.03em;
        color: #393939;
    }

    option:disabled,
    ::placeholder {
           color: #B9B9B9;
       }
   }

  .add-button-container {
    align-items: baseline;

    button{
        display: flex;
        align-items: center;
        border: none;
        background: none;
        color: #5FB763;
        font-weight: 500;
        font-size: 16px;
        cursor: pointer;

        &:before {
            content: '+';
            display: flex;
            justify-content: center;
            align-items: center;
            width: 22px;
            height: 22px;
            font-size: 18px;
            color: #fff;
            background: #5FB763;
            border-radius: 2px;
            margin-right: 8px;
        }
    }

    [disabled="disabled"] {
      opacity: 0.5;
    }

    [disabled="disabled"] + span {
      opacity: 0.5;
    }
  }


</style>