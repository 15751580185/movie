<template>
    <div>
        <h2>
            {{movie.title}}
            <span style="color:lightgray">
                ({{movie.publishDate}})
            </span>
        </h2>
        <el-row type="flex" justify="center" :gutter="20">
            <el-col :span="5">
                <img src="../assets/1.jpg" style="width: 150px;height:200px">
            </el-col>
            <el-col :span="8" style="text-align: left">
                <div>
                    导演： {{movie.director}}
                </div>
                <div>
                    编剧：
                    <template v-for="(a,index) in movie.author">
                        <span style="color:#37a">{{a}}</span>
                        <template v-if="index!=movie.author.length-1">
                            /
                        </template>
                    </template>
                </div>
                <div>
                    主演：
                    <template v-for="(a,index) in movie.actors">
                        <span style="color:#37a">{{a}}</span>
                        <template v-if="index!=movie.actors.length-1">
                            /
                        </template>
                    </template>
                </div>
                <div>类型：{{movie.category}}</div>
                <div>
                    官方网站：
                    <a :href="movie.address" target="_blank">{{movie.address}}</a>
                </div>
                <div>
                    制片国家/地区：{{movie.country}}
                </div>
                <div>
                    语言：{{movie.lan}}
                </div>
                <div>
                    上映日期：{{movie.publishDate}}
                </div>
                <div>
                    片长：{{movie.timeLength}} 分钟
                </div>
                <div>
                    又名：{{movie.alias}}
                </div>
            </el-col>

            <el-col :span="5" style="border-left: 1px solid lightgray;text-align: left">
                <h5 style="color:lightgray;margin: 5px">豆瓣评分</h5>
                <div>
                    <div style="display: inline-block">
                        <h1 style="margin: 5px">{{movie.scoring.score}}</h1>
                    </div>
                    <div style="display: inline-block">
                        <el-rate disabled v-model="movie.scoring.star"></el-rate>
                        <div style="font-size:12px;color:#37a;padding-left: 3px">{{movie.scoring.amount}}人评价</div>
                    </div>
                    <div>
                        <el-row>
                            <el-col :span="4" class="star-col">
                                5星
                            </el-col>
                            <el-col :span="14">
                                <el-progress :percentage="movie.scoring.five" color="#ffd596"></el-progress>
                            </el-col>
                        </el-row>
                        <el-row>
                            <el-col :span="4" class="star-col">
                                4星
                            </el-col>
                            <el-col :span="14">
                                <el-progress :percentage="movie.scoring.four" color="#ffd596"></el-progress>
                            </el-col>
                        </el-row>
                        <el-row>
                            <el-col :span="4" class="star-col">
                                3星
                            </el-col>
                            <el-col :span="14">
                                <el-progress :percentage="movie.scoring.three" color="#ffd596"></el-progress>
                            </el-col>
                        </el-row>
                        <el-row>
                            <el-col :span="4" class="star-col">
                                2星
                            </el-col>
                            <el-col :span="14">
                                <el-progress :percentage="movie.scoring.two" color="#ffd596"></el-progress>
                            </el-col>
                        </el-row>
                        <el-row>
                            <el-col :span="4" class="star-col">
                                1星
                            </el-col>
                            <el-col :span="14">
                                <el-progress :percentage="movie.scoring.one" color="#ffd596"></el-progress>
                            </el-col>
                        </el-row>
                    </div>
                </div>
            </el-col>

        </el-row>
        <el-row style="margin-top: 30px">
            <el-col :span="2" :offset="4">
                <el-button size="mini" style="background-color:#FFEADA">想看</el-button>
            </el-col>
            <el-col :span="2">
                <el-button size="mini" style="background-color:#FFEADA">看过</el-button>
            </el-col>
            <el-col :span="4">
                评价：
                <el-rate style="display: inline-block"></el-rate>
            </el-col>
        </el-row>
        <el-row style="text-align: left;margin-top: 30px">

            <el-col :span="16" :offset="4">
                <span class="title-col" >{{movie.title}}的剧情简介· · · · · ·</span>
            </el-col>
        </el-row>
        <el-row style="text-align: left;margin-top: 30px">
            <el-col :span="16" :offset="4">
                <p style="text-indent: 20px">{{movie.describe}}</p>
            </el-col>
        </el-row>
        <el-row style="text-align: left;margin-top: 30px">
            <el-col :span="16" :offset="4">
                <span class="title-col">{{movie.title}}的短评· · · · · · </span>( 全部 44584 条 )
            </el-col>
        </el-row>
        <el-row style="text-align: left;font-size: 12px" v-for="comment in movie.comments">
            <el-col :span="16" :offset="4">
                <hr style="color:lightgray"/>
                <div>
                    <span>{{comment.user}}</span>看过
                    <el-rate disabled v-model="comment.star" style="display:inline-block"></el-rate>
                    <span>{{comment.date}}</span>
                    <span style="position:relative;left:60%">{{comment.zan}}有用</span>
                </div>
                <p>
                    {{comment.content}}
                </p>
            </el-col>
        </el-row>
    </div>
