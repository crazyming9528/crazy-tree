<template>
  <div id="app">
    <div class="top">
      <img alt="Vue logo" src="./assets/logo.png">
      <HelloWorld msg="Crazyming Tree Demo"/>
    </div>
    <Tree :listData="listData" ></Tree>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Tree from './components/tree'


export default {
  name: 'app',
  components: {
    HelloWorld,
    Tree
  },
  data(){
    return{
      listData:[
        {
          title:"食品生鲜",
          expansion:true,
          type:'primary',
          child:[
            {
              title:"新鲜水果",
              expansion:true,
              child:[
                {
                  title:"阿克苏苹果",
                  expansion:true,
                  child:[
                    {
                      title:"阿克苏的红富士",
                      expansion:false,
                      child:[],
                    },
                    {
                      title:"阿克苏的大苹果  (还能展开  点击展开 再次点击 收起)",
                      expansion:false,
                      child:[
                        {
                          title:"依托数据  无限级 树形   数据有多少层 就能show多少层",
                          expansion:false,
                          child:[],
                        },

                      ]
                    },
                  ]
                },
                {
                  title:"吐鲁番葡萄",
                  expansion:false,
                  child:[],
                },
                {
                  title:"库尔勒香梨",
                  expansion:false,
                  child:[],
                },
              ]
            },
            {
              title:"蔬菜蛋品",
              expansion:false,
              child:[
                {
                  title:"土豆",
                  expansion:false,
                  child:[],
                },
                {
                  title:"萝卜",
                  expansion:false,
                  child:[],
                },
                {
                  title:"菠菜",
                  expansion:false,
                  child:[],
                },
                {
                  title:"鸡蛋",
                  expansion:false,
                  child:[],
                },
              ]
            },
            {
              title:"河鲜海鲜",
              expansion:false,
              child:[],
            },

          ]
        },
        {
          title:"日用百货",
          expansion:false,
          type:'primary',
          child:[
            {
              title:"床上用品",
              expansion:false,
              child:[
                {
                  title:"被子",
                  expansion:false,
                  child:[],
                },
                {
                  title:"枕头",
                  expansion:false,
                  child:[],
                },
              ],
            },
            {
              title:"厨房用品",
              expansion:false,
              child:[],
            },
            {
              title:"洗浴用品",
              expansion:false,
              child:[],
            },

          ]
        },
        {
          title:"菜单三",
          expansion:false,
          type:'primary',
          child:[
            {
              title:"菜单222222222",
              expansion:false,
              child:[],
            },
            {
              title:"菜单222222222",
              expansion:false,
              child:[],
            },
            {
              title:"菜单222222222",
              expansion:false,
              child:[],
            },

          ]
        }
      ]
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
.top{

  text-align: center;

}

}

</style>
