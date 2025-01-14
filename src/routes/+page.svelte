<script>
	import { onMount } from 'svelte';

	let days = 8;
	let hours = 23;
	let minutes = 55;
	let seconds = 41;

	const countdown = () => {
		const interval = setInterval(() => {
			if (seconds > 0) {
				seconds--;
			} else if (minutes > 0) {
				minutes--;
				seconds = 59;
			} else if (hours > 0) {
				hours--;
				minutes = 59;
				seconds = 59;
			} else if (days > 0) {
				days--;
				hours = 23;
				minutes = 59;
				seconds = 59;
			} else {
				clearInterval(interval);
			}
		}, 1000);
	};

	onMount(countdown);
</script>

<div class="container">
	<img src="/images/bg-stars.svg" alt="Stars" class="stars" />
	<img src="/images/pattern-hills.svg" alt="Hills" class="hills" />
	<div class="content">
		<h1>We're Launching Soon</h1>
		<div class="countdown">
			<div class="card">
				<span class="flip">{days}</span>
				<div class="label">Days</div>
			</div>
			<div class="card">
				<span class="flip">{hours}</span>
				<div class="label">Hours</div>
			</div>
			<div class="card">
				<span class="flip">{minutes}</span>
				<div class="label">Minutes</div>
			</div>
			<div class="card">
				<span class="flip">{seconds}</span>
				<div class="label">Seconds</div>
			</div>
		</div>
	</div>
</div>

<style>
	/* Farben */
	:root {
		--primary-grayish-blue: hsl(237, 18%, 59%);
		--primary-soft-red: hsl(345, 95%, 68%);
		--neutral-white: hsl(0, 0%, 100%);
		--neutral-dark-desaturated-blue: hsl(236, 21%, 26%);
		--neutral-very-dark-blue: hsl(235, 16%, 14%);
		--neutral-very-dark-blackish-blue: hsl(234, 17%, 12%);
	}

	/* Allgemeine Stile */

	.container {
		position: relative;
		height: 100vh;
		background-color: var(--neutral-very-dark-blackish-blue);
	}

	.stars {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		z-index: 0;
	}

	.hills {
		position: absolute;
		bottom: 0;
		left: 0;
		width: 100%;
		height: 200px; /* adjust the height to match the design */
		z-index: 1;
	}

	.content {
		position: relative;
		z-index: 2;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		height: 100%;
	}

	h1 {
		text-align: center;
		margin-bottom: 2rem;
		font-weight: 700;
		font-size: 2.5rem;
		color: hsl(0, 0%, 90%); /* changed color to a lighter shade */
		letter-spacing: 0.1rem;
	}

	.countdown {
		display: flex;
		justify-content: center;
		gap: 2rem;
	}

	.card {
		background-color: var(--neutral-dark-desaturated-blue);
		color: var(--primary-soft-red);
		font-size: 4rem;
		font-weight: 700;
		width: 120px;
		height: 120px; /* changed height to match width */
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		border-radius: 10px;
		position: relative;
		perspective: 1000px;
		text-align: center;
		box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
	}

	.flip {
		position: absolute;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
		display: flex;
		justify-content: center;
		align-items: center;
		transition: transform 0.6s;
		backface-visibility: hidden;
	}

	.label {
		font-size: 1.2rem;
		color: var(--primary-grayish-blue);
		margin-top: 0.5rem;
		letter-spacing: 0.1rem;
		position: absolute;
		bottom: -30px;
	}

	/* Responsive */
	@media (max-width: 375px) {
		.card {
			width: 80px;
			height: 120px;
			font-size: 2.5rem;
		}

		h1 {
			font-size: 1.8rem;
		}

		.label {
			font-size: 1rem;
		}
	}
</style>
