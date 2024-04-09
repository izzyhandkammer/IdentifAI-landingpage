<script>
	let apps = '/apps.png';
	let favicon = '/eyecon.png';
	let mobile = '/mobile.png';
	let meetingAdd = '/meeting-add.png';

	let cards;
	function handleMouseMove(e) {
		for (const card of cards.getElementsByClassName('card')) {
			const rect = card.getBoundingClientRect(),
				x = e.clientX - rect.left,
				y = e.clientY - rect.top;

			card.style.setProperty('--mouse-x', `${x}px`);
			card.style.setProperty('--mouse-y', `${y}px`);
		}
	}
</script>

<body>
	<head>
		<title>IdentifAI</title>
		<link rel="icon" type="image/x-icon" src={favicon} />
	</head>

	<div class="content" id="content">
		<div class="title-card-gradient">
			<h1 class="title-card">We are IdentifAI</h1>
			<h2 class="info-card">
				Deepfakes have become a significant threat to the fabric of our society. That’s why
				IdentifAI seeks to create a transparent internet in an age of ever-improving artificial
				intelligence. <br />
				We take a novel approach to address the challenge of deepfakes; our platform offers a streamlined
				service for protecting, managing, and monitoring image veracity in real time for enterprises
				at high risk of deepfake attacks.
			</h2>
			<div class="learn-more">
				<a href="#cards">
					<p>Learn more</p>
					<div class="arrow"></div>
				</a>
			</div>
		</div>
		<div id="cards" bind:this={cards} on:mousemove={handleMouseMove} role="presentation">
			<div class="card ui-demo">
				<div class="card-content">
					<div class="card-image-ui-demo"></div>
					<div class="card-info-wrapper">
						<div class="card-info-ui-demo">
							<div class="card-info-title"></div>
						</div>
					</div>
				</div>
			</div>
			<div class="text-separator">
				<div class="rhetorical">
					<h2>Who has acess to your photos and videos?</h2>
					<p>
						To safeguard yourself from the risks of deepfakes, adopting a proactive stance is key.
						At IdentifAI, we've engineered a cutting-edge solution designed to actively protect and
						monitor the images you share online, ensuring your digital persona is secure from misuse
						and manipulation.
					</p>
				</div>
				<div class="solution">
					<h3>Reactive defense</h3>
					<h4>Utilize our KYE system for ----</h4>
				</div>
			</div>
			<div class="card apps">
				<div class="card-content">
					<div class="card-image-apps">
						<img src={apps} alt="apps" />
					</div>
					<div class="card-info-wrapper-apps">
						<div class="card-info">
							<div class="card-info-title">
								<h3>Connect your apps</h3>
								<h4>Compatible with the most widely used video conferencing services</h4>
							</div>
						</div>
					</div>
				</div>
			</div>
			<div class="card meeting-add">
				<div class="card-content">
					<div class="card-image-meeting-add">
						<img src={meetingAdd} alt="meetingAdd" />
					</div>
					<div class="card-info-wrapper-meeting-add">
						<div class="card-info">
							<div class="card-info-title">
								<h3>It's as simple as telling us where to be and when</h3>
								<h4>Our platform will take care of the rest</h4>
							</div>
						</div>
					</div>
				</div>
			</div>
			<div class="card mobile">
				<div class="card-content">
					<div class="card-image-mobile">
						<img src={mobile} alt="mobile" />
					</div>
					<div class="card-info-wrapper-mobile">
						<div class="card-info">
							<div class="card-info-title">
								<h3>On the go?</h3>
								<h4>Utilize the IdentifAI platform on any device</h4>
							</div>
						</div>
					</div>
				</div>
			</div>
			<div class="card profile-creation">
				<div class="card-content">
					<div class="card-image-profile-creation"></div>
					<div class="card-info-wrapper-profile-creation">
						<div class="card-info">
							<div class="card-info-title">
								<h3>Create profiles for your employees, business associates, and more</h3>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</body>

