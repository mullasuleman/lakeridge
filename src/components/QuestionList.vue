<template>
	<div id="QuestionList">
		<div class="CardView" v-if="this.viewState">
			<Information
				:mythData="mythData.data.myths[this.mythClicked]"
				:returnTo="updateViewState"
				:viewType="'browse'"
			/>
		</div>
		<div class="CardView" v-else>
			<QuestionCard
			v-for="(item) in mythData.data.myths"
			:key="item.id"
			:id="item.id"
			:art="item.art"
			:myth="item.myth_title"
			:handleClick="updateMythClicked"
		/>
		<!-- <router-link :to="{name: 'Home', props: { } }">Return to menu</router-link> -->
		</div>
	</div>

</template>

<script>
	import QuestionCard from "./QuestionCard.vue";
	import Information from "./Information";
	// v-on:click="updateMythClicked(item.id)"

	export default {
		name: "QuestionList",
		props: {
			mythData: Object
		},
		data() {
			return {
				viewState: false,
				mythClicked: 0
			};
		},
		components: {
			QuestionCard,
			Information
		},
		methods: {
			updateViewState: function() {
				this.viewState = !this.viewState;
			},
			updateMythClicked: function(id) {
				this.mythClicked = id;
				this.updateViewState();
			}
		}
	};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.CardView {
	width: 95vw;
	min-height: 82vh;
	background: #f5f5f5;
	border-radius: 10px;
	display: flex;
	flex-direction: row;
	flex-wrap: wrap;
	justify-content: center;
	align-content: center;
}
</style>
