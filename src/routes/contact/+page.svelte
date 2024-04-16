<script>
  import { onMount, onDestroy } from "svelte";

  let canvas;
  let ctx;
  let particles = [];
  let particleCount;
  let favicon = "/eyecon.png";
  
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

  // Form submission
  
  let status = "";

  const handleSubmit = async (data) => {
    status = "Submitting...";
    const formData = new FormData(data.currentTarget);
    const object = Object.fromEntries(formData);
    const json = JSON.stringify(object);

    const response = await fetch("https://api.web3forms.com/submit", {
      method: "POST",
      headers: {
        'Content-Type': 'application/json',
        Accept: "application/json",
      },
      body: json,
    });
    const result = await response.json();
    if (result.success) {
      console.log(result);
      status = "Thank you for your message! We will try to get back to you within the next 48 hours.";
    }
  };
</script>

<head>
  <title>Contact Us | IdentifAI</title>
  <link rel="icon" type="image/x-icon" src={favicon} />
</head>
<body>
  <canvas bind:this={canvas} id="particleCanvas"></canvas>
  <div class="content">
    <h2>Get in Touch</h2>
    <div class="form-wrapper">
      <form on:submit|preventDefault={handleSubmit}>
        <input
          type="hidden"
          name="access_key"
          value="d3ade7d6-8f02-4581-8436-835952ee3914"
        />
        <input type="checkbox" name="botcheck" class="hidden" style="display: none;">
        <div class="values-separator">
          <p>Your Name:</p>
          <input type="text" name="name" required />
        </div>
        <div class="values-separator">
          <p>Your Email:</p>
          <input type="email" name="email" required />
        </div>
        <div class="values-separator">
          <p>Your Message:</p>
          <textarea name="message" required rows="3"></textarea>
        </div>
        <div class="center-this" style="padding-top: 10px">
          <input type="submit" />
        </div>
      </form>
      <div class="status-message">{status}</div>
    </div>
  </div>
</body>

<style>
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

  p {
    color: white;
    font-size: 1.2rem;
    margin: 0;
  }

  h2 {
    color: white;
    font-size: 50px;
    font-weight: 750;
    width: 40%;
    color: #9dc3f7;
    text-align: center;
    margin: auto;
  }

  form {
    display: flex;
    flex-direction: column;
    gap: 10px;
    width: 70%;
  }

  .content {
    display: flex;
    flex-direction: column;
    gap: 10px;
    align-items: center;
    justify-content: center;
    margin-top: 50px;
  }

  .form-wrapper {
    background: rgba(255, 255, 255, 0.03);
    border-radius: 16px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(4.4px);
    -webkit-backdrop-filter: blur(4.4px);
    border: 1px solid rgba(255, 255, 255, 0.16);
    width: 40%;
    align-items: center;
    display: flex;
    justify-content: center;
    flex-direction: column;
    padding: 40px;
    margin: 10px;
    margin-bottom: 40px;
  }

  .form-wrapper:after {
    content: "";
    display: block;
    height: 1px; /* adjust as needed */
    width: 100%;
    background: radial-gradient(
      white 30%,
      transparent 70%
    ); /* adjust colors as needed */
    position: absolute;
    bottom: 0;
  }

  .form-wrapper:before {
    content: "";
    display: block;
    height: 1px; /* adjust as needed */
    width: 100%;
    background: radial-gradient(
      white 30%,
      transparent 70%
    ); /* adjust colors as needed */
    position: absolute;
    top: 0;
  }

  .center-this {
    display: flex;
    justify-content: center;
  }

  .values-separator {
    display: flex;
    flex-direction: column;
    gap: 5px;
    margin-top: 10px;
  }

  input[type="submit"] {
    font-weight: 500;
    justify-self: center;
    padding: 10px 20px;
    border: 1px solid #d0afe5;
    border-radius: 5px;
    background: transparent;
    color: white;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 4px 10px 1px #37195e;
    width: 100px;
  }

  input[type="submit"]:hover {
    box-shadow: 0 0 15px 3px #d0afe5;
    opacity: 0.9;
    background-color: #1e0e34;
  }

  input[type="text"],
  input[type="email"],
  textarea {
    font-size: 18px;
    color: white;
    padding: 10px;
    margin: 5px;
    opacity: 0.8;
    border-radius: 15px;
    border-width: 1px;
    background: rgba(40, 37, 61, 0.5);
  }

  .status-message {
    padding-top: 10px;
    color: white;
    font-size: 1.2rem;
    margin-top: 10px;
  }
</style>
