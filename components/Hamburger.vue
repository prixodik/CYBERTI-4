<template>
	<div
		@click="toggle"
		class="hamburger hamburger--spin js-hamburger"
		:class="{'is-active': $store.state.menuIsActive }"
	>
		<div class="hamburger-box">
			<div class="hamburger-inner"></div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			isOpen: false,
		};
	},
	computed: {},
	methods: {
		open() {
			this.isOpen = true;
		},
		close() {
			this.isOpen = false;
		},
		toggle() {
			// Look for .hamburger
			this.$store.commit("toggleMenuState");

			//var hamburger = document.querySelector(".hamburger");
			// On click

			// Toggle class "is-active"

			if (this.isOpen) {
				this.close();
			} else {
				this.open();
			}
		},
	},
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/helpers/variables.scss";
@import "~/assets/scss/helpers/mixin.scss";

.hamburger {
	display: block;
	cursor: pointer;
	transition-property: opacity, filter;
	transition-duration: 0.15s;
	transition-timing-function: linear;
	font: inherit;
	color: inherit;
	text-transform: none;
	background-color: transparent;
	border: 0;
	margin: 0;
	overflow: visible;
}
/* .hamburger:hover {
	.hamburger-inner,
	.hamburger-inner::before,
	.hamburger-inner::after {
		background: $blue;
	}
} */

.hamburger-box {
	width: 40px;
	height: 26px;
	display: inline-block;
	position: relative;
}

.hamburger-inner {
	display: block;
	top: 50%;
	margin-top: -2px;
}
.hamburger-inner,
.hamburger-inner::before,
.hamburger-inner::after {
	width: 40px;
	height: 4px;
	background-color: $black;
	border-radius: 10px;
	position: absolute;
	transition-property: transform;
	transition-duration: 0.15s;
	transition-timing-function: ease;
}
.hamburger-inner::before,
.hamburger-inner::after {
	content: "";
	display: block;
}
.hamburger-inner::before {
	top: -10px;
}
.hamburger-inner::after {
	bottom: -10px;
}

.hamburger--spin .hamburger-inner {
	transition-duration: 0.22s;
	transition-timing-function: cubic-bezier(0.55, 0.055, 0.675, 0.19);
}
.hamburger--spin .hamburger-inner::before {
	transition: top 0.1s 0.25s ease-in, opacity 0.1s ease-in;
}
.hamburger--spin .hamburger-inner::after {
	transition: bottom 0.1s 0.25s ease-in,
		transform 0.22s cubic-bezier(0.55, 0.055, 0.675, 0.19);
}

.hamburger--spin.is-active .hamburger-inner {
	transform: rotate(225deg);
	transition-delay: 0.12s;
	transition-timing-function: cubic-bezier(0.215, 0.61, 0.355, 1);
}
.hamburger--spin.is-active .hamburger-inner::before {
	top: 0;
	opacity: 0;
	transition: top 0.1s ease-out, opacity 0.1s 0.12s ease-out;
}
.hamburger--spin.is-active .hamburger-inner::after {
	bottom: 0;
	transform: rotate(-90deg);
	transition: bottom 0.1s ease-out,
		transform 0.22s 0.12s cubic-bezier(0.215, 0.61, 0.355, 1);
}
</style>