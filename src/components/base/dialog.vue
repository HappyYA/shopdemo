<template>
  <div>
    <div class="darlog-wrap" v-if='isShow'>
      <div class="dialog-cover" v-if='isShow' @click="closeMyself"></div>
      <transition name="slide">
        <div class="dialog-content" v-if='isShow'>
          <p class="dialog-close" @click='closeMyself'>X</p>
          <slot>空内容</slot>
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {
    closeMyself() {
      this.$emit('on-close');
    }
  },
  props:{
    isShow:{
      type:Boolean,
      default:false
    }
  }
};
</script>

<style lang=less scoped>
.darlog-wrap {
  position: fixed;
  left: 0;
  top: 0;
  bottom: 0;
  right: 0;
  .dialog-cover {
    position: absolute;
    width: 100%;
    height: 100%;
    background: #000;
    opacity: 0.3;
    z-index: 5;
  }
  .dialog-content{
      width: 50%;
      max-height: 50%;
      padding: 2%;
      left: 25%;
      top: 20%;
      background-color: #FFF;
      position: absolute;
      z-index: 10;
      .dialog-close{
        position: absolute;
        top: 5px;
        right: 5px;
        width: 20px;
        height: 20px;
        line-height: 20px;
        text-align:center;
        cursor:pointer;
        &:hover{
          color: #4fc08d;
        }
      }
    }
}
/* 动画 */
.slide-enter-active,.slide-leave-active{
  transition: all .3s ease;
}
.slide-enter{
  transform: translateY(-500px);
}
.slide-leave-active{
  transform: translateY(-500px);
}
</style>