<script>
  import { onMount, onDestroy } from "svelte";
  let apps = "/apps.png";
  let favicon = "/eyecon.png";
  let mobile = "/mobile.png";
  let meetingAdd = "/meeting-add.png";
  let pVann = "/pvann.jpeg";
  let jMarciano = "/jmarciano.jpeg";

  let cards;
  function handleMouseMove(e) {
    for (const card of cards.getElementsByClassName("card")) {
      const rect = card.getBoundingClientRect(),
        x = e.clientX - rect.left,
        y = e.clientY - rect.top;

      card.style.setProperty("--mouse-x", `${x}px`);
      card.style.setProperty("--mouse-y", `${y}px`);
    }
  }

  let canvas;
  let ctx;
  let particles = [];
  let particleCount;

  class Particle {
    constructor() {
      this.reset();
      this.y = Math.random() * canvas.height;
      this.fadeDelay = Math.random() * 600 + 100;
      this.fadeStart = Date.now() + this.fadeDelay;
      this.fadingOut = false;
    }

    reset() {
      this.x = Math.random() * canvas.width;
      this.y = Math.random() * canvas.height;
      this.speed = Math.random() / 5 + 0.1;
      this.opacity = 1;
      this.fadeDelay = Math.random() * 600 + 100;
      this.fadeStart = Date.now() + this.fadeDelay;
      this.fadingOut = false;
    }

    update() {
      this.y -= this.speed;
      if (this.y < 0) {
        this.reset();
      }

      if (!this.fadingOut && Date.now() > this.fadeStart) {
        this.fadingOut = true;
      }

      if (this.fadingOut) {
        this.opacity -= 0.008;
        if (this.opacity <= 0) {
          this.reset();
        }
      }
    }

    draw() {
      ctx.fillStyle = `rgba(${255 - (Math.random() * 255) / 2}, 255, 255, ${this.opacity})`;
      ctx.fillRect(this.x, this.y, 0.4, Math.random() * 2 + 1);
    }
  }

  function initParticles() {
    particles = [];
    for (let i = 0; i < particleCount; i++) {
      particles.push(new Particle());
    }
  }

  function animate() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    particles.forEach((particle) => {
      particle.update();
      particle.draw();
    });
    requestAnimationFrame(animate);
  }

  function calculateParticleCount() {
    return Math.floor((canvas.width * canvas.height) / 6000);
  }

  function onResize() {
    if (typeof window !== "undefined") {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
      particleCount = calculateParticleCount() * 2;
      initParticles();
    }
  }

  onMount(() => {
    if (typeof window !== "undefined") {
      ctx = canvas.getContext("2d");
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
      particleCount = calculateParticleCount() * 2;
      initParticles();
      animate();
      window.addEventListener("resize", onResize);
    }
  });

  onDestroy(() => {
    if (typeof window !== "undefined") {
      window.removeEventListener("resize", onResize);
    }
  });
</script>

<head>
  <title>IdentifAI</title>
  <link rel="icon" type="image/x-icon" src={favicon} />
