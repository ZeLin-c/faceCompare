<template>
  <div class="home">
    <!-- 海报展示图 -->
    <div class="poster">
      <img src="../assets/background.jpg" width="414" height="200" alt="">
    </div>
    <!-- 下方区域 -->
    <div class="container">
      <div class="container-square">
        <div class="face-analysis">
          <span>人脸分析</span>
        </div>
        <div class="square-left">
          <router-link to="/home/faceCompare">
             <el-button  icon="el-icon-user-solid" type="primary">人脸比对</el-button>
          </router-link>
        </div>
        <div class="square-right">
          <el-button  icon="el-icon-user-solid" type="primary" @click="message">人脸融合</el-button>
        </div>
      </div>
      <div class="container-square">
        <div class="face-division">
          <span>五官分割</span>
        </div>
        <div class="square-left">
          <router-link to="/home/faceDivision">
            <el-button  icon="el-icon-s-custom" type="primary">五官比对</el-button>
          </router-link>
        </div>
        <div class="square-right">
          <el-button  icon="el-icon-s-custom" type="primary" @click="message">颜值评分</el-button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  props: {
    msg: String
  },
  data() {
    return {
     
    };
  },
  methods: {
    // 提示消息
    message() {
      this.$message('该功能尚在开发中');
    }
  }
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
span {
  float:left;
  font-family: STSong;
  font-weight: bold;
  color:rgba(8, 1, 24, 0.56);
}
i {
  float: left;
  color:blue;
  width:30px;
  height: 30px;
}
.el-button {
  width:150px;
  background-color: #fff;
  /* border:1px solid rgb(138, 137, 137);  */
  font-family: STSong;
  color:#26a2ff;
  font-size:16px;
  font-weight: bold;
}
.container {
  width:390px;
  height: 360px;
  /* background-color: red; */
  margin:0 auto;
  margin-top:35px;
}
.container-square {
  width:390px;
  height:130px;
}
.face-analysis {
  float:left;
  width:390px;
  margin-bottom:20px;
}
.face-division {
  float:left;
  width:390px;
  margin-bottom:20px;
}
.square-left {
  width:150px;
  height:42px;
  float:left; 
  line-height: 30px;
}
.square-right {
  width:150px;
  height:42px;
  float:right; 
  line-height: 30px;
}
.text {
  font-size: 16px;
  line-height: 42px;
  padding-left:50px;
}
.icon {
  float: left;
  line-height:42px ;
}
</style>
