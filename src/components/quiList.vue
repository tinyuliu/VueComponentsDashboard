<template>
  <div class="qui-list">
    <span class="list-tips">{{tipsText}}</span>
    <!-- 生成動態組件 -->
    <component :is="currentView" @btnClickEvent="clickEvent" :msg=msg class="small" keep-alive></component>
  </div>
</template>
<script>
import quiButton from '../components/quiButton.vue'
import quiArrow from '../components/quiArrow.vue'
export default {
  props: {
    msg: {
      default: 'Download'
    },
    tipsText: {
      default: 'Default Text'
    },
    currentView: {
      default: 'qui-btn'
    },
    btnClickEvent: {
      type: Function,
      default: function () {
        alert(this.msg + 'I am default event')
      }
    }
  },
  components: {
    'qui-btn': quiButton,
    'qui-arrow': quiArrow
  },
  methods: {
    clickEvent: function () {
      this.btnClickEvent()
      this.$emit('btnClickEvent')
    }
  }
}
</script>
<style scoped>
.qui-list{
    padding: 10px 0;
    margin-left: 10px;
    overflow: hidden;
    border-bottom: 1px solid #e0e0e0;
    vertical-align: middle;
    display: flex;
    justify-content:center;
    align-items:Center;
    min-height: 30px;
  }
  .qui-list .qui-btn{
    float: right;
    margin-right: 10px;

  }
  .qui-list .list-tips{
    padding: 0 5px;
    color: #00A0D8;
    float: left;
    vertical-align: middle;
    flex:1;
    text-align: left;
    font-size: 14px;
  }
</style>
