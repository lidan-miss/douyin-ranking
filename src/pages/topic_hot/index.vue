<template>
  <div class="container">
    <div class="hot-subNav">
      <ul>
        <li class="active"><span>最新</span></li>
        <li><span>最热</span></li>
        <li><span>黑马</span></li>
      </ul>
    </div>
    <div class="content">
      <TopicList />
    </div>
  </div>
</template>

<style lang="scss">
@import '@/common/scss/style.scss';

.container {
  .hot-subNav{
    height: 40px;
    background: #1d1e20;
    ul{
      padding: 0 20px;
      display: flex;
      text-align: center;
      li{
        flex: 1;
        color: #A1A2A2;
        font-size: 12px;
        line-height: 40px;
        display: inline-block;
        &:first-child{ text-align: left;}
        &:last-child{ text-align: right;}
        span{
          padding: 14px 40px;
        } 
        &.active span{ color: #FACD13;}
      }
    }
  }
}

</style>

<script>
import SYSTEM from '@/utils/system';
import TopicList from '@/common/components/topic/list'

export default {
 

  components: {
    TopicList
  },

  methods: {
    switchCategory(id){
      this.currentCategory = id;
    },
    showMoreCategories(){
      this.showAllCategories = !this.showAllCategories;
    }
  },

  created() {
    if(SYSTEM.WIN_WIDTH < 360){
      this.maxCategoriesNum = 10;
    }
  },
  mounted() {

  },
};
</script>
