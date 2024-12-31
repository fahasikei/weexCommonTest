<template>
  <div class="full-page">
    <list class="list-wrap" :show-scrollbar="false" :paging-enabled="true">
      <cell
        class="section"
        v-for="(item, index) in videoList"
        v-dynamic-monitoring="[videoList]"
        :key="index"
        :item="item"
        :index="index"
        @touchstart="onStart(index, item)"
        @appear="onAppear(event, index, item)"
        @disappear="onDisappear(event, index, item)"
      >
        <div
          :style="{ backgroundColor: item, height: fullHeight + 'px' }"
          class="item"
        ></div>
      </cell>
    </list>
    <!-- <list class="list-wrap">
      <cell class="list-cell" v-for="(item, index) in lists" :key="index">
        <text class="list-text" :index="index" :item="item" v-dynamic-monitoring="[lists]" @touchstart="onStart(item, index)">{{
          `${item}--${index}`
        }}</text>
      </cell>
    </list>
    <button class="btn" @click="addInfo">添加数据</button> -->
  </div>
</template>

<script>
import screenMixin from "@/mixin/screenMixin";

export default {
  mixins: [screenMixin],
  data() {
    return {
      videoList: [],
      lists: [
        "pretty",
        "large",
        "big",
        "small",
        "tall",
        "short",
        "long",
        "handsome",
        "plain",
        "quaint",
        "clean",
        "elegant",
        "easy",
        "angry",
        "crazy",
        "helpful",
        "mushy",
        "odd",
        "unsightly",
        "adorable",
        "important",
        "inexpensive",
        "cheap",
        "expensive",
        "fancy",
      ],
      itemList: [
        "red",
        "green",
        "blue",
        "yellow",
        "purple",
        "orange",
        "pink",
        "black",
        "white",
        "gray",
      ],
    };
  },
  created() {
    this.setScreen({
      isOpen: true,
      showStatusMsg: true,
      statusMsgColor: 0,
    });
    setTimeout(() => {
      this.getVideoList();
    }, 300);
  },
  methods: {
    onAppear(ext, item, index) {
      console.log("显示了", ext, item, index);
    },
    onDisappear(ext, item, index) {
      console.log("隐藏了", ext, item, index);
    },
    onStart(item, index) {
      console.log(`${item}---${index}`);
    },
    getVideoList() {
      this.videoList = [
        "red",
        "green",
        "blue",
        "yellow",
        "purple",
        "orange",
        "pink",
        "black",
        "white",
        "gray",
      ];
    },
    addInfo() {
      console.log("button anniu");
      this.lists.push(
        ...[
          "pretty",
          "large",
          "big",
          "small",
          "tall",
          "short",
          "long",
          "handsome",
          "plain",
          "quaint",
          "clean",
          "elegant",
          "easy",
          "angry",
          "crazy",
          "helpful",
          "mushy",
          "odd",
          "unsightly",
          "adorable",
          "important",
          "inexpensive",
          "cheap",
          "expensive",
          "fancy",
        ]
      );
    },
  },
};
</script>

<style scoped>
.list-wrap {
  width: 750px;
  flex: 1;
}
.list-cell {
  width: 750px;
  margin-bottom: 20px;
}
.list-text {
  width: 750px;
  height: 50px;
  background-color: red;
}
.btn {
  width: 500px;
  padding: 20px;
  margin: 20px auto 0;
  border-radius: 10px;
  color: #6d7dff;
  text-align: center;
  font-size: 32px;
  border-style: solid;
  border-color: #6d7dff;
  border-width: 1px;
  opacity: 1;
}
</style>
