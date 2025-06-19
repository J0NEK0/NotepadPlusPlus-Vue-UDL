<style scoped>
	html {
		color: #0000FF; !important
	}
	
	#div {
		font-weight: bold;
	}

	.div::after {
		content: "+1";
		color: rgb(255, 0, 128);
	}
	
	p[lang="en"] > span:first-of-type{
		border: 10px medium 0.75em 2ex dotted black #0FAC32;
	}
	
	/* disable nesting of Keywords 7 inside Delimiter 1 to disable highlightings like v-if */
	.example[v-if$="true"]::before {
		color: green;
	}
	
	@media only screen and (max-width: 600px) {
		body {
			background-color: gray;
		}
	}
	
	@keyframes anim {
		0%   {top: 0px;}
		50%  {top: calc(100% / 2);}
		100% {top: 0px;}
	}
	
</style>

<template>
	<div id="app">
		<button @click="count++">
			Count is: {{ count }}
		</button>
		<h1 class="class">Heading with v-if and a div tag as well as href attribute</h1>
		<label>Username</label>		<!-- Comment in HTML -->
		<input id="input-1" placeholder="Enter your username" key="username-input">
		
		<div v-for="(item, index) in items">
			{{ item.text }}
		</div>
		<form @submit.prevent="onSubmit">...</form>
		
		<img :src="'/path/to/images/' + fileName" />
		<div v-if="Math.random() > 0.5">
			Now you see me
		</div>
		<div v-else>
			Now you don't
		</div>
		<class h1="h1" data-custom="1234" disabled> Something is wrong here... </class h1="h2">
	</div>
</template>

/* Composition API */
<script setup>
	import { ref, computed } from 'vue'
	const greeting = ref('Hello World!')
	
	const firstLetterUp = computed({
		get: () => keywords.value = keywords.split(" ").map(x => x[0].toUpperCase() + x.slice(1)).join(" "),
		set: (keywords) => {
			keywords.value = keywords
		}
	})
	
	class ClassWithPrivate {
	
		static #privateStaticFieldWithInitializer = 42;
		
		static deduplicate(keywords) {
			return Array.from(new Set(keywords.split(" "))).sort().join(" ");
		}
		
		constructor(a) {
			this.a = a;
		}
	}
	
	const x         = 0xFF * 0b10 * 3.14 + 0o2;	// ok -> ok
	const bigIntDec = 123456789123456789n;			// ok -> not supported
	const bigIntOct = 0o777777777777n;					// number not recognized -> not supported
	const bigIntHex = 0x123456789ABCDEFn;				// number not recognized -> not supported
	const bigIntBin = 0b11101001010101010101n;	// number not recognized -> not supported
	const numExp    = 5e-2;											// only partly highlighted -> not supported
	const num2Exp   = 5e+2;											// ok -> not supported
	const numExp2   = 1E4;											// ok -> not supported
	const mean      = (numExp + numExp2) / 2;		// ok -> ok(ish)
</script>

/* Options API */
<script setup>
	import OtherComponent from './components/OtherComponent.vue';
	export default {
		data () {
			return {
				key: "value",
				someNumber: 324.44,
				working: false,
				p: "Some text with a number: 32",
				color: "#AAFFEE"
			}
		},
		components: {
			OtherComponent 
		},
		props: {
			title: String,
			content: Object | Array,
			label: { type: String, required: false }
		},
		computed: {
			sqrtNumber: function() {
				return Math.sqrt(this.someNumber);
			},
			listeners () {
				return {
					input: event => this.$emit('input', event.target.value)
				}
			}
		},
		methods: {
			incrNumber: function() {
				this.someNumber++;
			},
			foo: function() {
				if(true != false && 2|3)
					return null;
				for(let i = 0; i < 10; i++) {
					if(i<2||i>5)
						console.log("Number: " + this.someNumber);
					if(i > 10)
						throw("Something is not right...");
				}
				alert("HEY");
				// .fS DOM
				let node = document.createElement("DIV");
				node.innerHTML = "<b>some bold text</b>";
				document.getElementsByClassName("some-class")[0].appendChild(node);
				//.foldEnd
		
				let number = new Number(); // {
				if (isNaN(number))
					throw("number is NaN");	// }{
				number <<= 3;
				number **= 4;	// }
				
				const templateString = `x is ${x}!`;
				const obj = {
					a: "text",
					a2: 13
				}
			}
		},
		watch: {
			key: function (val, oldVal) {
				console.log('new: %s, old: %s', val, oldVal);
			}
		}
	}
		
</script>


const x         = 0xFF * 0b10 * 3.14 + 0o2;	// ok -> ok
const bigIntDec = 123456789123456789n;			// ok -> not supported
const bigIntOct = 0o777777777777n;					// number not recognized -> not supported
const bigIntHex = 0x123456789ABCDEFn;				// number not recognized -> not supported
const bigIntBin = 0b11101001010101010101n;	// number not recognized -> not supported
const numExp    = 5e-2;											// only partly highlighted -> not supported
const num2Exp   = 5e+2;											// ok -> not supported
const numExp2   = 1E4;											// ok -> not supported
const mean      = (numExp + numExp2) / 2;		// ok -> ok


