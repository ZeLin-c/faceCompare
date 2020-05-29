<template>
  <div class="faceCompare">
    <!-- 海报展示图 -->
    <div class="poster">
      <img src="../assets/background.jpg" width="414" height="200" alt="">
    </div>
    <div class="uploadImg">
      <el-upload
      action="https://jsonplaceholder.typicode.com/posts/"
      list-type="picture-card"
      limit="2"
      :on-change="handleChange"
      :on-remove="handleRemove"
      :on-exceed="handleExceed"
    >
      <i class="el-icon-plus"></i>
    </el-upload>
    </div>
    <el-button icon="el-icon-upload" type="primary" v-show="isShowBtn" @click="faceCompare">开始检测吧</el-button>
    <el-button icon="el-icon-s-help" type="primary" v-show="isShowSimilarity">相似度：{{similarity}}</el-button>
  </div>
</template>
<script>
import { uploadImgToBase64 } from '@/utils' // 导入本地图片转base64的方法
export default {
  data() {
    return {
      dialogImageUrl: "",
      dialogVisible: false,
      // 上传数计数器
      handleCount: 0,
      imgBase64_1: "",
      imgBase64_2: "",
      isShowBtn:false,
      similarity: 0,
      isShowSimilarity:false
    };
  },
   methods: {
    handleRemove(file, fileList) {
      this.handleCount --;
      console.log(file, fileList);
      console.log(this.handleCount);
      if(this.handleCount == 1) {
        this.isShowBtn = false;
        this.isShowSimilarity = false;
      }
    },
    async handleChange(file) {
      this.handleCount ++;
      this.dialogImageUrl = file.url;
      // console.log(file.url)
      this.dialogVisible = true;
      // 并发 转码轮播图片list => base64
      const response = await uploadImgToBase64(file.raw)
      if(this.handleCount == 1) {
        this.imgBase64_1 = response.result.replace(/.*;base64,/, '') // 去掉data:image/jpeg;base64
      }
      else {
        this.imgBase64_2 = response.result.replace(/.*;base64,/, '') // 去掉data:image/jpeg;base64
        this.isShowBtn = true;
      }
      // console.log(this.imgBase64)
      console.log(this.handleCount);
    },
    async faceCompare() {
      console.log(this.dialogImageUrl);
      const res = await this.$http.post(
        "https://api-cn.faceplusplus.com/facepp/v3/compare",
        {
          api_key: "bZyVoXsm4I7b2n3fmCyTH95qhMxRe_hu",
          api_secret: "T4Z3dOFIVUTQOdynL2GfsJ2BgWV8BP1k",
          image_base64_1:this.imgBase64_1,
          image_base64_2:this.imgBase64_2   
        }
      );
      console.log(res.data.confidence);
      this.similarity = res.data.confidence;
      this.isShowSimilarity = true;
      this.isShowBtn = false;
      if(res.data.confidence >= 85)
        this.$message('很有可能是同一人哦');
      else
        this.$message('大概率不是同一人呢');
    },
    // 超出文件上传限制时的钩子函数
    handleExceed() {
      this.$message('人脸比对只需要两张图片哦');
    }
  }
};
</script>
<style scoped>
.uploadImg {
    width:414px;
    height:330px;
}
.el-button {
    font-family: STSong;
}
</style>