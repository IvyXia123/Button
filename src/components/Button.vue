<template>
    <div class="buttonCom">
        <div class="btn" @click="showStatus" :class="{BtnActive:show}">{{data[0].text}}</div>
        <ul class="list" v-show="show">
            <li v-for="(item,index) in data[1].list" @mouseover="listVal(item,index)" :key="index"
                :class="{listActive:curIndex==index}">{{item}}
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "buttonBox",
        props: ["data"],
        data() {
            return {
                show: false,
                curIndex: -1
            }
        },
        methods: {
            showStatus() {
                this.show = !this.show;
                this.curIndex=-1;
                this.$emit("emitShowStatus", {"text": this.data[0].text, "showStaus": this.show})
            },
            listVal(val, index) {
                this.$emit("emitVal", {"text": this.data[0].text, "liVal": val});
                this.curIndex = index;
            }
        }
    }
</script>

<style lang="less" type="text/less" scoped>
    .buttonCom {
        .btn {
            width: 50px;
            height: 30px;
            line-height: 30px;
            border-radius: 5px;
            border: 1px solid #c0c0c0;
            cursor: pointer;
            text-align: center;
            -moz-border-radius: 5px;
            -webkit-border-radius: 5px;
            -webkit-user-select: none;
        }
        .list {
            background: #CDC9C9;
            margin: 30px 0;
            padding: 0;
            li {
                padding: 10px;
                cursor: pointer;
                list-style: none;
                -webkit-user-select: none;
            }
        }
        .BtnActive {
            border: 3px solid red;
        }
        .listActive {
            background: #F5F5DC;
        }
    }
</style>