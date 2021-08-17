<template>
	<MainHeader/>
	<Promo/>
	<Pocket
	:totalCoinsMain="totalCoins"
	:arrayOfCoins="arrayOfTotalCoinsIcon"
	:farmCoin="addTotalCoin"
	@changeCheckboxState="changeCheckboxState"
	/>
	<Market
	:totalCoins="totalCoins"
	:numOfBiomech="numOfBiomech"
	:numOfProc="numOfProc"
	:numOfSoul="numOfSoul"
	@buyDetail="buyDetail"
	/>
	<Store
	:numOfBiomech="numOfBiomech"
	:numOfProc="numOfProc"
	:numOfSoul="numOfSoul"
	@sellDetail="sellDetail"
	/>
</template>

<script>

import MainHeader from './Components/MainHeader/MainHeader.vue';
import Promo from './Components/Promo/Promo.vue';
import Pocket from './Components/Pocket/Pocket.vue';
import Market from './Components/Market/Market.vue'
import Store from './Components/Store/Store.vue'

export default {
	components: {
		MainHeader, Promo, Pocket, Market, Store
	},
	data() {
		return {
			totalCoins: 0,
			maxTotalCoins: 100,
			arrayOfTotalCoinsIcon: [],
			checkboxState: false,

			numOfBiomech: 0,
			numOfProc: 0,
			numOfSoul: 0,
		}
	},
	methods: {
		showCoinsIcon() {
			this.arrayOfTotalCoinsIcon = [];
			for (let i = 0; i < this.totalCoins; i++) {
				this.arrayOfTotalCoinsIcon.push(i);
			}
		},
		checkMaxTotalCoins() {
			if (this.totalCoins > this.maxTotalCoins) {
					alert(`Макисмальное количество монет ${this.maxTotalCoins}`);
					this.totalCoins = this.maxTotalCoins;
				}
		},
		changeCheckboxState(status) {
			this.checkboxState = status;
			console.log(this.checkboxState)
		},
		addTotalCoin() {
			if (this.checkboxState) {
				this.totalCoins += 50;
			} else if (!this.checkboxState){
				this.totalCoins += 1;
			}
			this.checkMaxTotalCoins();
			this.showCoinsIcon();
		},
		buyDetail(name, detailCost) {
			if (detailCost <= this.totalCoins) {
				if (name === 'biomech') {
				this.numOfBiomech++;
				this.checkMaxTotalCoins();
				this.totalCoins -= detailCost
				this.showCoinsIcon();
			} else if (name === 'proc') {
					this.numOfProc++;
					this.checkMaxTotalCoins();
					this.totalCoins -= detailCost
					this.showCoinsIcon();
			} else if (name === 'soul') {
					this.numOfSoul++;
					this.checkMaxTotalCoins();
					this.totalCoins -= detailCost
					this.showCoinsIcon();
				}
			}
		},
		sellDetail(name, detailCost) {
			if (name === 'biomech') {
				if (this.numOfBiomech > 0) {
					this.numOfBiomech--;
					this.totalCoins += detailCost;
					this.checkMaxTotalCoins();
					this.showCoinsIcon();
				}
			} else if (name === 'proc') {
				if (this.numOfProc > 0) {
					this.numOfProc--;
					this.totalCoins += detailCost;
					this.checkMaxTotalCoins();
					this.showCoinsIcon();
				} 
			} else if (name === 'soul') {
				if (this.numOfSoul > 0) {
					this.numOfSoul--;
					this.totalCoins += detailCost;
					this.checkMaxTotalCoins();
					this.showCoinsIcon();
				}
			}
		}
	}
}
</script>
