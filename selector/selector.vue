<template>
<div :class="['selector', {'act': optionShow}]" @click="selectorClick">
	<h2 v-if="value.option">{{value.option[value.selected].text}}</h2>
	<transition name="option">
		<ul class="selector-option" v-show="optionShow">
			<li v-for="(item, index) in value.option" @click="optionClick(index)">{{item.text}}</li>
		</ul>
	</transition>
</div>
</template>


<script>
export default {
	name: 'selector',
	data() {
		return {
			optionShow: false
		}
	},
	props: {
		value: {
			type: Object,
			default: {
				selected: 0,
				option: []
			}
		}
	},
	methods: {
		selectorClick() {
			this.optionShow = !this.optionShow;
		},
		optionClick(index) {
			this.value.selected = index;
			this.$emit('input', this.value)
		}
	}
}
</script>


<style scoped>
.selector{position:relative; box-sizing:border-box; width:100%; height:100%; padding:10px; border-radius:4px; border:1px solid #ddd; line-height:22px;}
.selector:before{content:''; position:absolute; top:50%; right:15px; width:6px; height:6px; border-right:1px solid #999; border-bottom:1px solid #999; -webkit-transform:translateY(-50%) rotate(45deg); -moz-transform:translateY(-5px) rotate(45deg); transform:translateY(-5px) rotate(45deg); -webkit-transition:.2s; transition:.2s;}
.selector.act:before{-webkit-transform:translateY(-2px) rotate(-135deg); transform:translateY(-2px) rotate(-135deg);}
.selector h2{line-height:22px;}
.selector-option{position:absolute; top:100%; left:0; z-index:2; width:100%; max-height:276px; margin-top:3px; border-radius:4px; box-shadow:0 0 0 1px #ddd; background:#fff; overflow:auto; -webkit-transition:.2s; transition:.2s;}
.selector-option li{height:52px; padding:0 15px; border-bottom:1px solid #ddd; line-height:52px; -webkit-user-select:none;}
.selector-option li:last-of-type{border-bottom:0;}
.selector-option li:active{background:#eee;}

.option-enter,
.option-leave-active{opacity:0; -webkit-transform:translate3d(0,-10px,0); transform:translate3d(0,-10px,0);}
</style>
