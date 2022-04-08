<template>
    <div class="table">
        <table>
          <thead>
            <tr>
              <td>Nome</td>
              <td>Email</td>
              <td>CPF</td>
            </tr>
          </thead>
          <tbody>
            <tr v-for='(customers, index) in {customers}' :key='index'>
              <td >{{customers.customerFullName}}</td>
              <td >{{customers.customerEmail}}</td>
              <td >{{customers.customerCpf}}</td>         
              <td v-on:click='editDataCustomer(index)'>Edit</td>
              <td v-on:click='deleteCustomer(index)'>Delete</td>
            </tr>
          </tbody>
        </table>
      </div>
</template>

<script>

export default {
    name: "DashboardView",
};
</script>

<style scoped>

</style>