<style>
	/* -- ↓ ↓ ↓ global styles ↓ ↓ ↓ -- */
	:root {
		--bg-color: #141414;
		--card-color: #171717;

		--gradient-one: #141414;
		--gradient-two: #17142b;
		--gradient-three: #14151a;
		--gradient-four: #221220;
	}
	:global(html) {
		scroll-behavior: smooth;
	}
	/* -- ↓ ↓ ↓ background gardient and grid styles ↓ ↓ ↓ -- */

	/* 
content inspector nuclear option:
* {
  outline: 1px solid #f00 !important;
}
*/
	body {
		flex-direction: column;
		background-color: var(--bg-color);
		justify-content: center;
		align-items: center;
		align-content: center;
		font-family:
			system-ui,
			-apple-system,
			BlinkMacSystemFont,
			'Segoe UI',
			Roboto,
			Oxygen,
			Ubuntu,
			Cantarell,
			'Open Sans',
			'Helvetica Neue',
			sans-serif;
		background: linear-gradient(
			-45deg,
			var(--gradient-one),
			var(--gradient-two),
			var(--gradient-three),
			var(--gradient-four)
		);
		animation: gradient 15s ease infinite;
		background-size: 400% 400%;
		z-index: -1;
		margin: 0%;
	}

	/* -- ↓ ↓ ↓ background gradient effect ↓ ↓ ↓ -- */
	@keyframes gradient {
		0% {
			background-position: 0% 50%;
		}
		50% {
			background-position: 100% 50%;
		}
		100% {
			background-position: 0% 50%;
		}
	}
	/* -- ↓ ↓ ↓ background grid style ↓ ↓ ↓ -- */
	/*to change grid opacity: adjust alpha value in rbg(-, -, -, alpha) */

	.text-separator {
		display: flex;
		flex-direction: column;
		gap: 20px;
	}

	.rhetorical {
		display: flex;
		flex-direction: row;
	}

	.rhetorical h2 {
		color: white;
		font-size: 40px;
		margin-top: 20px;
		margin-bottom: 20px;
		font-weight: 800;
		width: 40%;
		animation-name: glow-two;
		animation-duration: 3s;
		animation-iteration-count: infinite;
		animation-direction: alternate;
		background-color: linear-gradient(
			180deg,
			rgb(175, 172, 172) 70%,
			transparent
		); /* adjust colors as needed */
	}
	@keyframes glow-two {
		from {
			text-shadow:
				0px 0px 5px #fff,
				0px 0px 3px #614ad3;
		}
		to {
			text-shadow:
				0px 0px 10px #fff,
				0px 0px 5px #614ad3;
		}
	}

	.rhetorical p {
		color: white;
		font-size: 20px;
		margin-top: 20px;
		margin-bottom: 20px;
		width: 60%;
	}

	.solution {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.solution h3 {
		color: white;
		font-size: 60px;
		margin-top: 60px;
		margin-bottom: 20px;
	}
	.solution h4 {
		color: white;
		font-size: 20px;
		margin-top: 20px;
		margin-bottom: 20px;
	}
	#content {
		background-color: transparent;
		background-image: linear-gradient(
				0deg,
				transparent 24%,
				rgba(255, 255, 255, 0.1) 25%,
				rgba(255, 255, 255, 0.1) 26%,
				transparent 27%,
				transparent 74%,
				rgba(255, 255, 255, 0.1) 75%,
				rgba(255, 255, 255, 0.1) 76%,
				transparent 77%,
				transparent
			),
			linear-gradient(
				90deg,
				transparent 24%,
				rgba(255, 255, 255, 0.1) 25%,
				rgba(255, 255, 255, 0.1) 26%,
				transparent 27%,
				transparent 74%,
				rgba(255, 255, 255, 0.1) 75%,
				rgba(255, 255, 255, 0.1) 76%,
				transparent 77%,
				transparent
			);

		height: 100%;
		background-size: 50px 50px;
		z-index: 2;
	}

	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.learn-more {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		padding: 6px;
		margin: 0;
		gap: 6px;
	}

	.learn-more a {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		color: white;
		text-decoration: none;
		font-size: 16px;
		cursor: pointer;
		opacity: 0.7;
	}
	.learn-more p {
		margin: 20px 0 0 0;
	}

	.arrow {
		box-sizing: border-box;
		height: 20px;
		width: 20px;
		border-style: solid;
		border-color: white;
		border-width: 0px 1px 1px 0px;
		transform: rotate(45deg);
		transition: transform 0.3s ease-in-out;
	}

	.learn-more:hover a {
		color: #f0f0f0;
		opacity: 1;
	}
	.learn-more:hover .arrow {
		transform: translateY(10px) rotate(45deg);
	}

	.title-card {
		color: white;
		margin-bottom: 50px;
		font-size: 72px;
		font-weight: 700;
		width: 70%;
		text-align: center;
	}

	.title-card-gradient {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		background: radial-gradient(var(--bg-color) 35%, transparent 65%);
		background-size:
			100% 100%,
			4vh 4vh;
	}

	.content h1 {
		margin-top: 180px;
		background: linear-gradient(180deg, white 70%, transparent); /* adjust colors as needed */
		background-clip: text;
		color: transparent;
		font-weight: 700;
		animation-name: glow;
		animation-duration: 3s;
		animation-iteration-count: infinite;
		animation-direction: alternate;
	}

	@keyframes glow {
		from {
			text-shadow:
				0px 0px 5px #fff,
				0px 0px 5px #614ad3;
		}
		to {
			text-shadow:
				0px 0px 10px #fff,
				0px 0px 15px #614ad3;
		}
	}

	.info-card {
		color: white;
		font-size: 20px;
		margin-top: 20px;
		margin-bottom: 20px;
		width: 70%;
		text-align: center;
	}

	.rhetorical h2 {
		color: white;
		font-size: 40px;
		margin-top: 20px;
		margin-bottom: 20px;
		text-align: center;
	}

	.rhetorical p {
		color: white;
		font-size: 20px;
		margin-top: 20px;
		margin-bottom: 20px;
		width: 70%;
		text-align: center;
	}

	/* -- ↓ ↓ ↓ card effects ↓ ↓ ↓ -- */

	#cards {
		padding-top: 10%;
		padding-bottom: 10%;
		display: flex;
		flex-wrap: wrap;
		gap: 8px;
		justify-self: center;
		max-width: 916px;
		width: calc(100% - 20px);
	}

	#cards:hover > .card::after {
		opacity: 1;
	}

	.card {
		background-color: rgba(255, 255, 255, 0.1);
		border-radius: 10px;
		cursor: pointer;
		display: flex;
		height: 260px;
		flex-direction: column;
		position: relative;
		width: 300px;
		transition: transform 0.3s ease-in-out;
	}

	.ui-demo {
		width: 916px;
		height: 516px;
	}

	.apps {
		width: 550px;
		height: 416px;
	}

	.mobile {
		width: 350px;
		height: 416px;
	}

	.meeting-add {
		width: 350px;
		height: 416px;
	}

	.profile-creation {
		width: 550px;
		height: 416px;
	}

	.card-info-wrapper-apps {
		position: absolute;
		bottom: 0;
		align-items: center;
		padding: 30px 20px;
		flex-direction: column;
	}

	.card-info-wrapper-mobile {
		position: absolute;
		bottom: 0;
		align-items: center;
		padding: 30px 20px;
		flex-direction: column;
	}

	.card-info-wrapper-meeting-add {
		position: absolute;
		bottom: 0;
		align-items: center;
		padding: 30px 20px;
		flex-direction: column;
	}

	.card-info-wrapper-profile-creation {
		position: absolute;
		bottom: 0;
		align-items: center;
		padding: 30px 20px;
		flex-direction: column;
	}

	.card:hover::before {
		opacity: 1;
	}

	.card::before,
	.card::after {
		border-radius: inherit;
		content: '';
		height: 100%;
		left: 0px;
		opacity: 0;
		position: absolute;
		top: 0px;
		transition: opacity 500ms;
		width: 100%;
	}

	.card::before {
		background: radial-gradient(
			800px circle at var(--mouse-x) var(--mouse-y),
			rgba(255, 255, 255, 0.06),
			transparent 40%
		);
		z-index: 3;
	}

	.card::after {
		background: radial-gradient(
			600px circle at var(--mouse-x) var(--mouse-y),
			rgba(255, 255, 255, 0.4),
			transparent 40%
		);
		z-index: 1;
	}

	.card > .card-content {
		background-color: var(--card-color);
		border-radius: inherit;
		display: flex;
		flex-direction: column;
		flex-grow: 1;
		inset: 1px;
		padding: 10px;
		position: absolute;
		z-index: 2;
	}

	/* -- ↓ ↓ ↓ extra card content styles ↓ ↓ ↓ -- */

	h1,
	h2,
	h3,
	h4 {
		color: rgb(240, 240, 240);
		font-weight: 400;
		margin: 0px;
	}

	.card-image-apps {
		align-content: center;
		display: flex;
		justify-content: center;
	}

	.card-image-mobile {
		align-content: center;
		display: flex;
		justify-content: center;
	}

	.card-image-meeting-add {
		align-content: center;
		display: flex;
		justify-content: center;
	}

	.card-image-profile-creation {
		align-content: center;
		display: flex;
		justify-content: center;
	}

	.card-image-apps img {
		opacity: 0.45;
		height: 50%;
		width: auto;
		max-height: 900px;
		transform: scale(0.7);
		transition: transform 0.3s ease-in-out;
		user-select: none;
	}

	.card:hover .card-image-apps img {
		opacity: 0.85;
		transform: scale(0.8);
	}

	.card-image-mobile img {
		opacity: 0.45;
		height: 40%;
		width: auto;
		max-height: 900px;
		transform: scale(0.8);
		transition: transform 0.3s ease-in-out;
		user-select: none;
	}

	.card:hover .card-image-mobile img {
		opacity: 0.85;
		transform: scale(0.9);
	}

	.card-image-meeting-add img {
		opacity: 0.45;
		height: 70%;
		width: auto;
		max-height: 900px;
		transition: transform 0.3s ease-in-out;
		user-select: none;
		position: absolute;
	}

	.card:hover .card-image-meeting-add img {
		opacity: 0.85;
		transform: scale(1.15);
	}
	/*
	.card-image-profile-creation img {
		opacity: 0.45;
		height: 70%;
		width: auto;
		max-height: 900px;
		transition: transform 0.3s ease-in-out;
		user-select: none;
		position: absolute;
	}
*/
	.card:hover .card-image-profile-creation img {
		opacity: 0.85;
		transform: scale(1.15);
	}

	.card-info-wrapper {
		align-items: center;
		display: flex;
		flex-grow: 1;
		justify-content: flex-start;
		padding: 0px 20px;
		user-select: none;
	}

	.card-info {
		align-items: flex-start;
		display: flex;
		gap: 10px;
	}

	.card-info-title > h3 {
		font-size: 1.1em;
		line-height: 20px;
	}

	.card-info-title > h4 {
		color: rgba(255, 255, 255, 0.5);
		font-size: 0.85em;
		margin-top: 8px;
	}

	/* -- ↓ ↓ ↓ some responsiveness ↓ ↓ ↓ -- */

	@media (max-width: 1000px) {
		body {
			align-items: flex-start;
			overflow: auto;
		}

		#cards {
			max-width: 1000px;
			padding: 10px 0px;
		}

		.card {
			flex-shrink: 1;
			width: calc(50% - 4px);
		}
	}

	@media (max-width: 500px) {
		.card {
			height: 180px;
		}

		.card-info-wrapper {
			padding: 0px 10px;
		}

		.card-info-title > h3 {
			font-size: 0.9em;
		}

		.card-info-title > h4 {
			font-size: 0.8em;
			margin-top: 4px;
		}
	}

	@media (max-width: 320px) {
		.card {
			width: 100%;
		}
	}
</style>
