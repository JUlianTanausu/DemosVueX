<template>
  <div id="product-list-one">
    <h2>Product List One</h2>
    <ul>
      <li v-for="product in saleProducts">
        <span class="name">{{ product.name }}</span>
        <span class="price">{{ product.price }}€</span>
      </li>
    </ul>
    <button v-on:click="reducePrice(4)">Reduce Price</button>
  </div>
</template>

<script>
import {mapActions} from 'vuex';
import {mapGetters} from 'vuex';

export default{
/*llama a la var product de app o algo
  props: ['products'],
  */
  computed: {
    products(){
      return this.$store.state.products
    },

    ...mapGetters([
      'saleProducts'//,
      //'siguiente'
    ])


  },
  methods:{
    /*
    reducePrice: function(amount){
      this.$store.state.products.forEach(product => {
        product.price -= 1;
      })
      this.$store.dispatch('reducePrice', amount);//para llamar al action
    }
    */

    ...mapActions([
      'reducePrice' //action
    ])
  }


}
</script>

<style scoped>

#product-list-one{
  background: #FFF8B1;
  box-shadow: 1px 2px 3px rgba(0,0,0,0,2);
  margin-bottom: 30px;
  padding: 10px 20px;
}

#product-list-one ul{
  padding: 0;
  list-style-type: none;
}

#product-list-one li{
  margin-right: 10px;
  margin-top: 10px;
  padding: 20px;
  background: rgba(255,255,255,0.7);
}

.price{
  font-weight: bold;
  color:#E8800C;

}


</style>
