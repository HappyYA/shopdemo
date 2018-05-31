<template>
  <div>
    <div class="app-header">
      <div class="app-header-con">
        <div class="logo">
          <a href="#">
            <img  class="logo-img" src="./../assets/logo.png" alt="logo">
          </a>
        </div>
        <div class="app-reg">
          <ul class="nav-list">
            <li v-if='userName!==""'>{{userName}}</li>
            <li v-if='userName===""' @click="showLog">登录</li>
            <li class="nav-line">|</li>
            <li v-if='userName!==""'>退出</li>
            <li v-if='userName===""' @click="showReg">注册</li>
            <li class="nav-line">|</li>
            <li @click="showAbout">关于</li>
          </ul>
        </div>
      </div>
    </div>
    <div class="app-cont">
      <keep-alive>
        <router-view></router-view>
      </keep-alive>
    </div>
    <div class="app-footet">
      <p>© 2018 lijinya MIT</p>
    </div>
    <my-dialog :isShow = "isShowAbout" @on-close = 'closeDialog("isShowAbout")'>
      <p>本报告在调研数据的基础上，采用定性与定量相结合的方式深入分析了专车市场发展的驱动因素与阻碍因素、专车市场背后的产业格局、专车企业的竞争格局、用户对专车市场的依赖程度、专车对其他交通工具运力的补充效应等，通过这五个章节的研究反映专车市场的发展态势和面临的问题。报告力求客观、深入、准确地反映中国专车市场发展情况，为政府、企事业单位和社会各界提供决策依据。 </p>
    </my-dialog>  
    <my-dialog :isShow = 'isShowReg' @on-close = 'closeDialog("isShowReg")'>
      <reg-form></reg-form>
    </my-dialog>
    <my-dialog :isShow = 'isShowLog' @on-close = 'closeDialog("isShowLog")'>
      <log-form></log-form>
    </my-dialog>
  </div>
</template>

<script>
import MyDialog from './base/dialog';
import LogForm from './logForm';
import RegForm from './regForm';
export default {
  name: "layout",
  data() {
    return {
      isShowAbout: false,
      isShowLog:true,
      isShowReg:false,
      userName:''
    };
  },
  components: {
    MyDialog,
    LogForm,
    RegForm
  },
  methods:{
    closeDialog(attr){
      this[attr]=false;
    },
    showAbout(){
      this.isShowAbout=true
    },
    showLog(){
      this.isShowLog=true
    },
    showReg(){
      this.isShowReg=true
    }
  }
};
</script>

<style lang='less'>
/* http://meyerweb.com/eric/tools/css/reset/ 
   v2.0 | 20110126
   License: none (public domain)
*/

html,
body,
div,
span,
applet,
object,
iframe,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
pre,
a,
abbr,
acronym,
address,
big,
cite,
code,
del,
dfn,
em,
img,
ins,
kbd,
q,
s,
samp,
small,
strike,
strong,
sub,
sup,
tt,
var,
b,
u,
i,
center,
dl,
dt,
dd,
ol,
ul,
li,
fieldset,
form,
label,
legend,
table,
caption,
tbody,
tfoot,
thead,
tr,
th,
td,
article,
aside,
canvas,
details,
embed,
figure,
figcaption,
footer,
header,
hgroup,
menu,
nav,
output,
ruby,
section,
summary,
time,
mark,
audio,
video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
menu,
nav,
section {
  display: block;
}
body {
  line-height: 1;
}
ol,
ul {
  list-style: none;
}
blockquote,
q {
  quotes: none;
}
blockquote:before,
blockquote:after,
q:before,
q:after {
  content: "";
  content: none;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
a {
  color: inherit;
  text-decoration: none;
}
body {
  background: #f0f2f5;
  font-family: "Helvetica Neue", Helvetica, Arial, "Hiragino Sans GB",
    "Hiragino Sans GB W3", "Microsoft YaHei UI", "Microsoft YaHei",
    "WenQuanYi Micro Hei", sans-serif;
  font-size: 14px;
  color: #444;
}
// 头部样式
.app-header {
  width: 100%;
  background-color: #363636;
  height: 90px;
  color: #b2b2b2;
  line-height: 90px;
  .app-header-con{
    width: 1200px;
    margin: 0 auto;
    .logo{
      float: left;
      height: 0;
      .logo-img{
        width: 50px;
        margin-top: 20px;
      }
    }
    .app-reg{
      float: right;
      .nav-list{
        li{
          float: left;
          cursor:pointer;
          &.nav-line{
            padding: 0 10px;
          }
        }
      }
    }
  }
}
// 底部样式
.app-footet{
  height: 90px;
  line-height: 90px;
  text-align: center;
  background-color: #e3e4e8;
  width: 100%;
}
</style>