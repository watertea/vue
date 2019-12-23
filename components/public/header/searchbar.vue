<template>
  <div class="search-panel">
    <el-row class="m-header-searchbar">
      <el-col :span="3" class="left">
        <img
          src="//s0.meituan.net/bs/fe-web-meituan/e5eeaef/img/logo.png"
          alt="美团"
        />
      </el-col>
      <el-col :span="15" class="center">
        <div class="wrapper">
          <el-input 
          v-model='search'
          placeholder="搜索商家或地点"
          @focus='handleFocus'
          @blur ='handleBlur'
          @input='handleInput'
          ></el-input>
          <button class="el-button el-button-primary">
            <i class="el-icon-search"></i>
          </button>
          <dl class="hot-search" v-if="isHotSearch">
            <dt>热门搜索</dt>
            <dd v-for='(item, index) in hotSearch' :key='index'>
              {{item}}
            </dd>
          </dl>
          <dl class="search-list" v-if="isSearchList">
            <dd v-for='(item,idx) in searchList' :key='idx'>
              {{item}}
            </dd>
          </dl>
        </div>
        <p class="suggest">
          <a href="#">故宫博物院</a>
          <a href="#">故宫博物院</a>
          <a href="#">故宫博物院</a>
          <a href="#">故宫博物院</a>
          <a href="#">故宫博物院</a>
        </p>
        <ul class="nav">
					<li>
						<nuxt-link to="/" class="takeout">美团外卖</nuxt-link>
					</li>
					<li>
						<nuxt-link to="/" class="movie">猫眼电影</nuxt-link>
					</li>
					<li>
						<nuxt-link to="/" class="hotel">美团酒店</nuxt-link>
					</li>
					<li>
						<nuxt-link to="/" class="apartment">民宿/公寓</nuxt-link>
					</li>
					<li>
						<nuxt-link to="/" class="business">商家入驻</nuxt-link>
					</li>
				</ul>
      </el-col>
      <el-col :span="6" class="right">
        <ul class="security">
          <li><i class="refund">随时退</i></li>
          <li><i class="free">不满意免单</i></li>
          <li><i class="overdue">过期退</i></li>
        </ul>
      </el-col>
    </el-row>
  </div>
</template>
<script>
export default {
    data(){
        return {
            isFocus: false,
            search: '',
            hotSearch:['欢乐谷','欢乐谷','欢乐谷','欢乐谷'],
            searchList:['颐和园','颐和园','颐和园','颐和园','颐和园']
        }
    },
    methods:{
      handleFocus(){
        this.isFocus=true
      },
     handleBlur: function() {
			let _self = this;
			setTimeout(function() {
				_self.isFocus = false;
			}, 200)
    },
    handleInput(){
      console.log('inpit')
    }
    },
    computed:{
      isHotSearch(){
        return this.isFocus && !this.search
      },
      isSearchList: function() {
        return this.isFocus && this.search
      }
    }
}
</script>