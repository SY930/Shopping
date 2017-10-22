<template>
  <div>
    <!--<MHeader title="个人主页"></MHeader>-->
    <div class="scroll">
      <div class="hea">
        <img src="../assets/bb.jpg" alt="">
        <p>userName</p>
        <a
          style="color:#fff;background-color: orangered;border-radius: 8px;font-size: 14px;line-height: 30px;border:1px solid #fff;"
          v-if="this.book.bb" type="button" @click.stop="removebb">退出登录</a>
        <router-link
          style="color:#fff;background-color: orangered;border-radius: 8px;font-size: 18px;line-height: 36px;border:1px solid #fff;"
          to="/login" v-if="!this.book.bb

">登录
        </router-link>

      </div>
      <ul class="list">
        <router-link to="/MyCar" tag="li">
          <i class="iconfont icon-dingdan"></i>全部订单
          <span>  > </span>
        </router-link>
        <li>
          <i style="color:red;font-size: 18px" class="iconfont icon-shoucang"></i>我的收藏
          <span>  > </span>
        </li>
        <li>
          <a style="color: black" href="https://auth.alipay.com/login/index.htm">
            <i style="color:dodgerblue;font-size: 18px" class="iconfont icon-zhifubao"></i>支付宝
          </a>
          <span>  > </span>
        </li>
        <li>
          <a style="color: black" href="http://www.kuaidi100.com/all/sf.shtml?from=openv"><i
            class="iconfont icon-wuliu-copy" style="font-size: 18px"></i>我的物流
          </a>
          <span>  > </span>
        </li>
        <li><i class="iconfont icon-kefu" style="font-size: 18px"></i>联系客服<span>  > </span></li>
      </ul>
    </div>
  </div>

</template>
<script>
  import MHeader from '../components/MHeader.vue'
  import axios from 'axios'

  export default {
    data() {
      return {
        book: {
          bb: ''
        }
      }
    },
    created() {
      this.bb

      ()
    },
    components: {MHeader},
    methods: {
      bb() {
        this.book.bb

          = Boolean(localStorage.getItem("code"));
      },
      removebb() {
//        localStorage.removeItem("code")
//        window.location.reload();
        axios.get('/api/user/signout').then(res => {
          console.log(res);
          localStorage.removeItem("code");
          window.location.reload();
        })
      }
    },
    computed: {},
    mounted() {
    }
  }
</script>
<style scoped>
  .scroll {
    position: absolute;
    top: 0;
  }

  .hea {
    width: 100%;
    background: url("../assets/aa.jpg") no-repeat center;
    background-size: cover;
    border-top: 1px solid gainsboro;
    padding: 30px 0;
  }

  .hea p {
    color: #fff;
    font-weight: bold;
    text-align: center;
    margin: 10px 0;
  }

  .hea img {
    display: block;
    margin: 0 auto;
    width: 100px;
    height: 100px;
    border: 3px solid #fff;
    border-radius: 50%;
  }

  .hea a {
    display: block;
    margin: 0 auto;
    width: 100px;
    border: 1px solid #999;
    list-style: none;
    text-align: center;
    font-size: 18px;
    font-weight: 300;
  }

  .list {
    width: 100%;
    margin-top: 30px;
    padding-left: 18px;
  }

  .list li {
    width: 100%;
    height: 40px;
    line-height: 40px;
    font-size: 15px;
    border-bottom: 1px solid #e5e5e5;
  }

  .list li i {
    display: inline-block;
    width: 15px;
    height: 15px;
    margin-right: 20px;
  }

  .list li span {
    float: right;
    margin-right: 18px;
    color: #9d9d9d;
  }

  a {
    text-decoration: none;
  }

</style>
