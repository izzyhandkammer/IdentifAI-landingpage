<script>
  import { onMount, onDestroy } from "svelte";
  let favicon = "/eyecon.png";
  let pVann = "/pvann.jpeg";
  let jMarciano = "/jmarciano.jpeg";

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
      particleCount = calculateParticleCount() * 3;
      initParticles();
    }
  }

  onMount(() => {
    if (typeof window !== "undefined") {
      ctx = canvas.getContext("2d");
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
      particleCount = calculateParticleCount() * 3;
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
  <div class="solution"><h3>Our Team</h3></div>
  <div class="team">
    <div class="member">
      <img src={pVann} alt="pVann" />
      <h3>Paul Vann: Co-Founder</h3>
      <p>
        Paul is a seasoned cybersecurity professional, with experience across
        numerous emerging markets in the field. He has worked at a wide array of
        cybersecurity and software development startups, helping to ensure a
        more secure future for all. Paul additionally is passionate about
        emerging technologies in the space and was recognized as a Top rated
        Speaker at the RSA Conference in 2023.
      </p>
    </div>
    <div class="member">
      <img src={jMarciano} alt="jMarciano" />
      <h3>Justin Marciano: Co-Founder</h3>
      <p>
        Justin is the Co-Founder and CEO of IdentifAI. Studying economics with a
        concentration in finance at the University of Virginia, he has navigated
        his way through the venture capital, blockchain, and payment sectors,
        aligning his career path with his enthusiasm for emerging technologies.
        Justin currently works in product management and has previously worked
        at Stepstone Group as a VC & Growth Analyst.
      </p>
    </div>
  </div>
</body>

<style>
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

  .solution {
    justify-self: center;
  }
  .solution h3 {
    text-align: center;
    color: white;
    font-size: 60px;
    margin-top: 60px;
    margin-bottom: 20px;
  }

  /* -- ↓ ↓ ↓ some responsiveness ↓ ↓ ↓ -- */

  @media (max-width: 1000px) {
    body {
      align-items: flex-start;
      overflow: auto;
    }
    .team {
      flex-direction: column;
    }
    .team .member {
      width: 50%;
    }
    .team .member img {
      width: 85%;
    }
    .team .member p {
      width: 85%;
    }
    .team .member h3 {
      width: 85%;
    }
  }

  @media (max-width: 500px) {
    .team .member {
      width: 90%;
    }
  }
</style>
