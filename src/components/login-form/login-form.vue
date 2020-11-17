<template>
  <Form ref="loginForm" :model="form" :rules="rules" @keydown.enter.native="handleSubmit">
    <FormItem prop="userName">
      <Input v-model="form.userName" placeholder="Please input user name">
        <span slot="prepend">
          <Icon :size="16" type="ios-person"></Icon>
        </span>
      </Input>
    </FormItem>
    <FormItem prop="password">
      <Input type="password" v-model="form.password" placeholder="Please Input the Password">
        <span slot="prepend">
          <Icon :size="14" type="md-lock"></Icon>
        </span>
      </Input>
    </FormItem>
    <FormItem>
      <Button @click="handleSubmit" type="primary" long>Login</Button>
    </FormItem>
  </Form>
</template>
<script>
export default {
  name: 'LoginForm',
  props: {
    userNameRules: {
      type: Array,
      default: () => {
        return [
          { required: true, message: 'Username cannot be empty', trigger: 'blur' }
        ]
      }
    },
    passwordRules: {
      type: Array,
      default: () => {
        return [
          { required: true, message: 'Password cannot be empty', trigger: 'blur' }
        ]
      }
    }
  },
  data () {
    return {
      form: {
        userName: 'FMX_Juarez',
        password: ''
      }
    }
  },
  computed: {
    rules () {
      return {
        userName: this.userNameRules,
        password: this.passwordRules
      }
    }
  },
  methods: {
    handleSubmit () {
      this.$refs.loginForm.validate((valid) => {
        if (valid) {
          // if this.form.userName==''
          if (this.form.password == 'fmxhpe') {
            this.$Message.success('Login Sucessfully!')
            this.$emit('on-success-valid', {
              userName: this.form.userName,
              password: this.form.password
            })
          } else {
            this.$Message.error('Password incorrect!')
            this.$emit('on-failure')
            this.errors.push('Something went wrong, please refresh and try again.')
          }
        }
      })
    }
  }
}
</script>
