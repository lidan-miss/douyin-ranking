<template>
  <div class="container">
    <div class="tabNav">
      <ul>
        <li :class="{active: currentTab === 0}" @click="switchTab(0)"><span>热门视频</span></li>
        <li :class="{active: currentTab === 1}" @click="switchTab(1)"><span>热门音乐</span></li>
        <li :class="{active: currentTab === 2}" @click="switchTab(2)"><span>热门话题</span></li>
      </ul>
    </div>

    <div v-show="currentTab === 0">
      <div class="navigation">
        <ul class="plist" :class="{showAll: showAllCategories}">
          <li class="item" :class="{active: currentCategory === null}" @click="switchCategory(null)">全部</li>
          <li class="item" :class="{active: currentCategory === item.id, hidden: index >= maxCategoriesNum }" v-for="(item, index) in videoCategories" :key="index" @click="switchCategory(item.id)">{{item.name}}</li>
          <li class="item more" @click="showMoreCategories"></li>
        </ul>
      </div>
      <div class="content">
        <i-spin size="large" i-class="loading" v-if="showLoading"></i-spin>
        <VideoList :listData="videoList" :total="total" />
        <i-load-more :tip="loadMoreText" :loading="!isEnd" v-if="showLoadMore" />
      </div>
    </div>
    <div v-show="currentTab === 1">
      232
    </div>
    <div v-show="currentTab === 2">
      25235xxx
    </div>

  </div>
</template>

<style lang="scss">
@import '@/common/scss/style.scss';

.container {
  .loading{
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, 0)
  }
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
  .navigation{
    background:#1d1e20;
    padding: 12px;
    font-size: 14px;
    .plist{
      .item{
        text-align: center;
        vertical-align: middle;
        width: 14.28%;
        height: 20px;
        line-height: 20px;
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
import SYSTEM from '@/utils/system';
import VideoList from '@/common/components/video/list'
import config from '@/config'
import request from '@/utils/request'
import { GET_VIDEO_CATEGORIES } from '@/store/mutation-types'
import { mapState } from 'vuex'

const { services } = config;

export default {
  data() {
    return {
      currentTab: 0,
      videoList: [],
      page: 1,
      totalPage: 1,
      total: 0,
      loadMoreText: '正在加载..',
      isEnd: false,
      showLoadMore: false,
      showLoading: true,
      currentCategory: null,
      showAllCategories: false,
      maxCategoriesNum: 5,
      filters: {
        type: '', //分类
        time: 1, //1: 24小时 2:7天
        sort: '' //排序
      }
    };
  },

  computed: {
    ...mapState({
      videoCategories: state => state.videoCategories
    })
  },

  components: {
    VideoList
  },

  methods: {
    switchTab(i){
      this.currentTab = i
    },
    switchCategory(id){
      this.currentCategory = id;
      this.resetList({type: id})
    },
    showMoreCategories(){
      this.showAllCategories = !this.showAllCategories;
    },
    async getList(){
      let params = Object.assign({}, {page: this.page}, this.filters);
      let res = await request.get(services.videoList, params);
      wx.stopPullDownRefresh();
      this.showLoading = false;
      this.showLoadMore = false;
      if(res.result == 'success'){
        let data = res.data;
        if(this.page == 1){
          this.totalPage = data.totalPage;
        }
        this.page++;
        this.videoList = this.videoList.concat(res.data.listData);
        this.total = res.data.total;
      }
    },
    resetList(params){
      this.page = 1;
      this.videoList = [];
      console.log(this.videoList)
      this.showLoading = true;
      if(params){
        this.filters = Object.assign(this.filters, params);
      }
      this.getList();
    },
  },

  created() {
    if(SYSTEM.WIN_WIDTH < 360){
      this.maxCategoriesNum = 4;
    }

    this.$bus.$on('filter', param => {
      this.resetList(param)
    })

  },
  async onLoad() {
    this.$store.dispatch(GET_VIDEO_CATEGORIES)
    this.getList();
  },

  onReachBottom() {
    if(this.page <= this.totalPage){
      this.showLoadMore = true;
      this.getList();
    } else{
      this.showLoadMore = true;
      this.isEnd = true;
      this.loadMoreText = '没有更多了';
    }
  },
  onPullDownRefresh(){
    this.resetList()
  }
};
</script>
