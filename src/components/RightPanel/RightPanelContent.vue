<template>
	<div class="search">
		<label for="search" class="search__label text--white bg--black">
			<h3 class="search__label--text">E.g.: Charizard | 6</h3>
			<input 
			id="search" 
			v-model.trim="name"
			type="text" 
			class="search__input"
			@keyup.enter="searchPokemon"
			>
		</label>

		<div class="buttons">
			<button class="btn btn--clear search__button " @click.prevent="clear">Clear</button>
			<button class="btn btn-search search__button bg--gray text--yellow" @click.prevent="searchPokemon">Search</button>

		</div>

	</div>
</template>

<script>
import { actions, mutations} from '@/store'
	export default {
		name: 'RightPanelContent',
		data() {
			return {
				name: '',
			};
		},
		methods: {
			clear() {
				this.name = '';
				mutations.resetList();
			},
			async searchPokemon(){
				await actions.searchPokemon(this.name);
			},
		},
	};
</script>

<style lang="scss" scoped>
	.search {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		flex: 1;
		transform: rotateX(-180deg);
		@media (min-width: $viewport-medium) {
			transform: rotateY(-180deg);
			padding-top: 20px;
		}
		&__label {
			display: flex;
			flex-direction: column;
			justify-content: space-between;
			width: 100%;
			
			padding: 6px 12px 192px;
			@media (min-width: $viewport-medium) {
				height: 36%;
				padding: 12px 24px 224px;
			}
		}
		&__input {
			color: inherit;
			background: transparent;
			border: none;
			border-bottom: 2px solid color(white);
			padding: 4px 8px;
			@media (min-width: $viewport-medium) {
				padding: 8px;
			}
		}
	.buttons {
		display: flex;
		justify-content: flex-end;
		align-items: center;
		margin-top: 3cm;

	.btn {
		border-radius: 8px;
		font-size: 22px;
		font-weight: bold;
		cursor: pointer;
		margin: 10px;		

		&--search {
			width: 120px;
			padding: 18px 8px 8px;
			border: 4px solid color(black);

			@media (min-width: $viewport-medium) {
				width: 160px;
				
				


				
		}
	}
}

}
	}
	
</style>