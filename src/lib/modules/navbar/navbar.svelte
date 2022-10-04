<script lang="ts">
	import Logo from '../../../assets/shared/logo.svg';
</script>

<nav class="navbar">
	<img class="nav-logo" src={Logo} alt="Logo" />
	<span class="pseudo" />
	<div class="nav-items global-nav-text">
		<a href="." class="nav-item">
			<span class="bold">00</span> Home
		</a>
		<a href="." class="nav-item">
			<span class="bold">01</span> Destination
		</a>
		<a href="." class="nav-item">
			<span class="bold">02 </span> Crew
		</a>
		<a href="." class="nav-item">
			<span class="bold">03</span> Technology
		</a>
	</div>
</nav>

<style lang="scss">
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

			display: flex;
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
	}
</style>
