<template lang="html">
  <div class="AssessmentProgress">
    <ul class="AssessmentProgress__list">
      <li v-for="node in nodeList" :key="node.id" :class="{ complete: node.answer && !node.active, active: node.active }" class="AssessmentProgress__list-item">
        <span v-if="node.answer && !node.active">✔</span>
        <span v-else>{{ (node.id+1) }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name:'Progress',
  props: {
    nodeList: {
      type:Array,
      default: null
    }
  },
  updated: function () {
    console.log(this.nodeList)
  }
}
</script>

<style lang="scss" scoped>
@import 'theme/css/main.scss';
.AssessmentProgress{
  width:100%;
  display:flex;
  align-items:center;
  justify-content:center;
  padding:0;
  ul{
    display:flex;
    flex-flow: row nowrap;
    list-style: none;
    padding:0;
    li{
      background: transparent 1px;
      transition:all .2s ease-in-out;
      border-radius:50%;
      width:25px;
      height:25px;
      display:flex;
      align-items: center;
      justify-content: center;
      margin:0 15px;
      &.active{
        color:white;
        background:$color-primary;
      }
      &.complete{
        color:white;
        background:#CC7685;
      }
    }
  }
}
</style>
