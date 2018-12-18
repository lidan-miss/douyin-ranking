<template>
  <div class="container">
    <div class="tabNav">
      <ul>
        <li :class="{active: currentTab === 0}" @click="switchTab(0)"><span>播主</span></li>
        <li :class="{active: currentTab === 1}" @click="switchTab(1)"><span>视频</span></li>
        <li :class="{active: currentTab === 2}" @click="switchTab(2)"><span>音乐</span></li>
        <li :class="{active: currentTab === 3}" @click="switchTab(2)"><span>话题</span></li>
      </ul>
    </div>
    
    <div v-show="currentTab === 0">
      <MusicList />
    </div>
    <div v-show="currentTab === 1"></div>
    <div v-show="currentTab === 2">
      <div class="container">
        <div class="collection-tip">收藏了6个视频</div>
        <div class="default-area">
          <h5>暂无收藏~</h5>
          <p>您可以在XX详情页中点击收藏按钮收藏喜欢</p>
        </div>
        <div class="authorization">
          <a href="#" class="btns">微信授权</a>
          <p>授权登录后查看您的收藏</p>
        </div>
        
        <MusicList />
      </div>
    </div>
    <div v-show="currentTab === 3"></div>
  </div>
</template>

<style lang="scss">
@import '@/common/scss/style.scss';

.container {
   .tabNav{
    height: 47px;
    background: #161617;
    ul{
      padding: 0 20px;
      display: flex;
      text-align: center;
      li{
        flex: 1;
        color: #A1A2A2;
        font-size: 14px;
        line-height: 44px;
        display: inline-block;
        &:first-child{ text-align: left;}
        &:last-child{ text-align: right;}
        span{
          padding: 14px 15px;
        } 
        &.active span{ color: #FACD13; border-bottom: 3px solid #FACD13; box-sizing: border-box;}
      }
    }
  }
  .authorization{
    color: #fff;
    font-size: 14px;
    text-align: center;
    padding: 35px 30px;
    border-radius: 4px;
    .btns{width:90px;
    text-align: center;
    height:32px;
    line-height: 32px;
    font-size: 14px;
    background: #FACD13;
    margin:0 auto 15px;
    }
  }
  .collection-tip{
    background:#24252a;
    height:25px;
    line-height: 25px;
    text-align: center;
    font-size:12px;
    color:#ffffff;
    border-bottom: 1px solid #32333c;
    opacity:0.6;
  }
  .default-area{
    padding: 27px 20px;
    color: #fff;
    text-align: center;
    font-size: 12px;
    h5{
      font-size: 14px;
      margin-bottom: 10px;
    }
  }
  .navigation{
    background:#1d1e20;
    padding: 15px;
    font-size: 14px;
    .plist{
      .item{
        text-align: center;
        vertical-align: middle;
        width: 14.28%;
        height: 30px;
        line-height: 30px;
        display: inline-block;
        color:#a1a2a2;
        &.active{
          color:#facd13;
        }
        &.more{
          background: url(../../common/assets/img/arrow-down.png) center center no-repeat;
          background-size: 14px 8px;
          display: inline-block !important;
          transition: all .2s;
        }
        &.hidden{
          display: none;
        }
      }

      &.showAll{
        .item{
          &.hidden{
            display: inline-block;
          }
          &.more{
            transform:rotate(180deg)
          }
        }
      }
    }
  }
}

@media all and (max-width: 359px){
  .container .navigation .plist .item{
    width: 16.66%;
  }
}
</style>

<script>
import MusicList from '@/common/components/music/list'

export default {
  data() {
    return {
      currentTab: 2,
    };
  },

  components: {
    MusicList
  },

  methods: {
    switchTab(i){
      this.currentTab = i
    },
  },

  created() {

  },
  mounted() {

  },
};
</script>
