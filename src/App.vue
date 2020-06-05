<template>
  <div id="app">
      <div class="container">
        <h2 align="center">Workshop #3 - คำนวณราคาสินค้า</h2>
        <hr>
        <div class="row">
            <div class="col-md-3" v-for="item in products">
              <div class="card h-100">
                    <img :src="item.image" class="card-img-top">
                    <div class="card-body">
                          <h4 class="card-title">{{item.name}}</h4>
                          <p class="card-text">ราคา {{item.price}} บาท</p>
                    </div>
                    <div class="card-footer">
                          <input type="checkbox" class="form-control" @change="selected(item)">
                    </div>
              </div>
            </div>
            <h4>ยอดชำระเงิน {{total()}} บาท </h4>
        </div>
      </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      products:[
        {
          id:1,
          name:"กาแฟเย็น",
          price:30,
          image:"https://cdn.pixabay.com/photo/2017/06/21/01/17/coffee-2425652_960_720.jpg",
          active:false
        },
        {
          id:2,
          name:"ชาเย็น",
          price:35,
          image:"https://cdn.pixabay.com/photo/2015/08/26/11/20/beverage-908356_960_720.jpg",
          active:false
        },
        {
          id:3,
          name:"ชามะนาว",
          price:50,
          image:"https://cdn.pixabay.com/photo/2018/01/11/17/29/ice-tea-3076517__340.jpg",
          active:false
        }
      ]
    }
  },
  methods:{
    selected:function(item){
        item.active = !item.active
    },
    total:function(){
        var sum=0;
        this.products.forEach(function(item){
              if(item.active){
                  sum+=item.price; 
              }
        });
        return sum;
    }
  }
}
</script>

