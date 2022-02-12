<template>
    <Master>
        <div class="container">
            <table class="table table-striped">
                <tr>
                    <td>Name</td>
                    <td>image</td>
                    <td>+ -</td>
                    <td>Qty</td>
                    <td>price</td>
                    <td>Total</td>
                </tr>
                <tr v-for="p in cart" :key="p.id">
                    <td>{{p.title}}</td>
                    <td>
                        <img src="https://s.alicdn.com/@sc04/kf/Hfdb38af816234fd08196cbcec4432c5eK.jpg_220x220.jpg" width="100px" alt="">
                    </td>
                    <td>
                        <span @click="addQty(p)" class="btn btn-small btn-success">+</span>
                         <span @click="reduceQty(p)" class="btn btn-small btn-danger">-</span>
                    </td>
                    <td>{{p.qty}}</td>
                    <td>$100</td>
                    <td>{{p.qty*100}}</td>
                </tr>
            </table>
        </div>
    </Master>
</template>
<script>
import Master from "../Layout/Master";
export default {
    components:{Master},
    name:"Cart",
    data(){
        return {
            cart:[],
        };
    },
    created(){
        this.cart=this.$root.cart;
    },
    methods:{
        addQty(p){
            p.qty++;
        },
        reduceQty(p){
            p.qty--;
        },
    }
}
</script>