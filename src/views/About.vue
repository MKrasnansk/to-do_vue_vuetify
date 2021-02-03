<template>
	<div class="about pa-6">
		<h1>About {{ $store.state.appTitle }}</h1>
		<p>
			Táto aplikácia slúži na organizovanie a plánovanie
			Vášho času a úloh. <br />
			Ak máte dalšie nápady na zlepšenie aplikácie neváhajte
			ma kontaktovať. <br />
			Dúfam že budete spokojný. <br />
			<strong>Ďakujem!</strong>
		</p>
		<ul>
			<li>Stranka vytvorena: Február 2021</li>
			<li>Autor: Michal Krasňanský</li>
			<li>Framework: Vue.js</li>
			<li>
				knižnice: Vuetify, vuedraggable, date-fns a
				localbase
			</li>
		</ul>

		<h3>Kontakt</h3>
		<ul>
			<li>Michal Krasňanský</li>
			<li>miso.krasnansky@gmail.com</li>
		</ul>
	</div>
</template>
<style lang="scss" scoped>
.about {
	text-align: center;
	ul {
		margin: 1em;
		padding-left: 0;
		list-style: none;
	}
}
</style>
