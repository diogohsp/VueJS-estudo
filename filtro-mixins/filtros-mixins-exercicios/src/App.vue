<template>
	<div id="app">
		<h1>Filtros & Mixins</h1>
		<hr>
		<p>{{ usuarioLogado}}</p>
		<p>{{ cpf | cpf | inverter}}</p>
		<input type="month" :value="cpf | cpf">
		<hr>
		<Frutas/>
		<hr>
		<div>
			<ul>
				<li v-for="fruta in frutas" :key="fruta"> {{ fruta }}</li>
				<input type="text" v-model="fruta" @keydown.enter="add">
			</ul>
		</div>
	</div>
</template>

<script>
import Frutas from './Fruta.vue'
import frutasMixin from './frutasMixin'
import usuarioMixin from './usuarioMIxin'

export default {
	components: {Frutas},
	mixins: [frutasMixin, usuarioMixin],
	filters: {
		cpf(valor){
			const arr = valor.split('')
			arr.splice(3,0,'.')
			arr.splice(7,0,'.')
			arr.splice(11,0,'-')
			return arr.join('')
		}
	},
	data() {
		return {
			cpf: '10110110108',
			frutas: ['abacate'],
		}
	},
	methods: {
        
    }
}
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
	font-size: 2.5rem;
}

input{
	font-size: 2.5rem;
}
</style>
