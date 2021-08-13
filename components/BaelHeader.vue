<template>
	<nav
		class="panel"
		ref="navBar"
		:data-nav="`${pagetitle}`"
		id="navbar"
	>
		<div class="panel__body">
			<hamburger />

			<div class="panel__title"><span>{{pagetitle}}</span></div>

			<div class="panel__soc soc-list">
				<div class="soc-list__item">
					<a href="#">
						<img
							src="~/assets/svg/soc-1.svg"
							alt=""
						/>
					</a>
				</div>
				<div class="soc-list__item">
					<a href="#">
						<img
							src="~/assets/svg/soc-2.svg"
							alt=""
						/>
					</a>
				</div>
				<div class="soc-list__item">
					<a href="#">
						<img
							src="~/assets/svg/soc-3.svg"
							alt=""
						/>
					</a>
				</div>
				<div class="soc-list__item">
					<a href="#">
						<img
							src="~/assets/svg/soc-4.svg"
							alt=""
						/>
					</a>
				</div>
			</div>

			<div class="panel__lang">
				<a href="#">RU</a>
			</div>
		</div>
		<div
			class="panel__wrapper"
			v-show="$store.state.menuIsActive"
		>
			<div class="panel__row row row--stretch">
				<transition name="col-1">
					<div class="panel__col col-6 col-xs-12">
						<div class="panel__buttons">
							<nuxt-link
								class="btn btn--border"
								to="/categories"
								exact
							>Отправить заявку</nuxt-link>
							<a
								href="#"
								class="btn btn--border"
							>PDF</a>
						</div>

						<div class="panel__menu">
							<div class="panel__menu-item">
								<nuxt-link to="/">
									<span class="panel__menu-title">Услуги</span>
									<span class="panel__menu-desc">что мы можем</span>
								</nuxt-link>
							</div>
							<div class="panel__menu-item">
								<nuxt-link to="/">
									<span class="panel__menu-title">Кейсы</span>
									<span class="panel__menu-desc">что мы создаём</span>
								</nuxt-link>
							</div>
							<div class="panel__menu-item">
								<nuxt-link to="/">
									<span class="panel__menu-title">О нас</span>
									<span class="panel__menu-desc">подробнее</span>
								</nuxt-link>
							</div>
							<div class="panel__menu-item">
								<nuxt-link to="/">
									<span class="panel__menu-title">Блог</span>
									<span class="panel__menu-desc">о чем рассказываем</span>
								</nuxt-link>
							</div>
							<div class="panel__menu-item">
								<nuxt-link to="/">
									<span class="panel__menu-title">Контакты</span>
									<span class="panel__menu-desc">где нас найти</span>
								</nuxt-link>
							</div>
						</div>
					</div>
				</transition>
				<transition name="col-2">
					<div class="panel__col col-6 col-xs-12">
						<div class="panel__contacts row">
							<div class="panel__contacts-item col-6 col-xs-12">
								<div class="panel__contacts-label">Написать</div>
								<a
									href="#"
									class="panel__contacts-value"
								>cyberti@gmail.com</a>
							</div>
							<div class="panel__contacts-item col-6 col-xs-12">
								<div class="panel__contacts-label">Позвонить</div>
								<a
									href="tel:+7-911-911-91-11"
									class="panel__contacts-value"
								>+7-911-911-91-11</a>
							</div>
						</div>
						<div class="panel__about">
							<div class="panel__about-title">CYBERTi</div>
							<div class="panel__about-slogan">управляй будущим</div>
							<div class="panel__about-text">
								<p>Разнообразный и богатый опыт постоянный количественный рост и сфера нашей активности обеспечивает актуальность ключевых компонентов планируемого обновления! С другой стороны повышение уровня гражданского сознания играет важную роль в формировании дальнейших направлений развития проекта. Не следует, однако, забывать о том, что новая модель организационной деятельности играет важную роль в формировании системы масштабного изменения ряда параметров?</p>
								<p>Соображения высшего порядка, а также реализация намеченного плана развития позволяет выполнить важнейшие задания по разработке дальнейших направлений развитая системы массового участия.</p>
								<p>направлений развития проекта. Не следует, однако, забывать о том, что новая модель организационной деятельности играет важную роль в формировании системы масштабного изменения ряда параметров?важную роль в формировании дальнейших</p>
							</div>
						</div>
					</div>
				</transition>
			</div>
		</div>

		<!-- <div class="r xs-border-bottom">
			<div class="c-4 xs-text-left xs-p2 sm-border-right">
				<div class="item">
					<nuxt-link
						class="sitename"
						to="/"
						exact
					>{{$store.state.info.sitename}}</nuxt-link>
				</div>
			</div>

			<div class="c-4 xs-border-top xs-border-bottom sm-border-bottom-none sm-border-top-none sm-border-left-none sm-border-right xs-p2">
				<div class="item xs-flex">
					<lazy-bael-search />
				</div>
			</div>
			<div
				v-if="pagetitle"
				style="z-index:55;"
				class="c-12 sm-border-top xs-p2 xs-text-6 titlebar"
			>
				<div class="item">
					<nuxt-link
						to="/"
						exact
					>Home</nuxt-link>
					<span v-if="path">
						&nbsp;
						<span class="text-gray-lightest">></span>
						&nbsp; {{path}}
					</span> &nbsp;
					<span class="text-gray-lightest">></span>
					&nbsp; {{pagetitle}}
				</div>
			</div>
		</div> -->
	</nav>
