<template>
  <!--多肉植物详情-->
  <div class="middleheader">
    <div class="middleheader-center scorall">
      <div class="middlecenter">
        <div class="serch">
          <div class="inputandcion">
            <!-- <button class="sousuo" @click="serch">
              <div class="claer" />
            </button> -->
          </div>
        </div>
        <div class="button">
          <div v-if="items && items.length > 0">
            <li v-for="(tableData, i) in items" :key="tableData.name">
              <router-link :to="`/shopcenter/${type}`">
                <HomeAll :title="tableData.name" :des="tableData.email" :eal="tableData.url" :class="
  name === tableData.name || (i === 0 && !name)
    ? 'isactive'
    : undefined
                " />
              </router-link>
            </li>
          </div>
        </div>
      </div>
    </div>
    <!-- <DetailPage /> -->
  </div>
</template>

<script>
// import DetailPage from "./DetailPage";
import { meatydetali } from "../API/index";
import HomeAll from "../components/HomeAll.vue";
// 在此处引用button组件

export default {
  props: ["type"],
  name: "reqCategoryList",
  components: {
    HomeAll,
    // DetailPage,
  },
  data() {
    return {
      items: [],
      name: "",
      keyWord: " ",
      SearchVault: "SearchVault",
      tableData: []
    };
  },
  mounted() {
    meatydetali().then((data) => {
      this.tableData = data.data;
      console.log("---> ", this.tableData);
    });
  },
};
</script>

<style>

</style>