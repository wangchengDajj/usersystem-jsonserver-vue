<template>
  <div class="add container">
    <h1 class="page-header">添加用户</h1>
    <form @submit="addCustomer">
      <div class="well">
        <h4>用户信息</h4>
        <div class="form-group">
          <label>姓名</label>
          <input type="text" v-model="customer.name" class="form-control" placeholder="name">
        </div>
        <div class="form-group">
          <label>电话</label>
          <input type="text" v-model="customer.phone" class="form-control" placeholder="phone">
        </div>
        <div class="form-group">
          <label>邮箱</label>
          <input type="text" v-model="customer.email" class="form-control" placeholder="email">
        </div>
        <div class="form-group">
          <label>学历</label>
          <input
            type="text"
            v-model="customer.education"
            class="form-control"
            placeholder="education"
          >
        </div>
        <div class="form-group">
          <label>毕业学校</label>
          <input
            type="text"
            v-model="customer.graducationSchool"
            class="form-control"
            placeholder="graducationSchool"
          >
        </div>
        <div class="form-group">
          <label>职业</label>
          <input
            type="text"
            v-model="customer.profession"
            class="form-control"
            placeholder="profession"
          >
        </div>
        <div class="form-group">
          <label>个人简介</label>
          <!-- <input type="textarea" v-model="customer.profile" class="form-control" placeholder="profile">  -->
          <textarea v-model="customer.profile" class="form-control" rows="10" placeholder="profile"></textarea>
        </div>
        <button type="submit" class="btn btn-primary">添加</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "add",
  data() {
    return {
      customer: {}
    };
  },
  methods: {
    addCustomer(e) {
      //   console.log("123")
      if (!this.customer.name || !this.customer.phone || !this.customer.email) {
        console.log("请添加对应的信息！");
      } else {
        let newCustomer = {
          name: this.customer.name,
          phone: this.customer.phone,
          email: this.customer.email,
          education: this.customer.education,
          graduationSchool: this.customer.graduationSchool,
          profession: this.customer.profession,
          profile: this.customer.profile
        };
        this.$http
          .post("http://localhost:3000/users", newCustomer)
          .then(function(response) {
            //   console.log(111,response)
            
            this.$router.push({path:"/",query:{alert:"用户信息添加成功!!!"}})
          });
      }
      e.preventDefault();
    }
  }
};
</script>

<style scoped>
</style>
