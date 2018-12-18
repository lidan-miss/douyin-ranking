<template>
  <div class="item" @click="viewDetail(1)">
     <div class="index index1">01</div><!--前面3名后面加样式名index1、index2、index3，从第四名开始就只要index就行了-->
     <div class="name"><span>#</span>做一天百分之一</div><!--收藏话题里面没有排名的话要加一个样式名name1，class="name name1"-->
     <div class="video-content">1.4W视频</div>
  </div>
</template>

<style lang="scss">
.topic-list{
  .item{
    display: flex;
    border-bottom: 1px solid #32333c;
    padding: 12px 0;
    height: 25px;
    line-height: 25px;
    color: #fff;
    font-size: 12px;
    .index{
      width: 50px;
      color: #fff;
      font-size: 12px;
      font-style: italic;
      text-align: center;
      &.index1, &.index2, &.index3{
      font-size:18px;
      color:#facd13;
      font-weight: bold;
      }
    }
    .name{
      flex: 1;
      color: #fff;
      font-size: 15px;
      span{ color: #FACD13; margin:0 5px;}
    }
    .name1{
      span{ color: #FACD13; margin:0 5px 0 15px;}
    }
    .video-content{
      width:80px;
      font-size: 12px;
      color:#fff;
      text-align: right;
      padding-right: 15px;
    }         
  }
}
</style>

<script>
export default {
    methods: {
      viewDetail(id){
        wx.navigateTo({
          url: `/pages/topic_details/main?id=${id}`
        })
      }
    }
}
</script>