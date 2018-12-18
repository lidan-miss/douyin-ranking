<template>
  <div class="container">
    <div class="update-time">数据更新时间：2018/04/06 13:36</div>
    <div class="topic-details">
      <div class="topic-details-hd">
        <div class="item">
          <div class="text">
            <div class="btns">取消收藏</div>
            <div class="mark">#</div>
            <div class="title">谁的太阳花成精了</div>
            <p class="">该话题下共1.4W视频</p>
          </div>
        </div>
      </div>
      <div class="topic-details-bd">
        <div class="topic-title">
          话题7天数据
        </div>
        <div class="chart-area">
          <img src="/static/img/7.png" alt="" mode="widthFix">
        </div>
        <div class="topic-title">
          话题最热视频
        </div>
        <div class="topic-video">
          <div class="content">
            <div class="item">
              <div class="img"><img src="/static/img/8.jpg" alt="" mode="widthFix"></div>
              <div class="text">68.7W播放</div>
              <div class="tag">01</div>
            </div>
            <div class="item">
              <div class="img"><img src="/static/img/8.jpg" alt="" mode="widthFix"></div>
              <div class="text">68.7W播放</div>
              <div class="tag">02</div>
            </div>
            <div class="item">
              <div class="img"><img src="/static/img/8.jpg" alt="" mode="widthFix"></div>
              <div class="text">68.7W播放</div>
              <div class="tag">03</div>
            </div>
            <div class="item">
              <div class="img"><img src="/static/img/8.jpg" alt="" mode="widthFix"></div>
              <div class="text">68.7W播放</div>
              <div class="tag">04</div>
            </div>
            <div class="item">
              <div class="img"><img src="/static/img/8.jpg" alt="" mode="widthFix"></div>
              <div class="text">68.7W播放</div>
              <div class="tag">05</div>
            </div>
            <div class="item">
              <div class="img"><img src="/static/img/8.jpg" alt="" mode="widthFix"></div>
              <div class="text">68.7W播放</div>
              <div class="tag">06</div>
            </div>
          </div>
          <div class="more">
            加载更多
          </div>
        </div>
      </div>

    </div>
   
  </div>
</template>

<style lang="scss">
@import '@/common/scss/style.scss';

.container {
  .update-time{
    background:#24252a;
    height:25px;
    line-height: 25px;
    text-align: center;
    font-size:12px;
    color:#ffffff;
    border-bottom: 1px solid #32333c;
    opacity:0.6;
  }
  .topic-details{
    .topic-details-hd{
      padding: 0 15px;
      .item{
        border-bottom: 1px solid #32333c;
        padding: 12px 0;
        display: flex;
        .img{
          width: 80px;
          height: 80px;
          margin-right: 15px;
          img{
            width: 80px;
            height: 80px;
            border: 1px solid #fff;
            border-radius: 4px;
          }
        }
        .text{
          text-align: center;
          flex: 1;
          font-size: 12px;
          color:#ffffff;
          padding: 8px 0;
          position: relative;
          .mark{ color: #FACD13; font-size: 32px; margin-bottom: 10px;}
          .title{font-size:16px; padding-bottom:10px;}
          p{opacity:0.6; padding-bottom: 8px;}
          .btns{
          position: absolute;
          right: 0;
          top: 0;
          padding:0 5px;
          height:24px;
          line-height: 24px;
          background:#FACD13;
          border-radius:4px;
          font-size: 12px;
          &::before{
            background: url(http://resource.xiguaji.com/images/dsp/stars.png) no-repeat center center;
            background-size: 24rpx 24rpx;
            width: 24rpx;
            height: 24rpx;
            content: "";
            display: inline-block;
            margin-right: 4rpx;
            vertical-align: middle;
            margin-top: -3px;
          }
          }
        }
      }
    }
    .topic-details-bd{
      .topic-title{
        border-bottom: 1px solid #32333c;
        padding: 15px 0 10px;
        margin: 0 15px;
        font-size:12px;
        color:#ffffff;
      }
      .chart-area{
        min-height: 220px;
        padding: 0 15px;
        img{ width: 350px;
        height: 210px;}
      }
      .topic-video{
        .content {
          padding-top: 15px;
          flex-wrap: wrap;
          justify-content: space-between;
          .item {
            display: inline-block;
            position: relative;
            width: 33.33%;
            .img {
              img {
                width: 100%;
                height: 166px;
                margin-bottom: -3px;
              }
            }
            .text {
              font-size: 12px;
              color: #fff;
              background:rgba(0,0,0,0.5);
              position: absolute;
              left: 0;
              bottom: 0;
              right: 0;
              width: 100%;
              height: 25px;
              line-height: 25px;
               padding: 0 5px; 
            }
            .tag {
              background: #facd13;
              width: 42px;
              height: 18px;
              position: absolute;
              top: 0;
              left: 0;
              border-bottom-right-radius: 4px;
              font-size: 12px;
              color: #fff;
              line-height: 18px;
              padding-left: 14px;
              box-sizing: border-box;
              font-size: 16px; 
              
            }

          }
        }
        .more{
          color:#999999;
          text-align: center;
          margin-top: 5px;
          margin-bottom: 20px;
          font-size: 14px;
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
import TopicList from '@/common/components/topic/list'

export default {
  data() {
    return {

    };
  },

  components: {
    TopicList,
    VideoWidget
  },

  methods: {

  },

  created() {

  },
  mounted() {

  },
};
</script>
