<template>
<Master>
    <Loader v-show="isLoad"/>
    <div class="container" v-show="!isLoad">
        <div class="row">
            <div v-for="p in products" :key="p.id" class="col-md-4" >
                <div class="card  m-3" >
                    <div class="card-header">{{p.title}}</div>
                    <div class="card-body">
                        <img src="https://s.alicdn.com/@sc04/kf/Hfdb38af816234fd08196cbcec4432c5eK.jpg_220x220.jpg" alt="">
                    </div>
                    <div class="card-footer">
                        <span>Price:<small>$100</small></span>
                        <a @click="addToCart(p)" class="btn btn-sm btn-dark float-right">Add To Cart</a>
                    </div>
                </div>
            </div>
        </div>

    </div>
</Master>
    
</template>
<script>
import Master from "../Layout/Master";
import Loader from "../Component/Loader";
import axios from 'axios';
export default {
    components:{Master,Loader},
    name:"Product",
    data(){
        return{
            isLoad:true,
            products:[],
        };
    },
    created(){
        axios.get("http://jsonplaceholder.typicode.com/posts").
        then(res=>{
           this.products=res.data;
           this.isLoad=false;
        })
    },
    methods:{
        addToCart(p){
           var cart=this.$root.cart;
           var isInCart=cart.find(v=>{
               return v.id==p.id;
           })
           if(isInCart){
               isInCart.qty++;
           }
           else{
                cart.push({...p,qty:1});
           }
          
        }
    }
}
</script>