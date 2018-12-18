<template>
    <div class="topic-list">
        <div class="tip-overview">
          数据更新时间：2018/04/06 13:36
        </div>
        <div class="list">
            <Item />
        </div>
    </div>
</template>

<style lang="scss">
.topic-list{
  background: #24252a;
  .tip-overview{
    height:25px;
    line-height: 25px;
    background:rgba(36,37,42,1);
    text-align: center;
    font-size: 12px;
    color: #fff;
    border-bottom: 1px solid #32333c;
  }
}
</style>

<script>
import Item from "./item";
export default {
  data(){
    return {
      currentType: 0,
      showSort: false
    }
  },
  components: {
    Item
  },
  methods: {
    toggleSort(){
      this.showSort = !this.showSort;
    }
  }
};
</script>