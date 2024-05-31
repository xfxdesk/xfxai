<template>
  <div class="index-page" >
    <div class="menu-box">
      <el-menu
          mode="horizontal"
          :ellipsis="false"
      >
        <div class="menu-item">
          <el-image :src="logo" alt="xfxai"/>
          <div class="title">{{ title }}</div>
        </div>
      <div class="menu-item">
          <a @click="router.push('/chat')" color="#ffffff" style="color:#333333" :dark="false">
            <span>聊天</span>
          </a>

         <a @click="router.push('/mj')" color="#C4CCFD" style="color:#333333" :dark="false">
           <span>绘画</span>
         </a>
         <a @click="router.push('/xmind')" color="#FFFD55" style="color:#333333" :dark="false">
           <span>导图</span>
         </a>
        </div> 
      </el-menu>
    </div>
    <section class="content sec"  id="home">
      <h1 class="navtitle">欢迎使用 {{ title }}</h1>
      <p class="slogan">{{ slogan }}</p>
      <el-button class="begin" @click="router.push('/chat')" color="#ffffff" style="color:#007bff;" :dark="false">
        <span>开始智能生成</span>
      </el-button>
	  <div class="feature">
		  <div class="item">
			  <el-image src="/images/feature1.png"  style="width: 60px;height: 60px;margin:0 auto;"></el-image>
			  <span>全平台支持</span>
		  </div>
		  <div class="item">
		  			  <el-image src="/images/feature2.png"  style="width: 60px;height: 60px;margin:0 auto;"></el-image>
		  			  <span>多模态支持</span>
		  </div>
		  <div class="item">
		  			  <el-image src="/images/feature3.png"  style="width: 60px;height: 60px;margin:0 auto;"></el-image>
		  			  <span>数据云端存</span>
		  </div>
		  <div class="item">
		  			  <el-image src="/images/feature4.png"  style="width: 60px;height: 60px;margin:0 auto;"></el-image>
		  			  <span>海量模板</span>
		  </div>
	  </div>
    </section>
	
	<section class="des1"  id="g1">
	  <div class="left">
		  <span class="title">AI时代</span>
		  <span class="title">永远不要忘了你有智能助手</span>
		  <span class="description">告别传统，拥抱未来</span>
		  <el-button class="begin mt15" @click="router.push('/chat')" color="#ffffff" style="color:#007bff;" :dark="false">
		    <span>开始智能生成</span>
		  </el-button>
	  </div>
	  <div class="right">
		  <el-image src="/images/featurev0.webp"  style="width: 668px;height: 452px;margin:0 auto;"></el-image>
		  
	  </div>
	 
	</section>
	
	<section class="des1"  id="g2">
	  <div class="left">
		 <el-image src="/images/featurev1.webp"  style="width: 668px;height: 452px;margin:0 auto;"></el-image>
		 
	  </div>
	  <div class="right">
		  <span class="title">自动生成PPT和思维导图</span>
		  <span class="title">文案自动生成+智能文档</span>
		  <span class="description">AI赋能让PPT不再困难，人人都是PPT专家</span>
		  <el-button class="begin mt15" @click="router.push('/chat')" color="#ffffff" style="color:#007bff;" :dark="false">
		    <span>开始智能生成</span>
		  </el-button>
	  </div>
	 
	</section>
	
	<section class="des1"  id="g3">
	  <div class="left">
		  <span class="title">提供海量精品模板</span>
		  <span class="title">AI一键更换模板</span>
		  <span class="description">用AI快速实现PPT美化</span>
		  <el-button class="begin mt15" @click="router.push('/chat')" color="#ffffff" style="color:#007bff;" :dark="false">
		    <span>开始智能生成</span>
		  </el-button>
	  </div>
	  <div class="right">
		  <el-image src="/images/featurev4.webp"  style="width: 668px;height: 452px;margin:0 auto;"></el-image>
		  
	  </div>
	 
	</section>
	
	<section class="des1">
	  <div class="labels">
		 <span class="description">欢迎来到小飞侠AI——您的全方位AI学习与办公伙伴！</span>
	  </div>
	 <div class="right">
			<a href="/#home"><span class="link mt15"> 首页 </span></a>
			<a href="/#g1"><span class="link mt35"> 特性 </span></a>
			<a href="/nav"><span class="link mt35"> 分享 </span></a>
		</div>
	</section>
	
	
    <div class="footer">
      <footer-bar />
    </div>
  </div>
