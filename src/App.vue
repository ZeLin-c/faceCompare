<template>
  <div id="app">
    <mt-header class="header-text" fixed title="AI 人像识别" >
      <router-link to="/" slot="left">
        <mt-button icon="back">返回</mt-button>
      </router-link>
      <mt-button icon="more" slot="right"></mt-button>
    </mt-header>

    <!-- 中间路由跳转区域 -->
    <router-view/>

    <nav class="mui-bar mui-bar-tab">
			<router-link id="defaultTab" class="mui-tab-item" to="/home">
				<span class="mui-icon mui-icon-pengyouquan"></span>
				<span class="mui-tab-label" style="padding-top:5px;font-family:STSong">AI平台</span>
			</router-link>
			<router-link class="mui-tab-item" to="/myself">
				<span class="mui-icon mui-icon-contact"></span>
				<span class="mui-tab-label" style="padding-top:5px;font-family:STSong">个人中心</span>
			</router-link>
		</nav>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-top: 41px;
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
.header-text {
  font-family:STSong;
}
</style>
