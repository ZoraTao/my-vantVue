<template>
    <div class="login">
        <van-cell-group>
            <van-field
                v-model="username"
                label="用户名"
                icon="clear"
                placeholder="请输入用户名"
                required
                @click-icon="username = ''"
            />

            <van-field
                v-model="password"
                type="password"
                label="密码"
                placeholder="请输入密码"
                required
            />
        </van-cell-group>
        <van-button class="mgt20" type="primary" size="large" @click="login">登录</van-button>
    </div>
</template>

<script>
import {
  Tag,
  Col,
  Button,
  Icon,
  Field,
  CellGroup,
  Toast
} from 'vant';

export default {
  components: {
    [Tag.name]: Tag,
    [Col.name]: Col,
    [Icon.name]: Icon,
    [Field.name]: Field,
    [Button.name]: Button,
    [CellGroup.name]: CellGroup,
  },

  data() {
    return {
      username: '',
      password: ''
    };
  },

  methods: {
    login() {
      this.$router.push('goods');
    },
    
    sorry() {
      Toast('请输入正确用户名和密码！');
    }
  }
};
</script>

<style lang="less">
.login {
 .login-btn{
   margin-top: 20px;
 }
}
</style>