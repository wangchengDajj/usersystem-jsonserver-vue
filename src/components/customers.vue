<template>
  <div id="customers" class="container">
    <Alert v-if="alert" :message="alert"></Alert>
    <h1 class="page-header">用户管理系统</h1>
    <table class="table table-striped">
      <thead>
        <tr>
          <th>姓名</th>
          <th>电话</th>
          <th>邮箱</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(customer,index) in customers" :key="index">
          <td>{{customer.name,}}</td>
          <td>{{customer.phone}}</td>
          <td>{{customer.email}}</td>
          <td><router-link class="btn btn-type" :to="'/customer/'+customer.id">详情</router-link></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import Alert from "../components/alert";
export default {
  name: "customers",
  // 注册组件
  components: { Alert },
  data() {
    return {
      customers: [],
      alert:""
    };
  },
  created() {
    if(this.$route.query.alert){
      this.alert = this.$route.query.alert
    }
    this.fetchCustomers();
  },
  updated() {
    // this.fetchCustomers();
  },
  methods: {
    fetchCustomers() {
      this.$http.get("http://localhost:3000/users").then(function(response) {
        // console.log(response);
        this.customers = response.body;
      });
    }
  }
};
</script>

<style scoped>
</style>
