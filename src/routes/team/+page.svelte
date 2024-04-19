<script>
  import Background from '../../components/Background.svelte';
  const favicon = '/eyecon.png';
  const pVann = '/pvann.jpeg';
  const jMarciano = '/jmarciano.jpeg';
</script>

<head>
  <title>IdentifAI</title>
  <link rel="icon" type="image/x-icon" src={favicon} />
</head>
<body>
  <Background />
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
      <a href="https://www.linkedin.com/in/paul-vann-b996b2120" target="_blank"
        ><button id="buttons" class="glow-button">LinkedIn</button></a
      >
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
      <a href="https://www.linkedin.com/in/justin-marciano32" target="_blank"
        ><button id="buttons" class="glow-button">LinkedIn</button></a
      >
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

  .glow-button {
    font-weight: 500;
    padding: 10px 20px;
    border: 1px solid #d0afe5;
    border-radius: 5px;
    background: transparent;
    color: white;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 4px 10px 1px #37195e;
    margin: 20px;
    margin-top: 0;
  }

  .glow-button:hover {
    box-shadow: 0 0 15px 3px #d0afe5;
    opacity: 0.9;
    background-color: #1e0e34;
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
