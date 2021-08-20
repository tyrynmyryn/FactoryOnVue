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
	<Production
	:numOfBiomech="numOfBiomech"
	:numOfProc="numOfProc"
	:numOfSoul="numOfSoul"
	@detailsAfterInstall="detailsAfterInstall"
	@resetActiveDetails="resetActiveDetails"
	:totalCoins="totalCoins"
	/>
</template>

<script>

import MainHeader from './Components/MainHeader/MainHeader.vue';
import Promo from './Components/Promo/Promo.vue';
import Pocket from './Components/Pocket/Pocket.vue';
import Market from './Components/Market/Market.vue'
import Store from './Components/Store/Store.vue'
import Production from './Components/Production/Production.vue'

export default {
	components: {
		MainHeader, Promo, Pocket, Market, Store, Production
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

			installBiomech: 0,
            installProc: 0,
            installSoul: 0
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
				this.checkStateDetailAfterBuy('.prod__biomech', 'prod__biomech_none', 'prod__biomech_available', this.numOfBiomech, 'prod__biomech_active', this.installBiomech, 4)
			} else if (name === 'proc') {
					this.numOfProc++;
					this.checkMaxTotalCoins();
					this.totalCoins -= detailCost
					this.showCoinsIcon();
					this.checkStateDetailAfterBuy('.prod__proc', 'prod__proc_none', 'prod__proc_available', this.numOfProc, 'prod__proc_active', this.installProc, 4)
			} else if (name === 'soul') {
					this.numOfSoul++;
					this.checkMaxTotalCoins();
					this.totalCoins -= detailCost
					this.showCoinsIcon();
					this.checkStateDetailAfterBuy('.prod__soul', 'prod__soul_none', 'prod__soul_available', this.numOfSoul, 'prod__soul_active', this.installSoul, 1)
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
					this.checkStateDetailAfterSell('.prod__biomech', 'prod__biomech_none', 'prod__biomech_available', this.numOfBiomech, this.installBiomech, 4)
				}
			} else if (name === 'proc') {
				if (this.numOfProc > 0) {
					this.numOfProc--;
					this.totalCoins += detailCost;
					this.checkMaxTotalCoins();
					this.showCoinsIcon();
					this.checkStateDetailAfterSell('.prod__proc', 'prod__proc_none', 'prod__proc_available', this.numOfProc, this.installProc, 4)
				} 
			} else if (name === 'soul') {
				if (this.numOfSoul > 0) {
					this.numOfSoul--;
					this.totalCoins += detailCost;
					this.checkMaxTotalCoins();
					this.showCoinsIcon();
					this.checkStateDetailAfterSell('.prod__soul', 'prod__soul_none', 'prod__soul_available', this.numOfSoul, this.installSoul, 1)
				}
			}
		},
		detailsAfterInstall(proc, biomech, soul, installProc, installBiomech, installSoul) {
			this.numOfProc += proc
			this.numOfBiomech += biomech
			this.numOfSoul += soul

            this.installProc = installProc
			this.installBiomech = installBiomech
            this.installSoul = installSoul
		},
		checkStateDetailAfterBuy(containerName, noneDetail, availableDetail, numOfDetal, activeDetail, numOfInstallDetail, iterator) {
			const container = document.querySelectorAll(containerName)
			// if (numOfDetal + numOfInstallDetail <= iterator) {
				for (let i = 0; i < iterator; i++) {
					if (container[i].classList.contains(noneDetail) && !container[i].classList.contains(activeDetail) && !container[i].classList.contains(availableDetail)) {
						container[i].classList.add(availableDetail)
					break
				}
				}
			// }
		},
		checkStateDetailAfterSell(containerName, noneDetail, availableDetail, numOfDetail, numOfInstallDetail, iterator) {
			const container = document.querySelectorAll(containerName)
				for (let i = 0; i < iterator; i++) {
				if (container[i].classList.contains(availableDetail) && numOfDetail < iterator) {
					container[i].classList.remove(availableDetail)
					container[i].classList.add(noneDetail)
					break
				}
			}
		},
		resetActiveDetails(creationCost) {
			this.totalCoins += creationCost;
			this.showCoinsIcon();
		}
	}
}
</script>
