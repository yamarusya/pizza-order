<template>
  <div class="home">
    <div class="leftColumn"> 
      <h2> {{name}} </h2>
      <h3> Address </h3> 
    </div>
    <div class="rightColumn">   
        <h2> {{ price }} руб.</h2>     
          <div class="form">
            <p>
                <input v-model="street" placeholder="street" />
            </p>
            <p>
                <input v-model="house" placeholder="house" />
            </p>
            <p>
                <input v-model="flat" placeholder="flat" />
            </p>
          <button class="orderButton" :disabled="!this.flat || !this.house || !this.street"
            @click="ordered()"
          >
            Make order
          </button>
        </div>
      </div>
    </div>
</template>

<script scoped>
export default {
  name: 'OrderPage',
  props: {
    name: {
      type: String,
      default: null
    },
    price: {
      type: Number,
      default: null
    }
  },
  data(){
      return {
          street: '',
          house: null,
          flat: null
      }
  },
  methods:{
    ordered(){
       this.$router.push('/')
      alert(`Pizza ordered! It will be delivered to ${this.street}  ${this.house}, ${this.flat}`)
    }
  }
}
</script>

<style scoped>
.rightColumn{
  float: left;
  width: 60%;
}
.leftColumn{
  width: 30%;
  text-align: right;
  float: left;
}
.form{
    display: inline-block;
    width: 80%;
}

.orderButton{
    float: right;
    width: 40%;
    border-radius: 4px;
}

input {
  border: 1px solid #eee;
  border-radius: 4px;
  width: 80%;
  height: 52px;
  max-width: 100%;
  margin-top: 2%;
  margin-bottom: 20px;
  padding: 0 8px 0 8px;
}
</style>