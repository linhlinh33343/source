<template>
    <div class="product-info">
        <div class="pricing-header px-3 py-3 md-5 pb-md-4 nx-auto text-center">
            <h3 class="display-5">Product Infomation</h3>
            <router-link to="/product">Back</router-link>
        </div>
        <div class="container">
            <form @submit.prevent="save()">
                <div class="form-group row"> 
                    <label for="inputPassword" class="col-sm-3 col-form-label" >Product name</label>
                    <div class="col-sm-9">
                        <input  type="text" class="form-control" 
                        v-bind:class="{'is-invalid':error.name}" 
                        @blur=" validate()" 
                        v-model="product.name" 
                        @input="updateUserObj('name',$event)"
                        />
                        
                        <div class="invalid-feedback">{{error.name}}</div>
                    </div>
                </div>
                <div class="form-group row"> 
                    <label for="inputPassword" class="col-sm-3 col-form-label">Product price</label>
                    <div class="col-sm-9">
                        <input type="text" class="form-control" 
                        v-model="product.price"
                        v-bind:class="{'is-invalid':error.price}" 
                       
                        @input="updateUserObj('price',$event)"
                        />
                        <div class="invalid-feedback">{{error.price}}</div>
                    </div>
                </div>
                <div class="form-group row"> 
                    <label for="inputPassword" class="col-sm-3 col-form-label">Product description</label>
                    <div class="col-sm-9">
                        <textarea  rows="3" class="form-control" v-model="product.description"></textarea>
                    </div>
                </div>
                <div class="form-group row"> 
                    <label for="inputPassword" class="col-sm-3 col-form-label">Product description</label>
                    <div class="col-sm-9 text-left">
                        <button type="submit" class="btn btn-primary">Save</button> &nbsp;
                        <button type="reset" class="btn btn-danger" @click="cancel()">Cancel</button>
                    </div>
                </div>
                
            </form>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name:'ProductForm',
    
    data(){
        return {
            check :false,
            error:{
                id:'',
                name:'',
                price:'',
                description:'',
            },
            product:{
                id:'',
                name:'',
                price:'',
                description:'',
            }
        }
    },
    created(){
        let productId = this.$route.params.id;
      
        if(productId){
            this.getProduct(productId)
        }

    },
    methods:{
        validate(){
            let isValid = true;
            this.error={
                name:'',
                price:'',
                description:'',
            }
            if(!this.product.name){
                this.error.name='Product name is required'
                console.log("name");
                isValid= false;
            }
            if(!this.product.price){
                this.error.price='Product price is required'
                console.log('price');
                isValid= false;
            }
            // }else if(!this.isNumber(this.product.price)){
            //     this.error.price= 'Product price must be number'
            //     isValid= false;

            // }
            return isValid;
        },
        isNumber(value){
            return /^\d*$/.test(value)
        },
        save(){
            
            if(this.validate()){
                if(this.product.id){
                    axios.put(`http://localhost:8000/api/products/${this.product.id}`,this.product)
                        .then(res =>{
                            if(res.data.success){
                                this.$router.push({name:'product.list'})
                                console.log(this.product.id);
                                return
                            }
                                alert("Something went wrong")
                        });
                    return;
                }
                 axios.post("http://localhost:8000/api/products",this.product)
                  .then(res =>{
                    if(res.data.success){
                        this.$router.push({name:'product.list'})
                        return
                    }
                        alert("Something went wrong")
                  });
            }
        },
        updateUserObj(attribute,e){
           if(this.error[attribute]){
            this.error[attribute] =''
           } 
        
        },
        getProduct(productId){
            axios.get(`http://localhost:8000/api/products/${productId}`).then(res =>{
                this.product = res.data;
            })
        },
        cancel(){
                this.product.name='',
                this.product.price='',
                this.product.description=''
        }

        
    }
}
</script>

<style>

</style>