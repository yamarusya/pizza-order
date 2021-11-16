<template>
  <div class="home">
    <div class="carousel-container">
      <button class="left" @click="left()"> &lt;</button>
      <router-link :to="{name: 'Order', params: {name: el.name, price: el.price}}" 
        v-for="(el, index) in dataToDisplay"
        v-bind:key="index"
        class="card"
      >
        <img alt="" :src='"../assets/"+`${el.name}`+".jpeg"'>
        <div>
          {{ el.name }}
          <p> <strong> Price: </strong> {{ el.price }} </p>
        </div>
      </router-link>
      <button class="right" @click="right()">&gt;</button>
      </div>
    </div>
</template>

<script>
const pizzaCatalog = [
  {
    name: 'Маргарита',
    price: 375
  },
  {
    name: 'Пепперони',
    price: 435
  },
  {
    name: 'Карбонара',
    price: 495
  },
  {
    name: 'Мясная',
    price: 500
  },
  {
    name: 'Сырная',
    price: 245
  },
  {
    name: 'Песто',
    price: 495
  },
   {
    name: 'Пепперони',
    price: 435
  },
  {
    name: 'Карбонара',
    price: 495
  },
  {
    name: 'Мясная',
    price: 500
  },
  {
    name: 'Сырная',
    price: 245
  },
  {
    name: 'Песто',
    price: 495
  },
  {
    name: 'Мясная',
    price: 500
  },
  {
    name: 'Сырная',
    price: 245
  },
  {
    name: 'Песто',
    price: 495
  },
  {
    name: 'Мясная',
    price: 500
  },
  {
    name: 'Сырная',
    price: 245
  },
  {
    name: 'Песто',
    price: 495
  }
]

export default {
  name: 'Home',
  data() {
    return {
      currentPage: 0,
      pizzaCatalog: pizzaCatalog,
      dataToDisplay: null
    }
  },
  created(){
    this.dataToDisplay = pizzaCatalog.slice(this.currentPage, this.currentPage+6)
  },
  methods: {
    left(){
      if ( this.currentPage === 0) return
      this.currentPage-=1
      this.dataToDisplay = pizzaCatalog.slice(this.currentPage*6, (this.currentPage+1)*6)
    },
    right(){
      if (this.pizzaCatalog.length - 6*(this.currentPage+1) <= 0) return
      this.currentPage+=1
      this.dataToDisplay = pizzaCatalog.slice(this.currentPage*6, this.currentPage*6+6)
    }
  }
}
</script>

<style>
.carousel-container{
  display: block;
  margin-left: 5%;
  max-width: 87%;
  position: absolute;
  right: 0;
}
.carousel-container > button{
  height: 5%;
  width: 5%;
  border-radius: 8px;
  z-index: 2;
  top: 48%;
  position: absolute;
}
.card{
  border-radius: 8px;
  margin: 1%;
  width: 20%;
  background: rgb(189, 201, 228);
  padding: 3%;
  float: left;
  text-decoration: none !important;
  color: black;
  text-align: left;
}
img{
  margin-bottom: 10px;
  display: block;
  max-width: 100%;
}
.left{
  left: -1%;
  float: left;
}
.right{
  margin-left: -10%;
  float: right;
}
</style>