<template>
  <div>
    <el-form :model="ruleForm" status-icon :rules="rules" ref="loginForm">
      <el-form-item label="用户名" prop="username">
        <el-input type="text" v-model="ruleForm.username" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="密码" prop="password">
        <el-input type="password" v-model="ruleForm.password" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="确认密码" prop="checkPassword">
        <el-input type="password" v-model="ruleForm.checkPassword" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item>
        <!-- <el-button type="primary"  @click="submitForm('loginForm')">提交</el-button>
         <el-button @click="resetForm('loginForm')">重置</el-button>-->
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
  export default {
    data() {
      var validatePass = (rule, value, callback) => {
        if (this.ruleForm.checkPassword !== '') {
          this.$refs.ruleForm.validateField('checkPassword');
        }
        callback();
      };
      var validatePass2 = (rule, value, callback) => {
        if (value !== this.ruleForm.password) {
          callback(new Error('两次输入密码不一致!'));
        } else {
          callback();
        }
      };
      return {
        ruleForm: {
          password: '',
          checkPassword: ''
        },
        rules: {
          username: [{required: true, trigger: 'blur'}],
          password: [{required: true, trigger: 'blur', validator: validatePass}],
          checkPassword: [{required: true, trigger: 'blur', validator: validatePass2}]
        }
      };
    },
    methods: {
    }
  }
</script>
<style lang="scss">
</style>
