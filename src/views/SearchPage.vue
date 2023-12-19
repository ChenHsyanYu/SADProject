<template>
  <div class="all">
    <div class="head">
      <span class="header">搜尋 Search to trace</span>
      <el-button size="large" class="button" @click="back"><span class="back"> 回到產品頁面</span></el-button>
    </div>
    
    <div class="searchById">
    <span class="title">依批號查詢</span>
    <el-autocomplete
        v-model="state1"
        :fetch-suggestions="querySearch"
        clearable
        class="searchBar"
        placeholder="請輸入批號查詢"
        @select="handleSelect"
        size="large"
      />
      <el-button type="primary" size="large">查詢</el-button>
    </div>
    <!--  -->
    <div class="searchByName">
      <span class="title">依名稱查詢</span>
      <el-autocomplete
        v-model="state2"
        :fetch-suggestions="querySearch"
        clearable
        class="searchBar"
        placeholder="請輸入名稱查詢"
        @select="handleSelect"
        size="large"
      />
      <el-button type="primary" size="large">查詢</el-button>
    </div>
    
  </div>
  
</template>

<script>
import { onMounted, ref } from 'vue';
import { useRouter } from 'vue-router';
export default {

  setup(){
    const state1 = ref('');
    const state2 = ref('');
    const restaurants = ref([]);
    const router = useRouter();
    const back = () =>{
      router.push('/timeline');
    };
    const querySearch = (queryString, cb) => {
    const results = queryString ? restaurants.value.filter(createFilter(queryString)) : restaurants.value;
  // 調用回調函數以返回建議
    cb(results);
  };

  const createFilter = (queryString) => {
    return (restaurant) => {
      return (
        restaurant.value.toLowerCase().indexOf(queryString.toLowerCase()) === 0
      );
    };
  };

  const loadAll = () => {
    return [
      { value: '4x2lu6KpZUthHdLw$Adj'},
      { value: '紡織原料'}
    ];
  };

  const handleSelect = (item) => {
    console.log(item);
  };

  onMounted(() => {
    restaurants.value = loadAll();
  });

    return{
      handleSelect,
      querySearch,
      state1,
      state2,
      back,
    }
  }

}
</script>

<style scoped>

  .searchBar{
    padding: 30px;
    margin: 0 auto;
    display: block;
    font-size: 24px;
  }

  .all{
    /* position: absolute; */
    display: flex;
    top: 9%;
    /* gap: 50%; */
  }
  .searchById{
    position: absolute;
    left: 0;
    width: 50%;
    height: 90%;
    display: block;
    align-content: center;
    align-items: center;
    border-right: 1px solid;
    top:10%;
    padding-top: 18%;
  }
  .searchByName{
    width: 50%;
    height:90%;
    position: absolute;
    left: 50%;
    top: 10%;
    align-items: center;
    padding-top: 18% ;
  }

  .header{
    font-size: 38px;
    padding: 10px;
  }
  .back{
    padding: 10px;

  }
  .button{
    /* display: block; */
    padding: 10px;
    margin: 10px;
    position: absolute;
    right: 20px;
  }
  .head{
    display: flex;
    justify-content: space-between;
  }
  .title{
    padding: 20px;
    display: block;
    font-size: 26px;
  }
</style>