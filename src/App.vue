<template>
  <div id="app">
    <div class="top">
      <img alt="Vue logo" src="./assets/logo.png">
      <HelloWorld msg="Crazyming Tree Demo"/>
    </div>

    <button style="width: 180px;height: 50px;margin-bottom: 20px" @click="addNewBuilding()">添加 新的 楼宇/区域</button>
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
      listData: [
        {
          title: "本校区",
          expansion: true,
          type: 'primary',
          child: [
            {
              title: "行政楼",
              child: [],
            },
            {
              title: "男生宿舍",
              expansion: true,
              child: [
                {
                  title: "男生宿舍1栋",
                  child: [],
                },
                {
                  title: "男生宿舍2栋",
                  child: [],
                },
                {
                  title: "男生宿舍3栋",
                  child: [],
                },
                {
                  title: "男生宿舍4栋",
                  child: [],
                },
              ],
            },
            {
              title: "女生宿舍",
              child: [],
            },
            {
              title: "体育馆",
              child: [],
            },
            {
              title: "图书馆",
              child: [],
            },
            {
              title: "1号食堂",
              child: [],
            },
            {
              title: "2号食堂",
              child: [],
            }
          ],
        },
        {
          title: "2校区",
          expansion: true,
          type: 'primary',
          child: [
            {
              title: "体育馆",
              child: [],
            },
            {
              title: "图书馆",
              child: [],
            },
            {
              title: "1号食堂",
              child: [],
            },
          ],
        }
      ]
    }
  },methods:{
    addNewBuilding() {
      this.listData.forEach((item)=>{
        item.expansion = false;
      });
      setTimeout(()=>{
        this.listData.push({
          title: "未命名",
          expansion: true,
          type: 'primary',
          child: [],
        })
      },800);
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
