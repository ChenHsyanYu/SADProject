<!-- App.vue -->
<template>
    <div>
      <TreeNode :node="familyTree" @toggle="toggleNode" />
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
          children: [
            {
              name: 'Nike',
              children: [
                { name: '廠商棉質處理',
                    children:[
                        {name: ' 廠商棉'},
                        {name: ' 廠商絲料'},
                        {name: ' 廠商紡織原料'},
                    ],
                },
                { name: '廠商加工成品' },
                { name: '廠商品牌印刷' },
              ],
            },
            {
              name: 'ABC Mart',
              children: [
                { name: '廠商棉質處理' },
                { name: '廠商加工成品' },
                { name: '廠商品牌印刷' },
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
  