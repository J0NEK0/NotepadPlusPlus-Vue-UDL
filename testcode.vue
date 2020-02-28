<template v-if="loginType === 'username'">
	<h1>Heading</h1>
	<label>Username</label>
	<input placeholder="Enter your username" key="username-input">
</template>
<template v-else>
	<b-container fluid>
		<b-row class="my-1" v-for="type in content" :key="type">
			<b-col sm="3">
				<label :for="`type-${type}`">Type <code>{{ type }}</code>:</label>
			</b-col>
			<b-col sm="9">
				<b-form-input :id="`type-${type}`" :type="type"></b-form-input>
			</b-col>
		</b-row>
	</b-container>
</template>

<script>
	import OtherComponent from './components/OtherComponent.vue';
	
    export default {
		data () {
			return {
				key: "value",
				someNumber: 324.44,
				working: false,
				p: "Some text with a number: 32"
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
		propsData: {
			title: "Testing tiral",
			content: [1,"hex"],
			label: "<code> return null </code>"
		},
		computed: {
			sqrtNumber: function() {
				return Math.sqrt(this.someNumber);
			},
			listeners () {
				return {
					this.$listeners,
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
				// .foldStart DOM
				let node = document.createElement("DIV");
				// .fS
				node.innerHTML = "<b>some bold text</b>";
				// .fE
				document.getElementsByClassName("some-class")[0].appendChild(node);
				//.foldEnd
				let array = new Array();
				
				/** .fS
					comment
				*/
				let number = new Number();
				if (isNaN(number))
					throw("number is NaN");
				number <<= 3;
				number **= 4;
				/* .fE */
				let str = new String();
			}
		},
		watch: {
			key: function (val, oldVal) {
				console.log('new: %s, old: %s', val, oldVal);
			}
		}
    }
</script>

<style scoped>
    div {
        display: inline-block;
        margin: 2px;
    }
	
    span {
        font-family: monospace;
    }
	
    #some-id {
        text-decoration: line-through
    }
	
	.some-class:first-child {
		background-color: #FA900E;
	}
	
	.b-button {
		color: #123456;
	}
	
</style>