</template>
<script>
import _capitalize from "lodash/capitalize";
import Hamburger from "~/components/Hamburger.vue";
export default {
	components: { Hamburger },
	data() {
		return {
			//isOpen: false,
		};
	},
	computed: {
		pagetitle() {
			return this.$store.state.current.title;
		},

		path() {
			const split = _get(this.$store, "state.current.dir").split("/");

			return split.length && split[1] !== "page" ? _capitalize(split[1]) : null;
		},
	},
	methods: {
		/* open() {
			this.isOpen = true;
		},
		close() {
			this.isOpen = false;
		},
		toggle() {
			// Look for .hamburger
			this.$store.commit("toggleMenuState");

			var hamburger = document.querySelector(".hamburger");
			// On click

			// Toggle class "is-active"

			if (this.isOpen) {
				this.close();
			} else {
				this.open();
			}
		}, */
	},
};
</script>

<style lang="scss">
@import "~/assets/scss/styles.scss";

.panel {
	position: fixed;
	background: $white;
	top: 0;
	bottom: 0;
	left: 0;
	z-index: 100;

	&__body {
		position: relative;
		z-index: 3;
		height: 100%;
		background: $white;
		border-right: 1px rgba($black, 0.5) solid;
		@include flex(space-between, center, center, nowrap, column);
		padding: 40px 30px 26px;
	}

	&__title {
		text-transform: uppercase;
		color: $black;
		flex: 1 1 auto;
		font: bold 24px/1 $baseFF;
		@include flex(center, center, center, nowrap);

		span {
			display: block;
			writing-mode: tb-rl;
			transform: rotate(180deg);
		}
	}
	&__soc {
	}
	&__lang {
		margin-top: 52px;
		color: $black;
		font: bold 24px/1 $baseFF;

		a {
			text-decoration: none;
		}
	}

	&__wrapper {
		position: absolute;
		top: 0;
		left: 100%;
		bottom: 0;
		z-index: 2;
		background: $white;
		width: 100vw;
		max-width: 1200px;
		//@include time();
		opacity: 1;
		//pointer-events: none;

		&.isOpen,
		&.is-open {
			left: 100%;
			opacity: 1;
			pointer-events: auto;

			.panel__col {
				transform: translateX(0);
			}
		}
	}
	&__buttons {
		@include flex();
		margin-right: -40px;

		.btn {
			margin: 0 40px 40px 0;
		}
	}
	&__row {
		height: 100%;
		margin: 0;
	}
	&__col {
		padding: 60px 90px;
		border-left: 1px rgba($black, 0.5) solid;
		@include flex(0, stretch, stretch, nowrap, column);
		transform: translateX(-50%);
		@include time();

		&:first-child {
			border-left: 0;
		}
	}

	&__menu {
		flex: 1 1 auto;
		@include flex(center, stretch, stretch, nowrap, column);
		&-item {
			color: $black;
			margin-bottom: 30px;
			&:last-child {
				margin-bottom: 0;
			}
		}
		&-title {
			font: 900 78px/1 $baseFF;
			display: block;
		}
		&-desc {
			font: 20px/1 $baseFF;
			display: block;
		}
	}

	&__contacts {
		&-item {
			font: 20px/1.4 $baseFF;
		}
		&-label {
			font-weight: 500;
		}
	}

	&__about {
		flex: 1 1 auto;
		@include flex(center, stretch, stretch, nowrap, column);
		&-title {
			font: 900 45px/1 $baseFF;
			margin: 0;
		}
		&-slogan {
			font: 20px/1 $baseFF;
		}
		&-text {
			margin-top: 70px;
			color: #8a8a8a;
			font: 18px/1.2 $baseFF;

			p {
				margin-bottom: 20px;
				&:last-child {
					margin-bottom: 0;
				}
			}
		}
	}
}

.soc-list {
	&__item {
		margin-bottom: 34px;
		&:last-child {
			margin-bottom: 0;
		}

		img {
			display: block;
		}
	}
}
</style>