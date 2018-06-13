<template>
    <div class="list">
      <!-- 上拉刷新 -->
      <van-pull-refresh v-model="isLoading" @refresh="onRefresh">
        <p>刷新次数: {{ count }}</p>

      <!-- 无限加载 -->
        <van-list
          v-model="loading"
          :finished="finished"
          @load="onLoad"
        >
          <van-cell v-for="item in list" :key="item" :title="item + ''" />
        </van-list>
        </van-pull-refresh>
    </div>
</template>

<script>
import {
  List,
  Tag,
  Col,
  Button,
  Icon,
  Field,
  Cell,
  CellGroup,
  Toast,
  PullRefresh  
} from 'vant';

export default {
  components: {
    [List.name]: List,
    [Tag.name]: Tag,
    [Col.name]: Col,
    [Icon.name]: Icon,
    [Field.name]: Field,
    [Button.name]: Button,
    [Cell.name]: Cell,
    [CellGroup.name]: CellGroup,
    [PullRefresh.name]: PullRefresh
  },

  data() {
    return {
      count: 0,
      isLoading: false,
      list: [],
      loading: false,
      finished: false
    };
  },

  methods: {
    onRefresh() {
      setTimeout(() => {
        this.$toast('刷新成功');
        this.isLoading = false;
        this.count++;
      }, 500);
    },
    onLoad() {
      setTimeout(() => {
        for (let i = 0; i < 10; i++) {
          this.list.push(this.list.length + 1);
        }
        this.loading = false;

        if (this.list.length >= 40) {
          this.finished = true;
          Toast('没有更多数据了哦~');
        }
      }, 500);
    }
  }
};
</script>

<style lang="less">

</style>