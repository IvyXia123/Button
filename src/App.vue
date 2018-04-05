<template>
    <div id="app">
        <div class="btnOne">
            <input class="input" type="text" v-model="iptVal1"/>
            <btn-com :data="json.buy" @emitVal="receiveVal" @emitShowStatus="receiveShowStatus"></btn-com>
        </div>
        <div class="btnTwo">
            <input class="input" type="text" v-model="iptVal2"/>
            <btn-com :data="json.sell" @emitVal="receiveVal" @emitShowStatus="receiveShowStatus"></btn-com>
        </div>
        <div class="btnThree">
            <input class="input" type="text" v-model="iptVal3"/>
            <btn-com :data="json.change" @emitVal="receiveVal" @emitShowStatus="receiveShowStatus"></btn-com>
        </div>
    </div>
</template>

<script>
    import BtnCom from './components/Button'

    export default {
        name: 'app',
        data() {
            return {
                json: {
                    "buy": [
                        {"text": "买"},
                        {"list": ["B1", "B2", "B3"]}
                    ],
                    "sell": [
                        {"text": "卖"},
                        {"list": ["S1", "S2", "S3"]}
                    ],
                    "change": [
                        {"text": "换"},
                        {"list": ["C1", "C2", "C3"]}
                    ]
                },
                iptVal1: "",
                iptVal2: "",
                iptVal3: ""
            }
        },
        components: {
            BtnCom
        },
        methods: {
            switchFn(obj) {
                var iptV = "";
                iptV = ((typeof obj.showStatus != undefined) && obj.showStatus == false) ? "" : obj.liVal;
                switch (obj.text) {
                    case "买":
                        this.iptVal1 = iptV;
                        break;
                    case "卖":
                        this.iptVal2 = iptV;
                        break;
                    case "换":
                        this.iptVal3 = iptV;
                        break;
                }
            },
            receiveVal(obj) {
                this.switchFn(obj);
            },
            receiveShowStatus(obj) {
                this.switchFn(obj);
            }
        }
    }
</script>

<style lang="less" type="text/less">
    html, body {
        margin: 0;
        padding: 0;
        width: 100%;
        height: 100%;
        #app {
            width: 100%;
            height: 100%;
            padding: 20px 30px;
            box-sizing: border-box;
            overflow: hidden;
            .btnOne, .btnTwo, .btnThree {
                float: left;
                width: 45%;
                height: 400px;
                padding: 20px;
                margin: 10px 20px;
                font-size: 16px;
                background: #EEE9E9;
                box-sizing: border-box;
                border-radius:5px;
                .input {
                    margin-bottom: 20px;
                }
            }
        }
    }
</style>
