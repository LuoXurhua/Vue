<template>
	<div>
		<div v-if="lists.length">
			<el-row>
				<el-col :span="3"><div class="grid-content">商品信息</div></el-col>
				<el-col :span="3"><div class="grid-content">商品图片</div></el-col>
				<el-col :span="3"><div class="grid-content">尺码颜色</div></el-col>
				<el-col :span="3"><div class="grid-content">吊牌价</div></el-col>
				<el-col :span="3"><div class="grid-content">数量</div></el-col>
				<el-col :span="3"><div class="grid-content">折扣</div></el-col>
				<el-col :span="3"><div class="grid-content">总金额</div></el-col>
				<el-col :span="3"><div class="grid-content">操作</div></el-col>
			</el-row>
			<div>
				<ul>
					<li v-for="item in lists" style="overflow:hidden;display:flex;align-items:center">
						
						<el-col :span="3"><div class="grid-content"><el-checkbox v-model="checkList" :label="item.id"> {{item.name}}</el-checkbox></div></el-col>
						<el-col :span="3"><div class="grid-content" style="width:100%;display: flex;justify-content: center;align-items: center;"><img style="width:50%" :src="item.photo"></div></el-col>
						<el-col :span="3"><div class="grid-content">{{item.color}} / {{item.size}}寸</div></el-col>
						<el-col :span="3"><div class="grid-content">{{item.pirce}}</div></el-col>
						<el-col :span="3">
							<div class="grid-content">
								<el-button round @click="cutCoust(item)">-</el-button> {{item.const}} <el-button round @click="addCoust(item)">+</el-button>
							</div>
						</el-col>
						<el-col :span="3"><div class="grid-content">{{item.active}}</div></el-col>
						<el-col :span="3"><div class="grid-content">{{item.pirce * item.active * item.const}} </div></el-col>
						<el-col :span="3"><div class="grid-content"><el-button type="danger" icon="el-icon-delete" circle @click="del(item)"></el-button></div></el-col>
					</li>
				</ul>
				<el-footer>
					<el-checkbox v-model="radio" @click="selectAll">全选 {{radio}}</el-checkbox>
					<span>已选商品{{checkList.length}}件 合计{{}}元</span>
				</el-footer>
			</div>      
		</div>
		<div v-else>
			你的购物车是空的，快去逛逛吧
		</div>
	</div>
</template>

<script>
export default {
    data() {
        return {
			radio: false,
			checkList:[],
            lists:[
				{
					name:'vue',
					photo:require('./../assets/logo.png'),
					color:'Green',
					size:'21',
					pirce:'55',
					const:'2',
					active:'0.5',
					id:'1'
				},
				{
					name:'vue',
					photo:require('./../assets/logo.png'),
					color:'Yellow',
					size:'21',
					pirce:'55',
					const:'2',
					active:'0.5',
					id:'2'
				},
				{
					name:'vue',
					photo:require('./../assets/logo.png'),
					color:'Red',
					size:'21',
					pirce:'55',
					const:'2',
					active:'0.5',
					id:'3'
				},
				{
					name:'vue',
					photo:require('./../assets/logo.png'),
					color:'Red',
					size:'21',
					pirce:'55',
					const:'2',
					active:'0.5',
					id:'4'
				},
				{
					name:'vue',
					photo:require('./../assets/logo.png'),
					color:'Red',
					size:'21',
					pirce:'55',
					const:'2',
					active:'0.5',
					id:'5'
				},
				{
					name:'vue',
					photo:require('./../assets/logo.png'),
					color:'Red',
					size:'21',
					pirce:'55',
					const:'2',
					active:'0.5',
					id:'6'
				},
            ]
        }
	},
	methods: {
		cutCoust(item){
			item.const==0 ? 0 : item.const--
			
		},
		addCoust(item){
			item.const++
		},
		//实现购物车删除的原理是把数据删除了就行了，所以难点是怎么找准数据
		del(item){
			let index = this.lists.findIndex(cloth => {
				return cloth.id == item.id
			})
			console.log(index)
			this.lists.splice(index,1)
			
		},
		selectAll(){
			this.checkList
		}
	},
}
</script>

<style lang="less" scoped>


  .el-row {
    margin-bottom: 20px;
    &:last-child {
      margin-bottom: 0;
    }
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
    line-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
  .el-button+.el-button{
	  margin: 0
  }
</style>