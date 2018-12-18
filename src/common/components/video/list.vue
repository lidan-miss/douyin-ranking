<template>
    <div class="video-list">
        <div class="head">
            <div class="title"><span class="title-number">{{total}}条</span></div>
            <!--<div class="switch-time">
              <ul>
                <li :class="{curent: currentType == 0}" @click="filter({time: 1}, 0)">24小时</li>
                <li :class="{curent: currentType == 1}" @click="filter({time: 2}, 1)">近7天</li>
              </ul>
            </div>-->
            <div class="sort sort-time" :class="{active: showSortTime === true}" @click="toggleSortTime">24小时</div>
            <ul v-if="showSortTime" class="sort-popup sort-time-popup">
              <li class="active">24小时</li>
              <li>7天</li>
            </ul>
            <div class="sort" :class="{active: showSort === true}" @click="toggleSort">综合排序</div>
            <ul v-if="showSort" class="sort-popup">
              <li class="active">综合排序</li>
              <li>最多点赞</li>
            </ul>
        </div>
        <div class="list">
            <Item v-for="item in listData" :key="item.id" :itemData="item" />
        </div>
    </div>
</template>

<style lang="scss">
.video-list{
    background: #24252a;
    padding:0 15px;
    .head{ 
        height: 15px;
        padding: 12px 0;
        border-bottom: 1px solid #32333c;
        color: #fff;
        font-size:12px;
        color:#888888;
        display: flex;
        position: relative;
        .title{ 
          font-size: 16px;
          line-height: 27px;
          color:#ffffff;
          flex: 1;}
        .title-number{
          font-size:12px;
          color:#888888;
          }
        .switch-time{
          flex: 1;
          ul{ 
            background:#32333c;
            border-radius:16px;
            width:108px;
            height:23px;
            font-size:11px;
            color:#ffffff;
            display: block;
            padding:2px 3px; }
          li{ text-align: center;
            float: left;
            width: 50%;
            line-height: 23px;
            }
          .curent{
            background:#24252a;
            border-radius:32px;
            width:52px;
            line-height: 23px;
            display: inline-block;
            text-align:center;
          }
        }
        .sort{
          width:60px;
          margin:0 0 0 10px;
          position: relative;
          line-height: 15px;
          text-align: right;
          padding-right: 20px;
          box-sizing: content-box;
          border-left: 1px solid #32333c;
          &.active{
            &::after{
              transform: rotate(180deg)
            }
          }
          &::after{ 
            display: block;
            content: ' ';
            position: absolute;
            top: 5px;
            right:0;
            background: url(../../assets/img/arrow-down.png) center right no-repeat;
            background-size: 11px 6px;
            width: 11px;
            height: 6px;
            transition: all .2s; 
          }

        }
        .sort-popup{
          position: absolute;
          top: 85rpx;
          right: -10rpx;
          width: 100px;
          border: 1px solid #32333c;
          background:#24252a;
          border-radius: 4px;
          li{ 
            border-bottom: 1px solid #32333c; 
            text-align: center;
            line-height: 30px;
            &.active{
              color: #fff !important;
            }
          }
          &::before{
            content:"";
            width:0;
            height:0;
            position:absolute;
            left:46px;
            top:-6px;
            border-left:solid 7px transparent;
            border-bottom:solid 7px #32333c;
            border-right:solid 7px transparent;
          }
          &:after{
            content:"";
            width:0;
            height:0;
            position:absolute;
            left:47px;
            top:-5px;
            border-left:solid 6px transparent;
            border-bottom:solid 6px #24252a;
            border-right:solid 6px transparent;
          }
        }
        .sort-time{
         border-left:none;
        }
        .sort-time-popup{
          top: 85rpx;
          right: 160rpx;
          width: 100px;
        }
    }
}
</style>

<script>
import Item from "./item";
export default {
  data(){
    return {
      currentType: 0,
      showSort: false,
      showSortTime: false
    }
  },
  props: {
    listData: {
      type: Array
    },
    total: {
      type: Number
    }
  },
  components: {
    Item
  },
  methods: {
    filter(param, tabIndex){
      this.currentType = tabIndex;
      this.$bus.$emit('filter', param);
    },
    toggleSort(){
      this.showSort = !this.showSort;
      if(this.showSort){
        this.showSortTime = false
      }
    },
    toggleSortTime(){
      this.showSortTime = !this.showSortTime;
      if(this.showSortTime){
        this.showSort = false
      }
    }
    
  }
};
</script>