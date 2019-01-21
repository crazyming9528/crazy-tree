<template>

    <ul>
        <template v-for="(item,index) in listData">
            <li v-if="item.child.length <= 0" :class="{'primary-menu':item.type==='primary'}">
                <a href="javascript:void(0)">{{item.title}}</a>
                <div class="btn-group" v-if="item.type!=='primary'">
                    <button @click="add(index)">添加同级项</button>
                    <button @click="update(index, item.title+'被修改了')">修改此项</button>
                    <button @click="deleteFn(index)">删除此项</button>
                </div>
            </li>
            <li v-else :class="{'primary-menu':item.type==='primary'}" v-if="">
                <a href="javascript:void(0)" class="color-blue" @click="showChildMenu(index)">{{item.title}}</a>
                <div class="btn-group" v-if="item.type!=='primary'">
                    <button @click="add(index)">添加同级项</button>
                    <button @click="update(index, item.title+'被修改了')">修改此项</button>
                    <button @click="deleteFn(index)">删除此项</button>
                </div>
                <tree v-if="item.expansion" :listData="item.child"></tree>
            </li>
        </template>

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
                this.listData[index].expansion = !this.listData[index].expansion;
            },
            deleteFn(index) {
                this.listData.splice(index, 1)
            },
            add(index) {
                this.listData.splice(index + 1, 0, {
                    title: "我是新加的",
                    expansion: false,
                    child: [],
                });
            },
            update(index, text) {
                this.listData[index].title = text;

            }
        }
    }
</script>

<style lang="scss" scoped>

    .color-blue {
        color: #4278ff !important;
    }

    a {
        color: white;
        text-decoration: none;
        transition: all 0.5s;
    }


    ul {
        padding: 0;
        margin: 0;


    }

    .primary-menu {

        & > a {
            background-color: #45e2a8;
            padding: 15px;
            box-sizing: border-box;
            display: block;
            width: 100%;

            &:hover {
                background-color: #ef9000;
            }
        }

        ul {
            padding-left: 50px;

            li {


                position: relative;

                margin-bottom: 15px;


                a {
                    color: black;
                    width: 100%;
                    display: inline-block;

                    &:hover {
                        color: #6ad3ae;
                        background-color: #e4e4e4;
                    }
                }

                ul {
                    margin-top: 15px;
                }

                .btn-group {
                    position: absolute;
                    top: 0;
                    right: 15px;
                }


            }
        }

    }

</style>
