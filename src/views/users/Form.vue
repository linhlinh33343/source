<template>
    <div class="product-info">
        <div class="pricing-header px-3 py-3 md-5 pb-md-4 nx-auto text-center">
            <h3 class="display-5">User Infomation</h3>
            <router-link to="/user">Back</router-link>
        </div>
        <div class="container">
            <form action="">
                <div class="form-group row"> 
                    <label for="inputPassword" class="col-sm-3 col-form-label">User name</label>
                    <div class="col-sm-9">
                        <input type="text" class="form-control">
                    </div>
                </div>
                <div class="form-group row"> 
                    <label for="inputPassword" class="col-sm-3 col-form-label">User price</label>
                    <div class="col-sm-9">
                        <input type="text" class="form-control">
                    </div>
                </div>
                <div class="form-group row"> 
                    <label for="inputPassword" class="col-sm-3 col-form-label">User description</label>
                    <div class="col-sm-9">
                        <textarea  rows="3" class="form-control"></textarea>
                    </div>
                </div>
                <div class="form-group row"> 
                    <label for="inputPassword" class="col-sm-3 col-form-label">User description</label>
                    <div class="col-sm-9 text-left">
                        <button type="submit" class="btn btn-primary">Save</button> &nbsp;
                        <button type="reset" class="btn btn-danger">Cancel</button>
                    </div>
                </div>
                
            </form>
        </div>
    </div>
</template>