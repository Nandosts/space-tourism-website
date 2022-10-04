<script lang="ts">
	import Logo from '../../../assets/shared/logo.svg';

	let sidebarDisplayed = false;
	function toggleSidebar() {
		sidebarDisplayed = !sidebarDisplayed;
	}
</script>

<div class="nav-container">
	<nav class="navbar">
		<img class="nav-logo" src={Logo} alt="Logo" />
		<span class="pseudo" />
		<div class="nav-items global-nav-text">
			<a href="." class="nav-item">
				<span class="bold">00</span> HOME
			</a>
			<a href="Destination" class="nav-item">
				<span class="bold">01</span> DESTINATION
			</a>
			<a href="/Crew" class="nav-item">
				<span class="bold">02 </span> CREW
			</a>
			<a href="." class="nav-item">
				<span class="bold">03</span> TECHNOLOGY
			</a>
		</div>
		<div class="sidebar-hamburger" on:click={toggleSidebar}>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				width="24"
				height="24"
				viewBox="0 0 24 24"
				fill="none"
				stroke="currentColor"
				stroke-width="2"
				stroke-linecap="round"
				stroke-linejoin="round"
			>
				<line class="top" x1="3" y1="6" x2="21" y2="6" />
				<line class="mid" x1="3" y1="12" x2="21" y2="12" />
				<line class="bot" x1="3" y1="18" x2="21" y2="18" />
			</svg>
		</div>
	</nav>

	<div class="sidebar" class:hidden={!sidebarDisplayed}>
		<button class="close-button" aria-label="Close alert" type="button" on:click={toggleSidebar}>
			<span aria-hidden="true">&times;</span>
		</button>
		<div class="side-items global-nav-text">
			<a href="." class="side-item">
				<span class="bold">00</span> HOME
			</a>
			<a href="/Destination" class="side-item">
				<span class="bold">01</span> DESTINATION
			</a>
			<a href="/Crew" class="side-item">
				<span class="bold">02 </span> CREW
			</a>
			<a href="." class="side-item">
				<span class="bold">03</span> TECHNOLOGY
			</a>
		</div>
	</div>
</div>

<style lang="scss">
	@use 'src/routes/styles/sizes.scss' as v;

	.nav-container {
		@media only screen and (min-width: v.$mobile-devices) {
			--navbar-display: none;
			--sidebar-display: block;
		}

		@media only screen and (min-width: v.$md-desktop-devices) {
			--navbar-display: flex;
			--sidebar-display: none;
		}
		.navbar {
			position: absolute;
			top: 0;
			right: 0;
			left: 0;

			width: 100%;
			height: 5rem;

			display: grid;
			grid-template-rows: auto;
			grid-template-columns: auto 1fr;
			justify-content: space-between;
			align-items: center;

			padding-inline-start: 2rem;

			.nav-logo {
				width: 3rem;
				height: 3rem;
			}

			.pseudo {
				position: absolute;
				display: var(--navbar-display);
				left: 10%;

				width: 32%;
				height: 1px;

				z-index: 2;

				background: #ffffff25;
			}

			.nav-items {
				background: rgba(255, 255, 255, 0.04);
				backdrop-filter: blur(2.5rem);

				height: 90%;
				width: 65%;

				display: var(--navbar-display);
				justify-content: space-evenly;
				align-items: center;
				margin-left: auto;

				.nav-item {
					position: relative;
					height: 100%;
					display: flex;
					align-items: center;

					text-decoration: none;
					color: var(--global-white);

					&:before {
						content: '';

						position: absolute;
						bottom: 0;
						left: 0;

						width: 100%;
						height: 0.2rem;

						background-color: var(--global-grey);

						visibility: hidden;
						transform: scaleX(0);

						transition: all 0.3s ease-in-out 0s;
					}

					&:hover:before {
						visibility: visible;
						transform: scaleX(1);
					}

					.bold {
						font-weight: 700;
					}
				}
			}

			.sidebar-hamburger {
				display: var(--sidebar-display);
				margin-left: auto;
				margin-right: 2rem;

				&:hover {
					cursor: pointer;
				}
			}
		}

		.sidebar {
			display: var(--sidebar-display);
			position: fixed;
			right: 0;
			top: 0;
			bottom: 0;

			transition: width 0.3s ease-in-out 0s;
			width: 70%;
			height: 100%;

			display: grid;
			grid-template-columns: auto;
			grid-template-rows: auto 1fr;
			align-items: flex-start;

			z-index: 2;

			background: rgba(255, 255, 255, 0.04);
			backdrop-filter: blur(2.5rem);

			.close-button {
				margin: 1rem 2rem 0 auto;
				height: min-content;

				font-size: 2rem;
				background: none;
				border: none;
				color: var(--global-white);

				&:hover {
					cursor: pointer;
				}
			}
			.side-items {
				display: grid;
				margin-left: 3rem;
				.side-item {
					text-decoration: none;
					color: var(--global-white);
					margin: 10% 0;

					.bold {
						font-weight: 700;
					}
				}
			}

			&.hidden {
				width: 0;
			}
		}
	}
</style>
