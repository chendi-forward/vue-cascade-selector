<template>
	<div class="tiku-selector">
		<div v-for="(item, itemIndex) in showSelector" 
				class="tiku-selector-item" 
				v-show="hideItem.indexOf(itemIndex) < 0"
				:data-order="itemIndex">
			<span class="tiku-selector-name">
				{{ nameMap[itemIndex] }}
			</span>
			<span class="tiku-selector-box">
				<a v-for="target in item" 
					:class="{'tiku-selector-target': true, 'tiku-selector-current': target.current}" 
					@click="click(target.key, target.name, target.id)">
					{{ target.name }}
				</a>
			</span>
		</div>
	</div>
</template>

<script>

	import Vue from 'vue'

	export default {
		props: {
			init: {
				type: Function
			},
			handle: {
				type: Function
			}
		},
		mounted(){
			this.init(this);
		},
		data() {
            return {
				hideItem: [],
				default: {},
				options: {},
				showSelector: {},
				nameMap: {}
            }
        },
		methods: {
			click(key, value, id){

				var _key = '',
					_name = '',
					_id = undefined;

				var _this = this;

				if(!!this.showSelector[key][value].children){
					var obj = {};
					for(var ix in this.showSelector[key][value].children){

						if(!_key){
							_key = this.showSelector[key][value].children[ix].key;
							_name = this.showSelector[key][value].children[ix].name;
							_id = this.showSelector[key][value].children[ix].id;
							this.showSelector[key][value].children[ix].current = 'true';
						}
						
						var name = this.showSelector[key][value].children[ix].name;
						obj[name] = {};
						for(let o in this.showSelector[key][value].children[ix]){
							obj[name][o] = this.showSelector[key][value].children[ix][o];
						}
						obj[name].current = false;
					}

					this.$set(this.showSelector, _key, obj);
					this.click(_key, _name, _id);
				}

				for(var name in this.showSelector[key]){
					this.$set(this.showSelector[key][name], 'current', false);
				}
				
				this.$set(this.showSelector[key][value], 'current', true);

				if(id) {
					this.handle(id);
				}
			}
		}
	}
</script>

<style>
	.tiku-selector-item {
		font-size: 13px;
		padding: 0px 0px;
		border-bottom: 2px dashed #e5e5e5;
	}
	.tiku-selector-item:last-child{
		border-bottom:none;
	}
	.tiku-selector-target {
		margin-right: 30px;
		padding: 3px 3px;
		cursor: pointer;
		display: inline-block;
		margin-bottom: 10px;
	}

	.tiku-selector-current {
		background-color: #f7be38;
		color: white;
		border-radius: 5px;
	}

	.tiku-selector-name {
		display: inline-block;
		width: 80px;
		margin-top: 13px;
	}

	.tiku-selector-box {
		display: inline-block;
		width: 80%;
		vertical-align: top;
		margin-top: 9px;
	}
</style>