</template>
<script>
    import ElProgress from "../../node_modules/element-ui/packages/progress/src/progress";
    export default {
        components: {ElProgress},
        /**
         * 当detail.vue被加载时，首先执行created函数，实际上指的是页面未加载完成前，先执行的函数
         * 生命周期钩子函数
         */
        created: function () {
            //先给movie对象附上title的值
            //console.log(this.$route)
            //alert(this.$route.params.title)
            this.movie.title = this.$route.params.title;
        },
        data () {
            return {
                movie: {
                    director: "托德·菲利普斯",
                    author: [
                        "托德·菲利普斯",
                        "斯科特·西尔弗",
                        "鲍勃·凯恩",
                        "比尔·芬格"],
                    actors: [
                        "杰昆·菲尼克斯",
                        "罗伯特·德尼罗",
                        "马克·马龙",
                        "莎姬·贝兹",
                        " 谢伊·惠格姆"
                    ],
                    category: "剧情 / 惊悚 / 犯罪",
                    address: "http://www.jokermovie.net",
                    country: "加拿大 / 美国",
                    lan: "英语",
                    publishDate: "2019-08-31",
                    timeLength: "122",
                    alias: "小丑起源电影：罗密欧 / Romeo / Joker Origin ",
                    title: "",
                    describe: "电影《小丑》以同名DC漫画角色为基础，由华纳兄弟影业公司发行，计划于2019年10月4日上映。" +
                    "本片的故事将独立于DCEU之外，故事背景设置在20世纪80年代，讲述了一位生活陷入困境的脱口秀喜剧演员渐渐走向精神的崩溃，在哥谭市开始了疯狂的犯罪生涯，最终成为了蝙蝠侠的宿敌“小丑”的故事。" +
                    "本片由《宿醉》的导演托德菲利普斯执导，他与编剧斯科特西尔弗一起撰写了编剧。杰昆菲尼克斯本片中饰演主人公“小丑”，其他的主演包括罗伯特德尼罗、莎姬贝兹、马克马龙等。",
                    comments: [
                        {
                            user: "谋杀游戏机",
                            content: "完全不是超英片，就是一个以普通底层小市民为主角的犯罪片，大概也是这些年漫威DC所有电影里人性剖析最深刻的一部。影片对哥谭市有着出色的氛围营造，阴暗潮湿的道路，满目垃圾的街头",
                            star: 4,
                            date: "2019-08-31",
                            zan: "6083"
                        },
                        {
                            user: "保卫胡萝卜",
                            content: "再也不要有人跳出来把DC和漫威比了，这已经是金狮体系了。",
                            star: 4,
                            date: "2019-09-10",
                            zan: "2288"
                        }
                    ],
                    scoring: {
                        score: 8.8,
                        five: 60,
                        four: 12,
                        three: 10,
                        two: 5,
                        one: 2,
                        amount: 474206,
                        star: 4.5
                    }
                }
            }
        }
    }
</script>
<style scoped>
    .star-col {
        font-size: 14px;
    }

    .title-col {
        color: #007722;
        font-size: 16px
    }
</style>