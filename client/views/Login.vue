<template>
      <div class="mark_box">
      <nprogress-container></nprogress-container>
      <div class="modal-cards">
        <section class="modal-card-bodys">
          <slot>
             <div class="box">
                <article class="middle">
                   <h4 class="subtitle is-1">
                      <strong>后台管理系统</strong>
                   </h4>
                   <div class="middle_sub">
                   <div class="control is-horizontal">
                      <p class="control">
                         <input type="text" class="input" placeholder="请输入登录名" v-model="loginMessage.username"/>
                      </p>
                   </div>
                   <div class="control is-horizontal">
                      <p class="control">
                         <input type="password" class="input" placeholder="请输入密码" v-model="loginMessage.password"/>
                      </p>
                   </div>
                   <div class="control is-horizontal">
                       <div class="control">
                          <input type="text" class="input" placeholder="请输入验证码"/>
                       </div>
                       <div class="control">
                          <img src="" class="imgs"/>
                       </div>
                   </div>
                  <div class="control is-horizontal">
                     <div class="control textAlign">
                        <button class="button is-primary is-medium" @click="logining">登录</button>
                     </div>
                  </div>
                  </div>
                </article>
              </div>
          </slot>
        </section>
      </div>
</template>
<script>
import NprogressContainer from 'vue-nprogress/src/NprogressContainer'
export default {
  components: {
    NprogressContainer
  },
  data () {
    return {
      confirm: '',
      show: true,
      loginMessage: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    deactive () {
      // this.$emit('cancel')
    },
    logining () {
      if (this.loginMessage.username === '' || this.loginMessage.password === '') {
        window.alert('请输入登录名或密码')
      } else if (this.loginMessage.username === 'admin' && this.loginMessage.password !== '123456') {
        window.alert('你输入的密码不正确 请重新输入')
      } else if (this.loginMessage.username !== 'admin' && this.loginMessage.password === '123456') {
        window.alert('你输入的登录名不正确 请重新输入')
      } else if (this.loginMessage.username === 'admin' && this.loginMessage.password === '123456') {
        window.sessionStorage.setItem('user', JSON.stringify('true'))
        window.alert('点击哈')
        this.$router.push({ path: '/default' })
      }
    }
  }
}
</script>
<style>
  .radio{
    padding-left:50px;
  }
  .middle{
    text-align:center;
  }
  .middle_sub{
    text-align:center;
    padding:0 140px;
  }
  .textAlign{
    justify-content: center;
  }
  .mark_box{
    width:100%;
    height:100%;
    position:absolute;
    left:0;
    top:0;
    background-color:#30d1b2;
  }
  .modal-card-bodys{
    /* background-color: white; */
    -ms-flex-positive: 1;
    flex-grow: 1;
    -ms-flex-negative: 1;
    flex-shrink: 1;
    overflow: auto;
    padding: 20px;
  }
  .modal-cards{
    width:640px;
    margin:0 auto;
  }
</style>










