<template>
  <div id="app">
    <!--<div id="nav">-->
      <!--<router-link to="/">Home</router-link> |-->
      <!--<router-link to="/about">About</router-link>|-->
      <!--<router-link to="/demo">Demo</router-link>-->
    <!--</div>-->
    <!--&lt;!&ndash;router-view其实就是页面变化的具体内容所在的位置，例如：home切换到about&ndash;&gt;-->
    <!--&lt;!&ndash;要使用动画，请将router-view用transition标签包裹起来,appearActiveClass用于设置想要用什么动画，设置-->
    <!--的是第一次出现页面时的动画，enterActiveClass：用于设置页面切换时动画&ndash;&gt;-->
    <!--<transition appear appearActiveClass="animated zoomInUp" enterActiveClass="animated zoomInUp">-->
      <!--<router-view/>-->
    <!--</transition>-->
    <el-row>
      <el-col :span ="24">
      <el-menu mode="horizontal"
               background-color="#545c64"
                    text-color="#fff"
                         active-text-color="#ffd04b"
                             default-active="/"
                                :router="true">
        <el-menu-item index="/">选电影</el-menu-item>
        <el-menu-item index="/top">排行榜</el-menu-item>
      </el-menu>
      </el-col>
    </el-row>
    <el-row type="flex" justify="center" style="background-color: #f0f3f5" >
      <el-col :span="4">
        <h2 style="color:#27a">豆瓣电影</h2>
      </el-col>
      <el-col :span="6" style="line-height: 71px;">
          <el-input placeholder="搜索电影，电视剧，综艺，艺人...">
              <template slot="append">
                  <i class="el-icon-search"></i>
              </template>
          </el-input>
      </el-col>
    </el-row>
    <el-row>
        <router-view/>
    </el-row>
  </div>
</template>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
