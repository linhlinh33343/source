<template>
  <div>
     <div class="pricing-header " >
      <h2>Product Management</h2>
      <p><router-link to="./product/create">Add new</router-link></p>
    </div>
    <div class="container">
        <div class="card-deck">
            <table class="table table-bordered">
              <thead>
                <tr>
                  <th scope="col">Id</th>
                  <th scope="col">Produc name</th>
                  <th scope="col">Price</th>
                  <th scope="col">Handle</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(product,index) in products" :key="index">
                  <th scope="row">{{product.id}}</th>
                  <td>{{product.name}}</td>
                  <td>{{product.price}}</td>
                  <td>
                    <router-link :to="{name:'product.edit',params:{id:product.id}}">
                      <button class="btn btn-primary " style="margin-right:10px">Edit</button>
                    </router-link>
                    <button class="btn btn-danger" @click="onDelete(product.id)">Delete</button>
                  </td>
                </tr>
              
              </tbody>
            </table>
        </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
    name:'ProductList',
    data(){
      return {
        products:[],
      }
    },
    created(){
      this.getAll();
    },
    methods:{
      getAll(){
        axios.get("http://localhost:8000/api/products").then(res=>{
          this.products = res.data
        })
      },
      onDelete(productId){
          this.$swal.fire({
            title: 'Do you want to delete?',
            showDenyButton: false,
            showCancelButton: true,
            confirmButtonText: 'Ok',
            denyButtonText: `Don't save`,
          }).then((result) => {
            /* Read more about isConfirmed, isDenied below */
            if (result.isConfirmed) {
              
              axios.delete(`http://localhost:8000/api/products/${productId}`).then(res=>{
                if(res.data.success){
                  this.$swal.fire('Saved','','success')
                  this.getAll()
                }
              })
            }
           
          })
      }
    }

}
</script>

<style>

</style>