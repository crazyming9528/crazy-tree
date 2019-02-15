<template>

    <ul>
        <template v-for="(item,index) in listData">
            <li v-if="item.child.length <= 0" :class="{'primary-menu':item.type==='primary'}" >
                <a href="javascript:void(0)">
                    <span  v-if="!item.edit">{{item.title}}</span><input v-if="item.edit" type="text" :value="item.title"><button v-if="item.edit" @click="confirmUpdate($event,index)">确认</button> <button v-if="item.edit" @click="update($event,index)">取消</button></a>
                <div class="btn-group" >
                    <button v-if="!item.edit" @click="update($event,index)">修改</button>
                    <button @click="deleteFn(index)">删除</button>
                    <button @click="addChild(index)">添加子项</button>
                </div>
            </li>
            <li v-else :class="{'primary-menu':item.type==='primary'}" >
                <a href="javascript:void(0)" class="color-blue" @click="showChildMenu(index)">
                    <span  v-if="!item.edit">{{item.title}}</span><input v-if="item.edit" type="text" :value="item.title"><button v-if="item.edit" @click="confirmUpdate($event,index)">确认</button> <button v-if="item.edit" @click="update($event,index)">取消</button>
                </a>
                <div class="btn-group" >
                    <button v-if="!item.edit" @click="update($event,index)">修改</button>
                    <button @click="deleteFn(index)">删除</button>
                    <button @click="addChild(index)">添加子项</button>
                </div>
                <tree v-if="item.expansion" :listData="item.child"></tree>
            </li>
        </template>
        <!--<button @click="add()">添加同级项</button>-->

    </ul>

</template>

<script>
    export default {
        name: "tree",
        props: {
            listData: {
                type: Array,
                required: true
            }
        },
        data() {
            return {}
        },
        methods: {
            showChildMenu(index) {
                console.log(index);
                let temp =  this.listData[index]
                temp.expansion = !temp.expansion;
                this.listData.splice(index, 1,temp);
            },
            deleteFn(index) {
                this.listData.splice(index, 1)
            },
            // add() {
            //   this.listData.push( {
            //     title: "新增的项",
            //     child: [],
            //   });
            //
            //
            //   // 移除 所有项的 编辑效果
            //     this.listData.forEach((item,i)=>{
            //         item.edit = false;
            //     });
            //
            //     // 给最后一项加上编辑效果
            //   this.listData[this.listData.length-1].edit = true;
            //
            // },
            update(e,index) {
                let temp = this.listData[index];
                temp.edit = !temp.edit;



                // 移除 其他项的 编辑效果
                if (temp.edit){
                    this.listData.forEach((item,i)=>{

                        if (i !== index){
                            item.edit = false;
                        }

                    })
                }
                // this.$set(this.listData,index,temp)
                this.listData.splice(index, 1, temp)
            },
            addChild(index){
                let temp = this.listData[index];
                temp.child.push(
                    {
                        title:"新增的子项",
                        child:[],
                    });

                temp.expansion =true;
                temp.child.forEach((item,i)=>{
                    item.edit = false;
                });
                temp.child[temp.child.length-1].edit = true;
                this.listData.splice(index, 1, temp)
            },
            confirmUpdate(e,index){
                let temp = this.listData[index];
                temp.edit = false;
                temp.title = e.target.previousSibling.value;// 找到 按钮前面的  input元素并获取值
                // this.$set(this.listData,index,temp)
                this.listData.splice(index, 1, temp)
            }

        }
    }
</script>

<style lang="scss" scoped>


    .color-blue {
        color: #7cc0ff !important;
    }

    a {
        color: white;
        text-decoration: none;
        transition: all 0.5s;
    }

    button{
        border:none;
        background: #e7f5f8;
        padding: 2px;
        box-sizing: border-box;
        color: #5d90c0;
        margin-left: 5px;
    }


    ul {
        padding: 0;
        margin: 0;


    }

    .primary-menu {
        position: relative;
        margin-bottom: 10px;

        & > a {
            background-color: #A7C4D7;
            background-image: linear-gradient(120deg, #ebeff8 10%, #bde9f8 70%);
            background-size: 100% 100%;
            padding: 10px;
            box-sizing: border-box;
            border-radius: 3px;
            display: inline-block;
            width: 100%;
        }
        .btn-group{
            position: absolute;
            top: 10px;
            right: 10px;
            height: 100%;
            /*button{*/
            /*border:none;*/
            /*background: #e7f5f8;*/
            /*padding: 2px;*/
            /*box-sizing: border-box;*/
            /*color: #1879ff;*/
            /*}*/

        }

        ul {
            padding-left: 20px;

            li {

                position: relative;




                a {
                    color: black;
                    width: 100%;
                    display: inline-block;
                    padding: 10px;
                    box-sizing: border-box;

                    &:hover {
                        color: #7bbdbc!important;
                        background-color: rgba(228, 228, 228, 0.35);
                    }
                }

                ul {
                    margin-top: 15px;
                }

                /*.btn-group {*/
                /*position: absolute;*/
                /*top: 0;*/
                /*right: 15px;*/

                /*}*/


            }
        }

    }

</style>
