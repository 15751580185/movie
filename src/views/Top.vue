<template>
    <div>
        <div style="border-bottom:1px dashed lightgrey;margin-bottom: 15px;">
        <h1>排行榜</h1>
        </div>
        <el-row type="flex" justify="center" :gutter="20" v-for="subList in movieList">
            <el-col span="8" >
                    <img src="../assets/6.jpg" style="float:left; margin-right:20px;">
                    <span style="font-size:13px;float:left;">爱尔兰人</span><br>
                    <span class="pl"> <table style="text-align:left;border:0;"><br><br>导演：: 马丁·斯科塞斯<br>编剧： 查尔斯·布兰特 / 玛格/斯蒂文/泽里安/
                        比尔/芬格·斯迪<br>主演： : 罗伯特·德尼罗 / 阿尔·帕西诺 / 乔·佩西 / 安娜·帕奎因 / 杰西·普莱蒙 / 更多...
                        <br>类型：剧情 /传记 / 犯罪</table></span><br>
                <el-rate
                        v-model="value"
                        disabled
                        show-score
                        text-color="#ff9900"
                        score-template="{value}">
                </el-rate>
                <span class="rating_nums">9.1</span>
                    <span class="pl">(46205人评价)</span>
            </el-col>
        </el-row><br>


            <el-row type="flex" justify="center" :gutter="20" >
                <el-col span="8" >
                    <img src="../assets/1.jpg" style="float:left; margin-right:20px;">
                        <span style="font-size:13px;float:left;">小丑</span><br>
                        <span class="pl"> <table style="text-align:left;border:0;">
                            <br><br>导演： 托德·菲利普斯<br>编剧： 托德·菲利普斯 / 斯科特·西尔弗 / 鲍勃·凯恩 /
                        比尔·芬格<br>主演： 杰昆·菲尼克斯 /罗伯特·德尼罗 / 马克·马龙 / 莎姬·贝兹 / 谢伊·惠格姆
                            <br>类型：剧情 / 惊悚 / 犯罪</table>
                        </span><br>
                    <el-rate
                            v-model="value"
                            disabled
                            show-score
                            text-color="#ff9900"
                            score-template="{value}">
                    </el-rate>
                        <span class="rating_nums">8.4</span>
                        <span class="pl">(36892人评价)</span>
                </el-col>
            </el-row><br>

            <el-row type="flex" justify="center" :gutter="20" >
                <el-col span="8" >
                    <img src="../assets/10.jpg" style="float:left; margin-right:20px;">
                        <span style="font-size:13px;float:left;">地久天长</span><br>
                        <span class="pl"> <table style="text-align:left;border:0;"><br><br>导演: 王小帅<br>编剧： 阿美 / 王小帅<br>
                            主演： 王景春 / 咏梅 / 齐溪 / 王源 / 杜江 / 艾丽娅 / 徐程 / 李菁菁 / 赵燕国彰
                            <br>类型：剧情 /  家庭</table>
                        </span><br>
                        <el-rate
                                v-model="value"
                                disabled
                                show-score
                                text-color="#ff9900"
                                score-template="{value}">
                        </el-rate>
                        <span class="rating_nums">8.0</span>
                        <span class="pl">(35668人评价)</span>
                </el-col>
            </el-row>

        </div>
</template>
<script>
    export default {
        data() {
            return {
                value:4.0
            }
        }
    }
</script>

<style>
    img
    {
        width: 160px;
        height: 240px;
    }
    .rating_nums
    {
        color:#e09015;
        font-size:12px;
        padding:0 3px;
    }
    .pl
    {
        color:#666666;
        font-size:13px;
        line-height:150%;
    }
</style>
