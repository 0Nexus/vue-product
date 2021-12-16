<template>
<div>
    <nav class="navbar navbar-dark bg-dark">
        <form action="" class="form-inline">
            <select name="color" v-model="color" id="color"     >
                <option value="Red" class="text-danger">Red</option>
                <option value="White" class="text-white-50">White</option>
                <option value="Yellow" class="text-warning">Yellow</option>
                <option value="Green" class="text-success">Green</option>
                <option value="Blue" class="text-primary">Blue</option>
                <option value="Black" class="text-dark">Black</option>
            </select>
            <input type="number" name="reduc" v-model="reduc" id="reduc" placeholder="%">
            <input type="text" name="names" v-model="names" id="names">
        </form>
    </nav>
    <div  id=prod>
 <table class="table table-striper table-dark">
     <thead>
         <tr>
         <th scope="col">id</th>
         <th scope="col">name</th>
         <th scope="col">price</th>
         <th scope="col">quantity</th>
         <th scope="col">color</th>
         </tr>
     </thead>
     <tbody>
         
        <tr v-for="product in filterproduct" :key="product.id">
         <th>{{ product.id }}</th>
         <th>{{ product.name }}</th>
         <th>{{ product.price }}</th>
         <th>{{ product.qte }}</th>
         <th>{{ product.color }}</th>
         </tr>
        <tr>
            <th> total price</th>
            <th></th>
            
        </tr>
        
     </tbody>
     
 </table>
 <h1>{{ total }}</h1>
    </div>
</div>
</template>
<script>

export default {
    

    data(){
        return{
            products:[
                {"id":1,"name":'pen',"price":230,"qte":1200,"color":'Blue'},
                {"id":2,"name":'paper',"price":40,"qte":100,"color":'White'},
                {"id":3,"name":'mouse',"price":250,"qte":50,"color":'Red'},
                {"id":4,"name":'back-pack',"price":150,"qte":10,"color":'Black'},
                {"id":5,"name":'tiles',"price":20,"qte":1120,"color":'Green'},
                {"id":6,"name":'pads',"price":130,"qte":300,"color":'Yellow'},
            ],
            color:'',
            names:'',
            //total: 5,
            reduc: 10,
            
            
      }
        
    },
      computed : {
        
        filterproduct: function(){
            return this.filtreC(this.filtreN(this.products))
        },
        total:function(){
            let total_price = 0;
            console.log('sjdso')
            for( let p of this.products){
                total_price = total_price + parseInt(p.price) * parseInt(p.qte)
            }
           return total_price
        }
          //totalrep:function(){
           // return(this.total(this.products))
        
        
    },
    created(){
        

    },
    methods:{
            
            
            filtreC:function(products){
            return products.filter((product)=>{
                
                return product.color.match(this.color);
            });
            //this.test();
            
            },
            filtreN:function(products){
             return products.filter((product)=>{
                
                return product.name.match(this.names);
            });
           // this.test()
        },
       
    },
    watch : {
        products:function(){
            let total_price = 0;
            console.log('sjdso')
            for( let p of this.products){
                total_price = total_price + parseInt(p.price) * parseInt(p.qte)
            }
           this.total = total_price
        },
      
        reduce:function(){
           var x = this.product.price ;
            this.product.price = x -((x * this.reduc) / 100);
            
        }
    }
}
</script>