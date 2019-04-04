<template>
  <div class="details container">
    <h1 class="page-header">{{customer.name}}
        <span class=pull-right>
            <router-link class="btn btn-primary" :to="'/edit/'+customer.id">编辑</router-link>
            <button class="btn btn-danger" @click="deleteCustomer(customer.id)">删除</button>
            <router-link class="btn btn-default" to="/">返回</router-link>
        </span>
    </h1>
    <ul class="list-group">
      <li class="list-group-item">
        <span class="glyphicon glyphicon-phone">&nbsp;{{customer.phone}}</span>
      </li>
      <li class="list-group-item">
        <span class="glyphicon glyphicon-envelope">&nbsp;{{customer.email}}</span>
      </li>
    </ul>
    <ul class="list-group">
        <li class="list-group-item">
        <span class="glyphicon glyphicon-th-large">&nbsp;{{customer.education}}</span>
      </li>
      <li class="list-group-item">
        <span class="glyphicon glyphicon-th-large">&nbsp;{{customer.graduationSchool}}</span>
      </li>
      <li class="list-group-item">
        <span class="glyphicon glyphicon-th-large">&nbsp;{{customer.profession}}</span>
      </li>
      <li class="list-group-item">
        <span class="glyphicon glyphicon-th-large">&nbsp;{{customer.profile}}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "customerdetails",
  data() {
    return {
      customer: ""
    };
  },
  created() {
    //   获取人员对应id
    this.fetchCustomers(this.$route.params.id);
  },
  methods: {
    fetchCustomers(id) {
      this.$http
        .get("http://localhost:3000/users/" + id)
        .then(function(response) {
          // console.log(response);
          this.customer = response.body;
        });
    }
  }
};
</script>

<style scoped>
</style>
