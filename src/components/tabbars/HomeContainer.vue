<template>
  <div>
    
    <ul class="mui-table-view mui-grid-view mui-grid-9">
      <li class="mui-table-view-cell mui-media mui-col-xs-6 mui-col-sm-6"><router-link to="/home/newslist">
              <img src="../../images/menu1.png" alt="">
              <div class="mui-media-body">企业信息</div></router-link></li>
      <li class="mui-table-view-cell mui-media mui-col-xs-6 mui-col-sm-6"><router-link to="/home/photolist">
              <img src="../../images/menu2.png" alt="">
              <div class="mui-media-body">空间位置</div></router-link></li>
      <li class="mui-table-view-cell mui-media mui-col-xs-6 mui-col-sm-6"><router-link to="/home/goodslist">
              <img src="../../images/menu3.png" alt="">
              <div class="mui-media-body">生产经营</div></router-link></li>
      <li class="mui-table-view-cell mui-media mui-col-xs-6 mui-col-sm-6"><a href="#">
              <img src="../../images/menu4.png" alt="">
              <div class="mui-media-body">环保监督</div></a></li>
      <li class="mui-table-view-cell mui-media mui-col-xs-6 mui-col-sm-6"><a href="#">
              <img src="../../images/menu5.png" alt="">
              <div class="mui-media-body">污染排放</div></a></li>
  </ul>

  </div>
</template>

<script>
// 导入自己封装的轮播图子组件
import swiper from "../sub-components/Swiper.vue";

export default {
  data() {
    return {
      lunbotu: [] // 轮播图的数组
    };
  },
  created() {
    this.getlunbotu();
  },
  methods: {
    async getlunbotu() {
      // 获取轮播图的方法
      const { data } = await this.$http.get("/api/getlunbo");
      if (data.status === 0) this.lunbotu = data.message;
    }
  },
  components: {
    // 注册子组件
    swiper
  }
};
</script>

<style lang="scss" scoped>

ul{
  padding: 0 10rpx;
  border: 1px
}
.mui-grid-view {
  li {
    img {
      width: 60px;
      height: 60px;
    }
    div {
      font-size: 12px;
    }
  }
}
.mui-grid-view.mui-grid-9 {
  background-color: #fff;
  border: none;
}

.mui-grid-view.mui-grid-9 .mui-table-view-cell {
  border: none;
}

.mui-table-view.mui-grid-view .mui-table-view-cell .mui-media-body {
  font-size: 13px;
}
</style>
