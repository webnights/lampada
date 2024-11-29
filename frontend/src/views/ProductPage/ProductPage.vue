<template>
   <section class="product__page">
       <div class="container">
           <div class="product__inner">
               <div class="product__info">
                  <img :src="product().image " alt="">
                  <div class="product__content">
                     <label><h2>{{product().name}}</h2></label>
                     <label><p>{{product().description}}</p></label>
                     <ul>
                        <li>Дата: {{product().date}}</li>
                        <li>Время: {{product().time}}</li>
                        <li>Адрес: {{product().address}}</li>
                     </ul>
                  </div>
               </div>
           </div>
       </div>
   </section>
</template>

<script>

import dataJson from '/src/assets/data/Data.json';

export default {
   props: {
       id: {
           type: Number, 
           required: true,
       },
   },
   data(){
      return{
         products: dataJson.products,
         
      }
   },
   methods:{
      product(){
         const result = this.products.find((product) => product.id == this.id);
         console.log(result)
         return result;
      }
   }
 
};
</script>