</head>
<body>
  <canvas bind:this={canvas} id="particleCanvas"></canvas>
  <div class="content" id="content">
    <div class="heroT">
      <h1>Defend Against Deepfakes</h1>
      <h1>Defend Against Deepfakes</h1>
    </div>
    <h2 class="info-card">
      Deepfakes have become a significant threat to the fabric of our society.
      That’s why IdentifAI has created proactive and reactive solutions to
      protect and increase transparency for enterprises in an age of
      ever-improving artificial intelligence.
    </h2>
    <div class="learn-more">
      <a href="#cards">
        <p>Learn more</p>
        <div class="arrow"></div>
      </a>
    </div>
    <div
      id="cards"
      bind:this={cards}
      on:mousemove={handleMouseMove}
      role="presentation"
    >
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
            To safeguard yourself from the risks of deepfakes, adopting a
            proactive stance is key. At IdentifAI, we've engineered a
            cutting-edge solution designed to actively protect and monitor the
            images you share online, ensuring your digital persona is secure
            from misuse and manipulation.
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
                <h4>
                  Compatible with the most widely used video conferencing
                  services
                </h4>
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
      <div class="text-separator">
        <div class="solution">
          <h3>Proactive Solutions</h3>
          <h4>Our Photographic Firewall system ----</h4>
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
                <h3>
                  Create profiles for your employees, business associates, and
                  more
                </h3>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="solution"><h3>Our Team</h3></div>
    <div class="team">
      <div class="member">
        <img src={pVann} alt="pVann" />
        <h3>Paul Vann: Co-Founder</h3>
        <p>
          Paul is a seasoned cybersecurity professional, with experience across
          numerous emerging markets in the field. He has worked at a wide array
          of cybersecurity and software development startups, helping to ensure
          a more secure future for all. Paul additionally is passionate about
          emerging technologies in the space and was recognized as a Top rated
          Speaker at the RSA Conference in 2023.
        </p>
      </div>
      <div class="member">
        <img src={jMarciano} alt="jMarciano" />
        <h3>Justin Marciano: Co-Founder</h3>
        <p>
          Justin is the Co-Founder and CEO of IdentifAI. Studying economics with
          a concentration in finance at the University of Virginia, he has
          navigated his way through the venture capital, blockchain, and payment
          sectors, aligning his career path with his enthusiasm for emerging
          technologies. Justin currently works in product management and has
          previously worked at Stepstone Group as a VC & Growth Analyst.
        </p>
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
    font-family: "Syne", "Inter";
    background: #05060f
      linear-gradient(
        0deg,
        rgba(216, 236, 248, 0.06),
        rgba(152, 192, 239, 0.06)
      );
    background-size: 400% 400%;
    z-index: -1;
    margin: 0%;
  }

  .heroT {
    height: 20em;
    padding-top: 2em;
    opacity: 0;
    animation: load 2s ease-in-out 0.6s forwards;
  }
  @keyframes load {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
  .heroT > h1 {
    position: absolute;
    left: 0;
    right: 0;
    margin: auto;
    width: fit-content;

    font-size: 4em;
    font-weight: 600;
    color: #9dc3f7;
    background: radial-gradient(
        2em 2em at 50% 50%,
        transparent calc(var(--p) - 2em),
        #fff calc(var(--p) - 1em),
        #fff calc(var(--p) - 0.4em),
        transparent var(--p)
      ),
      linear-gradient(0deg, #bad1f1 30%, #9dc3f7 100%);
    background-clip: text;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    text-shadow: 0 2px 16px rgba(174, 207, 242, 0.24);

    --p: 0%;
    transition: --p 3s linear;

    animation: pulse 10s linear 1.2s infinite;
  }
  .heroT h1:nth-child(2) {
    background: radial-gradient(
      2em 2em at 50% 50%,
      transparent calc(var(--p) - 2em),
      transparent calc(var(--p) - 1em),
      #fff calc(var(--p) - 1em),
      #fff calc(var(--p) - 0.4em),
      transparent calc(var(--p) - 0.4em),
      transparent var(--p)
    );
    background-clip: text;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    filter: blur(16px) opacity(0.4);
  }
  @keyframes pulse {
    0% {
      --p: 0%;
    }
    50% {
      --p: 300%;
    }
    100% {
      --p: 300%;
    }
  }
  @property --p {
    syntax: "<percentage>";
    inherits: false;
    initial-value: 0%;
  }

  h2 {
    font-family: "Inter";
    color: white;
    font-weight: 100;
  }
  h3 {
    font-family: "Syne";
    color: white;
    font-weight: 700;
  }
  h4 {
    font-family: "Inter";
    color: rgb(240, 240, 240);
    font-weight: 400;
  }
  p {
    font-family: "Inter";
    color: rgb(240, 240, 240);
    font-weight: 100;
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
  /* -- ↓ ↓ ↓ background particle style ↓ ↓ ↓ -- */

  canvas#particleCanvas {
    position: fixed;
    pointer-events: none;
    animation: load 0.4s ease-in-out forwards;
    z-index: 1;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
  }
  @keyframes load {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
  /*to change grid opacity: adjust alpha value in rbg(-, -, -, alpha) */

  .text-separator {
    display: flex;
    flex-direction: column;
    gap: 20px;
    align-items: center;
    justify-content: center;
    justify-self: center;
    margin: auto;
  }

  .rhetorical {
    display: flex;
    justify-content: center;
    flex-direction: row;
    align-items: center;
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
        0px 0px 3px #fff,
        0px 0px 1px #614ad3;
    }
    to {
      text-shadow:
        0px 0px 5px #fff,
        0px 0px 4px #614ad3;
    }
  }

  .rhetorical p {
    color: white;
    font-size: 20px;
    font-weight: 100;
    margin-top: 20px;
    margin-bottom: 20px;
    width: 60%;
  }

  .solution {
    justify-self: center;
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

  .content h1 {
    margin-top: 180px;
    background: linear-gradient(
      180deg,
      white 70%,
      transparent
    ); /* adjust colors as needed */
    background-clip: text;
    color: transparent;
    font-weight: 700;
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
    font-family: "Inter";
    font-weight: 200;
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
    content: "";
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
    height: 80%;
    width: auto;
    max-height: 416px;
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
    height: 80%;
    width: auto;
    max-height: 416px;
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
  .team {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    margin: 20px;
    gap: 30px;
  }
  .member {
    background: rgba(255, 255, 255, 0.03);
    border-radius: 16px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(4.4px);
    -webkit-backdrop-filter: blur(4.4px);
    border: 1px solid rgba(255, 255, 255, 0.16);
    width: fit-content;
    max-width: fit-content;
    align-items: center;
    display: flex;
    flex-direction: column;
  }
  .member img {
    border-radius: 5%;
    width: 300px;
    aspect-ratio: 1/1;
    overflow: hidden;
    width: 250px;
    border-radius: 8px;
    box-shadow:
      rgba(62, 63, 168, 0.3) 0px 10px 30px 8px,
      rgba(62, 63, 168, 0.4) 0px 0px 0px 2px;
    margin: 10%;
    opacity: 0.8;
  }

  .member h3 {
    color: white;
    margin: 0;
  }

  .member p {
    color: white;
    margin: 10px;
    width: 350px;
    padding: 10px;
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
