<template>
	<section class="m-has-style">
		<dl @mouseover="handleOver">
			<dt>有格调</dt>
			<dd 
				:class="{active:kind==='all'}"
				kind="all"
				keyword="景点">
				全部
			</dd>
			<dd 
				:class="{active:kind==='date'}"
				kind="date"
				keyword="美食">
				约会聚餐
			</dd>
			<dd 
				:class="{active:kind==='spa'}"
				kind="spa"
				keyword="丽人">
				丽人SPA
			</dd>
			<dd 
				:class="{active:kind==='movie'}"
				kind="movie"
				keyword="电影">
				电影演出
			</dd>
			<dd 
				:class="{active:kind==='travel'}"
				kind="travel"
				keyword="旅游">
				品质出游
			</dd>
		</dl>
		<ul class="has-style-body">
			<li 
				v-for="item in curList" 
				:key="item.title">
				<el-card 
					:body-style="{ padding: '0px' }"
					shadow="never">
					<img :src="item.img"
								class="image" />
					<ul class="content-body">
						<li class="title">{{ item.title }}</li>
						<li class="pos"><span>{{ item.pos }}</span></li>
						<li class="price">￥<em>{{ item.price }}</em><span>/起</span></li>
					</ul>
				</el-card>
			</li>
		</ul>
	</section>
</template>

<script>
export default {
	data() {
		return {
			kind: 'all',
			list: {
				all: [
                    {
                        img:'',
                        title:'大董（）',
                        pos:'王府',
                        price:'124'
                    },
                    {
                        img:'22',
                        title:'22大董（）',
                        pos:'王府',
                        price:'124'
                    }
                ],
				date: [
                    {
                        img:'',
                        title:'1大董（）',
                        pos:'王府',
                        price:'124'
                    }
                ],
				spa: [
                    {
                        img:'',
                        title:'2大董（）',
                        pos:'王府',
                        price:'124'
                    }
                ],
				movie: [
                    {
                        img:'',
                        title:'3大董（）',
                        pos:'王府',
                        price:'124'
                    }
                ],
				travel: [
                    {
                        img:'',
                        title:'5大董（）',
                        pos:'王府',
                        price:'124'
                    }
                ]
			}
		}
	},
	computed: {
		curList: function() {
			return this.list[this.kind]
		}
	},
	methods: {
		handleOver: async function(e) {
			let dom = e.target;
			let tag = dom.tagName.toLowerCase();
			if (tag === 'dd') {
				this.kind = dom.getAttribute('kind');
			}
		}
	}
}
</script>

<style lang="scss">
@import "@/assets/css/index/hasStyle.scss";
</style>