</template>

<script setup>

import * as THREE from 'three';
import {onMounted, ref} from "vue";
import {useRouter} from "vue-router";
import FooterBar from "@/components/FooterBar.vue";
import {httpGet} from "@/utils/http";
import {ElMessage} from "element-plus";

const router = useRouter()

const title = ref("xfxai 小飞侠AI")
const logo = ref("/images/logo.png")
const slogan = ref("小飞侠AI解决方案, AI学习助手, AI办公自动化工具, 内容模板库, AI产品与服务, 智能文档生成, 学习资源下载, AI内容创造, 职业发展工具, 智能数据分析")
const size = Math.max(window.innerWidth * 0.5, window.innerHeight * 0.8)
const winHeight = window.innerHeight - 150

onMounted(() => {
  httpGet("/api/config/get?key=system").then(res => {
    title.value = res.data.title
    logo.value = res.data.logo
  }).catch(e => {
    ElMessage.error("获取系统配置失败：" + e.message)
  })
  // init()
})

const init = () => {
  // 创建场景
  // 创建场景
  const scene = new THREE.Scene();

  // 创建相机
  const camera = new THREE.PerspectiveCamera(30, 1, 0.1, 1000);
  camera.position.z = 3.88;

  // 创建渲染器
  const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
  renderer.setSize(size, size);
  renderer.setClearColor(0x000000, 0);
  const container = document.getElementById('animation-container');
  container.appendChild(renderer.domElement);

  // 加载地球纹理
  const loader = new THREE.TextureLoader();
  loader.load(
      '/images/land_ocean_ice_cloud_2048.jpg',
      function (texture) {
        // 创建地球球体
        const geometry = new THREE.SphereGeometry(1, 32, 32);
        const material = new THREE.MeshPhongMaterial({
          map: texture,
          bumpMap: texture, // 使用同一张纹理作为凹凸贴图
          bumpScale: 0.05, // 调整凹凸贴图的影响程度
          specularMap: texture, // 高光贴图
          specular: new THREE.Color('#007bff'), // 高光颜色
        });
        const earth = new THREE.Mesh(geometry, material);
        scene.add(earth);

        // 添加环境光和点光源
        const ambientLight = new THREE.AmbientLight(0xffffff, 0.3);
        scene.add(ambientLight);
        const pointLight = new THREE.PointLight(0xffffff, 0.8);
        pointLight.position.set(5, 5, 5);
        scene.add(pointLight);

        // 创建动画
        const animate = function () {
          requestAnimationFrame(animate);

          // 使地球自转和公转
          earth.rotation.y += 0.0006;

          renderer.render(scene, camera);
        };

        // 执行动画
        animate();
      }
  );
}
</script>

