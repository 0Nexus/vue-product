<template>
    <nav class="navbar navbar-dark bg-dark">
        <form action="" class="form-inline">
            <select name="color" id="color" aria-placeholder="color">
                <option value="Red" class="text-danger">Red</option>
                <option value="White" class="text-white-50">White</option>
                <option value="Yellow" class="text-warning">Yellow</option>
                <option value="Green" class="text-success">Green</option>
                <option value="Blue" class="text-primary">Blue</option>
                <option value="Black" class="text-dark">Black</option>
            </select>
            <input type="number" name="reduc" id="reduc" placeholder="%">
            <input type="text" name="name" id="name">
        </form>
    </nav>
</template>
<script>
export default {
    data(){

        return {
        products:[],
        color:''
    }},
    computed: {
        filtreC:function(){
            return this.product.filter((product)=>{
                return product.color.match(this.color);
            });
        }
    }
}
</script>