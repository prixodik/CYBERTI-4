<template>
	<nav
		class="panel"
		ref="navBar"
		:data-nav="`${pagetitle}`"
		id="navbar"
	>
		<div
			class="panel__body"
			:class="{ active: $store.state.menuIsActive  }"
		>
			<hamburger />

			<div class="panel__title"><span>{{pagetitle}}</span></div>

			<div class="panel__soc soc-list">
				<div class="soc-list__item">
					<a href="#">
						<img
							loading="lazy"
							src="~/assets/svg/soc-1.svg"
							alt=""
						/>
					</a>
				</div>
				<div class="soc-list__item">
					<a href="#">
						<img
							loading="lazy"
							src="~/assets/svg/soc-2.svg"
							alt=""
						/>
					</a>
				</div>
				<div class="soc-list__item">
					<a href="#">
						<img
							loading="lazy"
							src="~/assets/svg/soc-3.svg"
							alt=""
						/>
					</a>
				</div>
				<div class="soc-list__item">
					<a href="#">
						<img
							loading="lazy"
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

		<transition
			name="panel-wrapper"
			key="panel-wrapper"
		>
			<div
				class="panel__wrapper"
				v-show="$store.state.menuIsActive"
			>
				<div class="panel__row row row--stretch">

					<div class="panel__col col-4 col-xs-12">
						<div class="panel__buttons">
							<a
								class="btn btn--border"
								href="#"
								@click="toggleForm()"
							>Отправить заявку</a>
							<a
								href="#"
								class="btn btn--border"
							>PDF</a>
						</div>

						<div class="panel__menu">
							<div class="panel__menu-item">
								<nuxt-link to="/services">
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

					<div class="panel__col col-4 col-xs-12">
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

					<div
						class="panel__col col-4 col-xs-12"
						v-if="showForm"
					>
						<div class="panel__form">
							<div class="panel__form-title">Заявка</div>
							<form
								action=""
								class="panel__form-form"
							>
								<div class="panel__form-item">
									<div class="panel__form-label">Имя</div>
									<input
										type="text"
										class="form-control"
									>
								</div>
								<div class="panel__form-item">
									<div class="panel__form-label">Телефон</div>
									<input
										type="text"
										class="form-control"
									>
								</div>
								<div class="panel__form-item">
									<div class="panel__form-label">E-mail</div>
									<input
										type="text"
										class="form-control"
									>
								</div>
								<div class="panel__form-buttons"><button
										class="btn btn--border"
										type="submit"
									>Отправить</button></div>
							</form>
						</div>
					</div>
				</div>
			</div>
		</transition>

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
			showForm: false,
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
		openForm() {
			this.showForm = true;
		},
		hideForm() {
			this.showForm = false;
		},
		toggleForm() {
			// Look for .hamburger
			//this.$store.commit("toggleFormState");

			if (this.showForm) {
				this.hideForm();
			} else {
				this.openForm();
			}
		},
	},
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/helpers/variables.scss";
@import "~/assets/scss/helpers/mixin.scss";

.panel {
	position: fixed;
	top: 0;
	bottom: 0;
	left: 0;
	z-index: 100;

	&__body {
		position: relative;
		z-index: 3;
		height: 100%;
		//background: $white;
		border-right: 1px rgba($black, 0.5) solid;
		@include flex(space-between, center, center, nowrap, column);
		padding: 40px 30px 26px;

		&.active {
			background: $white;

			.panel__soc {
				opacity: 1;
			}
		}
	}

	&__title {
		text-transform: uppercase;
		color: inherit;
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
		opacity: 0;
	}
	&__lang {
		margin-top: 52px;
		color: inherit;
		font: bold 24px/1 $baseFF;

		a {
			text-decoration: none;
			color: inherit;
		}
	}

	&__wrapper {
		position: absolute;
		top: 0;
		left: 100%;
		bottom: 0;
		z-index: 2;
		background: $white;
		width: calc(100vw - 100px);
		//max-width: 1200px;
		//@include time();
		//transition: all 0.4s ease;
		opacity: 1;
		pointer-events: auto;

		/* &.isOpen,
		&.is-open {
			.panel__col {
				transform: translateX(0);
			}
		} */

		&.panel-wrapper-enter {
			//transition: all 0.4s ease;
			left: 100%;
			opacity: 1;
			pointer-events: none;

			.panel__col {
				transform: translateX(-100%);
				transition: all 0.7s ease;

				&:nth-of-type(2) {
					transition-delay: 0.8s;
					transform: translateX(-200%);
				}
			}
		}
		&.panel-wrapper-enter-to {
			left: 100%;
			opacity: 1;
			pointer-events: auto;

			.panel__col {
				transform: translateX(0);

				&:nth-of-type(2) {
					transform: translateX(0);
				}
			}
		}

		// ! **** LEAVE *****
		&.panel-wrapper-leave {
			left: 100%;
			opacity: 1;
			pointer-events: auto;

			.panel__col {
				transform: translateX(0);
				transition: all 0.4s ease;
				/* 
				&:nth-of-type(1) {
					transition-delay: 4s !important;
				}
				&:nth-of-type(2) {
					transition-delay: 0 !important;
				} */
			}
		}
		&.panel-wrapper-leave-to {
			left: 100%;
			pointer-events: none;
			transition: all 0.4s ease;

			.panel__col {
				&:nth-of-type(1) {
					transform: translateX(-100%);
					transition-delay: 0.2s;
				}
				&:nth-of-type(2) {
					transform: translateX(-200%);
					transition-delay: 0s;
				}
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
		border-right: 1px rgba($black, 0.5) solid;
		@include flex(0, stretch, stretch, nowrap, column);
		transition: all 0.7s ease;
		background: $white;
		position: relative;
		z-index: 1;

		&:last-child {
			border-right: 0;
			z-index: 2;
		}

		/* &.col-2-enter {
			transition: 2s;
			transition-delay: 2s;
		}
		&.col-2-enter-to {
			transform: translateX(0);
		} */
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

	&__form {
		@include flex(space-between, stretch, stretch, nowrap, column);
		&-title {
			font: 900 78px/1 $baseFF;
			margin-bottom: 50px;
		}
		&-form {
			flex: 1 1 auto;
		}
		&-item {
			margin-bottom: 50px;
		}
		&-label {
			margin-bottom: 8px;
			font: 900 20px/1 $baseFF;
		}
		&-buttons {
			@include flex(center);
			margin-top: 50px;
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