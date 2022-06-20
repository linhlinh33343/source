<template>
  <div>
     <div class="pricing-header " >
      <h2>User Management</h2>
      <p><router-link to="./user/create">Add new</router-link></p>
    </div>
    <div class="container">
        <div class="card-deck">
            <table class="table table-bordered">
              <thead>
                <tr>
                  <th scope="col">#</th>
                  <th scope="col">User name</th>
                  <th scope="col">Price</th>
                  <th scope="col">Handle</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <th scope="row">1</th>
                  <td>Mark</td>
                  <td>Otto</td>
                  <td>@mdo</td>
                </tr>
                <tr>
                  <th scope="row">2</th>
                  <td>Jacob</td>
                  <td>Thornton</td>
                  <td>@fat</td>
                </tr>
                <tr>
                  <th scope="row">3</th>
                  <td>Larry</td>
                  <td>the Bind</td>
                  <td>@twitter</td>
                </tr>
              </tbody>
            </table>
        </div>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style>

</style>