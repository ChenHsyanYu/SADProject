<!-- App.vue -->
<template>
    <div>
      <span class="header">族譜圖搜尋 Family tree</span>
      <div class="classifier"><span>產品 product</span><span>銷售商 seller</span><span>加工廠 processor</span><span>原料供應商 supplier</span></div>
      <!-- <TreeNode :node="familyTree" @toggle="toggleNode" /> -->
      <TreeNode :node="familyTree" :level="0" @toggle="toggleNode" class="tree"/>
    </div>
  </template>
  
  <script>
  import TreeNode from '../views/TreeNode.vue';
  
  export default {
    components:{
        TreeNode,
    },
    data() {
      return {
        familyTree: {
          name: '衣服A',
          level: 0,
          children: [
            {
              name: 'Nike',
              level: 1,
              children: [
                { name: '廠商棉質處理',
                  level: 2, 
                    children:[
                        {name: '廠商棉', level: 3 },
                        {name: '廠商絲料', level: 3 },
                        {name: '廠商紡織原料', level: 3 },
                    ],
                },
                { name: '廠商加工成品' , level: 2 },
                { name: '廠商品牌印刷' , level: 2 },
              ],
            },
            {
              name: 'ABC Mart',
              level: 1,
              children: [
                { name: '廠商棉質處理' , level: 2 },
                { name: '廠商加工成品' , level: 2 },
                { name: '廠商品牌印刷' , level: 2 },
              ],
            },
          ],
        },
      };
    },
    methods: {
      toggleNode(node) {
        node.isOpen = !node.isOpen;
      },
    },
    // components: {
    //   TreeNode,
    // },
  };
  </script>

  <style scoped>
    .header{
      display: block;
      font-size: 36px;
      padding:15px;
      border-bottom: 1px solid;
    }
    /* .tree{
      margin-top: 0;
    } */
    .classifier{
      display: flex;
      font-size: 28px;
      gap: 150px;
    }

    .classifier > span{
      display: block;
      text-align: center;
      padding: 10px 40px;
    }
  </style>
  