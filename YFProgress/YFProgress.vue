<template>
    <div class="y-progress" v-bind:style="{'background-color':tip[0].fillStyle || '#ccc'}">
        <el-tooltip v-bind:content="tip[0].text.replace('X',total<done?0:(total-done))" placement="top">
            <p class="y-progress_text" v-bind:style="{'width':(100-donePercent)+'%'}"></p>
        </el-tooltip>
        <div class="y-progress_bar" v-bind:style="{'width':donePercent+ '%','background-color':tip[1].fillStyle || '#9c3'}">
            <el-tooltip v-bind:content="tip[1].text.replace('X',done>total?total:done)" placement="top">
                <p class="y-progress_text" v-bind:style="{'width':(100-modifyPercent)+'%'}"></p>
            </el-tooltip>
            <div class="y-progress_bar" v-bind:style="{'width':modifyPercent+ '%','background-color':tip[2].fillStyle || '#080'}">
                <el-tooltip v-bind:content="tip[2].text.replace('X',modify>done?done:modify)" placement="top">
                    <p class="y-progress_text" v-bind:style="{'width':'100%'}"></p>
                </el-tooltip>
            </div>
        </div>
    </div>
</template>
<script>
    var __CONFIG_YFProgrss = {
        tip: [
            {
                text: "未提交X人",
                fillStyle: "#ccc",
            }, {
                text: "已提交X人",
                fillStyle: "#9c3",
            }, {
                text: "已批改X人",
                fillStyle: "#080"
            }
        ]
    };
    
    export default {
        name:"yf-progress",
        props: {
            "total": {
                type: Number,
                default:0
                //required:true
            },
            "done": {
                type: Number,
                //required: true
                default: 0
            },
            "modify": {
                type: Number,
                //required: true
                default: 0
            },
            "tip": {
                type: Array,
                default: __CONFIG_YFProgrss.tip
            }
        },
        data: function () {
            return {
                inTotal: this.total,
                inDone: this.done,
                inModify: this.modify,
                donePercent: this.done==0?0:(this.done>=this.total ? 1 : this.done / this.total)*100,
                modifyPercent: this.modify == 0 ? 0 :(this.modify>=this.done ? 1: this.modify / this.done)*100,
            };
        },
        watch: {
            "done": function (val) {
                this.donePercent = val == 0 ? 0 : (val >= this.total ? 1 : val / this.total) * 100;
            },
            "modify": function (val) {
                this.modifyPercent = val == 0 ? 0 : (val >= this.done ? 1 : val / this.done) * 100;
            }
        },
        mounted: function () {
            // You can remove templates from the HTML when component was rendered
            var tpl = document.getElementById("tpl_Progress");
            tpl && ((tpl.remove) ? (tpl.remove()) : (tpl.parentNode && tpl.parentNode.removeChild(tpl)));
        }
    };
</script>
<style scoped>
.y-progress {
    position: relative;
    width: 100%;
    height: 8px;
    background-color: #ccc;
    border-radius: 4px;
    overflow: hidden;
}
.y-progress_bar {
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    border-radius: 4px;
    transition: all 1.5s ease;
}
.y-progress_text {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    text-align: center;
}
</style>