<style lang="stylus" scoped>
@import '@/assets/iconfont/iconfont.css'
.index-page {
  margin: 0
  // background-color #007bff /* 科技蓝色背景 */
  overflow hidden
  color #ffffff
  display flex
  flex-direction: column;
  justify-content center
  align-items baseline
  padding-top 60px
  
  .des1{
	  width:100%;
	  padding-bottom: 100px;
	  background-color: #fff;
	  display: flex
	  padding-left: 100px;
	  padding-right: 100px;
	  padding-top: 100px;
	  .navtitle{
	  			  margin-top: 240px
	  }
	  .labels{
		  display: flex
		  flex-direction: row
		  justify-content: center
		  align-content: center
		  .link{
		  			  font-size: 20px;
		  			  font-weight: normal;
		  			  color: #333333;
		  			  margin-top: 20px;
		  }
		  .description{
		  			  font-size: 26px;
		  			  font-weight: normal;
		  			  color: #333333;
		  			  margin-top: 15px;
		  }
		  .mt15{
		  			  margin-top: 15px;
		  }
		}
	  .left{
		  display: flex
		  flex-direction: column
		  justify-content: flex-start
		  align-content: flex-start
		  .title{
		  		  font-size: 36px;
		  		  font-weight: bold;
		  		  color: #333333;
				  margin-top: 20px;
		  }
		  .link{
			  font-size: 20px;
			  font-weight: normal;
			  color: #333333;
			  margin-top: 20px;
		  }
		  .description{
			  font-size: 26px;
			  font-weight: normal;
			  color: #333333;
			  margin-top: 15px;
			  
		  }
		  .mt15{
			  margin-top: 15px;
		  }
		  .mt35{
		  	  margin-top: 35px;
		  }
	  }
	  .right{
		  display: flex
		  flex-direction: column
		  justify-content: flex-start
		  align-content: flex-start
		  margin: 0 auto
		  .title{
		  		  font-size: 36px;
		  		  font-weight: bold;
		  		  color: #333333;
		  				  margin-top: 20px;
		  }
		  .description{
		  			  font-size: 26px;
		  			  font-weight: normal;
		  			  color: #333333;
		  			  margin-top: 15px;
		  }
		  .link{
		  			  font-size: 20px;
		  			  font-weight: normal;
		  			  color: #333333;
		  			  margin-top: 20px;
		  }
		  .mt15{
		  			  margin-top: 15px;
		  }
			.mt35{
				  margin-top: 35px;
			}
	  }
	 
  }
  
  .sec{
		  width:100%;
		  padding-bottom: 100px;
	      background-image: linear-gradient(95deg, #5261f9, #fa69e2);
		  .navtitle{
			  margin-top: 240px
		  }
		  
		  .feature{
			  display: flex
			  flex-direction: row
			  justify-content: space-between
			  align-content: center
			  margin: 80px auto
			  width: 70%
			  .item{
				  display: flex
				  flex-direction: column
				  align-content: center
				  justify-content: center
			  }
		  }
  }
  .slogan{
	  width:70%
	  text-align: center
	  margin: 80px auto
  }
  .begin{
	  background: linear-gradient(138deg, #3b2af9, #562cf7 22%, #dd34ee 89%, #f5e17d);
	  border-radius: 99px;
	  box-shadow: 0 0 4px 1px #9056ca66;
	  color: #fff;
	  font-size: 26px;
	  height:80px;
	  width:250px;
	  transition: all .3s cubic-bezier(.075,.82,.165,1);
	  span{
		  color: #fff
		  font-size: 26px
		  font-weight: bold
	  }
  }

  .menu-box {
    position absolute
    top 0
    width 100%
    display flex
	
    .el-menu {
      padding 0 30px
      width 100%
      display flex
      justify-content space-between
      background none
      border none
	  background: #fff
	  border-bottom: 1px solid #eee
      .menu-item {
        display flex
        padding 5px 0
		justify-content: center;
		align-items: center;
        color #ffffff
		
        .title {
          font-size 24px
          padding 10px 10px 0 10px
		  font-weight: normal
		  color: #333333
        }
        .el-image {
          height 50px
        }
		a:hover{
			cursor:pointer
		}
        a {
          margin-left 10px
		  font-weight: normal
          span {
            margin-left 5px
          }
        }
      }
    }
  }

  .content {
    text-align: center;
    position relative

    h1 {
      font-size: 5rem;
      margin-bottom: 1rem;
    }

    p {
      font-size: 1.5rem;
      margin-bottom: 2rem;
    }

    .el-button {
      padding: 25px 20px;
      font-size: 1.3rem;
      transition: all 0.3s ease;

      .iconfont {
        font-size 1.6rem
        margin-right 10px
      }
    }

    #animation-container {
      display flex
      justify-content center
      width 100%
      height: 300px;
      position: absolute;
      top: 350px

    }
  }

  .footer {
    .el-link__inner {
      color #ffffff
    }
  }

}
</style>
