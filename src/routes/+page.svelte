<script lang="ts">
</script>

<div class="wrapper">
	<div class="content">
		<div class="text-container">
			<h5 class="global-head-5">So, you want to travel to</h5>
			<div class="global-head-1">Space</div>
			Let’s face it; if you want to go to space, you might as well genuinely go to outer space and not
			hover kind of on the edge of it. Well sit back, and relax because we’ll give you a truly out of
			this world experience!
		</div>
		<a href="/Destination" class="global-head-4 explore"> EXPLORE </a>
	</div>
</div>

<style lang="scss">
	@use 'src/routes/styles/sizes.scss' as v;

	.wrapper {
		@media only screen and (min-width: v.$mobile-devices) {
			--background-image: url('../assets/home/background-home-mobile.jpg');
			--content-grid-columns: 1fr;
			--content-text-align: center;
		}

		@media only screen and (min-width: v.$tablet-devices) {
			--background-image: url('../assets/home/background-home-tablet.jpg');
		}

		@media only screen and (min-width: v.$md-desktop-devices) {
			--background-image: url('../assets/home/background-home-desktop.jpg');
			--content-grid-columns: 1fr 1fr;
			--content-text-align: start;
		}

		display: grid;
		grid-template-rows: 1fr;

		background-image: var(--background-image);
		background-size: cover;
		background-repeat: no-repeat;

		width: 100%;
		height: 100%;
		min-height: 100vh;

		.content {
			display: grid;

			margin-top: 4rem;

			grid-template-columns: var(--content-grid-columns);
			text-align: var(--content-text-align);

			place-items: center;

			width: 100%;
			overflow-x: auto;
		}
		.text-container {
			width: min(28rem, 100%);
		}

		.explore {
			position: relative;
			height: 17.125rem;
			width: 17.125rem;
			margin: 1rem;

			display: flex;
			justify-content: center;
			align-items: center;

			background-color: var(--global-white);
			color: black;
			text-decoration: none;
			border-radius: 50%;

			@media only screen and (min-width: v.$md-desktop-devices) {
				&:before {
					content: '';

					position: absolute;

					width: 140%;
					height: 140%;
					border-radius: 50%;

					background-color: var(--global-white);
					opacity: 0.1;

					visibility: hidden;
					transform: scale(0);

					transition: all 0.15s ease-in-out 0s;
				}

				&:hover:before {
					visibility: visible;
					transform: scale(1);
				}
			}
		}
	}
</style>
