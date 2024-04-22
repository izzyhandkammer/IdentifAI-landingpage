<script>
  import Background from "../components/Background.svelte";
  import CardUpload from "../components/CardUpload.svelte";

  const apps = "/apps.png";
  const favicon = "/eyecon.png";
  const meetingAdd = "/meeting-add.png";

  let cards;
  function handleMouseMove(e) {
    for (const card of cards.getElementsByClassName("card")) {
      const rect = card.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;

      card.style.setProperty("--mouse-x", `${x}px`);
      card.style.setProperty("--mouse-y", `${y}px`);
    }
  }
</script>

<head>
  <title>IdentifAI</title>
  <link rel="icon" type="image/x-icon" src={favicon} />
</head>
<body>
  <Background />
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
      <a href="#product">
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
      <div class="rhetorical">
        <p style="width: 80%">
          Using proactive and reactive solutions to protect and increase
          transparency for enterprises, IdentifAI provides the security that you
          need in an era of ever-improving artificial intelligence.
        </p>
      </div>
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
          <h3 id="product" class="subt">Reactive Plugin</h3>
          <h4>
            Our innovative Photographic Firewall solution offers proactive
            defense against manipulations by generative AI. By embedding a
            robust layer of defense directly within images, our patent-pending
            anti-deepfake technology empowers media to function as its own
            safeguard, effectively thwarting malicious alterations. Our powerful
            mechanism operates seamlessly, maintaining the original image
            quality while offering real-time protection for individuals or
            entities particularly vulnerable to deepfake attacks.
          </h4>
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
          <h3 class="subt">Proactive Defense</h3>
          <h4>
            Our "Know Your Employee" or KYE product provides real time
            protection for video conferencing environments from deepfake-enabled
            social engineering attacks. Employing technologies, the KYE process
            verifies the facial and audio profiles of participants, ensuring
            authenticity and integrity without depending on machine learning
            models. This targeted approach offers a sustainable, real-time
            defense against potential cyber threats.
          </h4>
        </div>
      </div>
      <div class="horizontal-align">
        <CardUpload />
      </div>
    </div>
  </div></body
>

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
    transition-delay: 1s;

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
    font-size: 2.5em;
    margin-top: 20px;
    margin-bottom: 20px;
    font-weight: 800;
    width: 40%;
    position: relative;
    color: #d8ecf8;
    background-color: linear-gradient(0deg, #9dc3f7 0, #39434e 100%);
    background-clip: text;
    -webkit-background-clip: text;
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
    position: relative;
  }
  .solution::before {
    content: "";
    display: block;
    height: 100px;
    pointer-events: none;
  }

  .solution h3 {
    font-size: 1.5em;
    position: relative;
    width: fit-content;
    margin: auto;
    margin-top: 20px;
    color: #d8ecf8;
    text-shadow: 0 2px 16px rgba(174, 207, 242, 0.24);
    background: linear-gradient(0deg, #d8ecf8 0, #39434e 100%);
    background-clip: text;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .solution h4 {
    color: white;
    font-size: 20px;
    margin-top: 20px;
    margin-bottom: 20px;
    font-weight: 100;
  }

  .content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .solution h3.subt::before,
  .solution h3.subt::after {
    position: absolute;
    top: 60%;
    display: block;
    content: "";
    width: 5em;
    height: 1px;
    opacity: 0.5;
  }

  .solution h3.subt::before {
    background: linear-gradient(-90deg, #9dc3f7 0%, transparent 100%);
    right: 120%;
    top: 50%;
  }
  .solution h3.subt::after {
    background: linear-gradient(90deg, #9dc3f7 0%, transparent 100%);
    left: 120%;
    top: 50%;
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
  .meeting-add {
    width: 350px;
    height: 416px;
  }

  .card-info-wrapper-apps {
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

  .card-image-meeting-add {
    align-content: center;
    display: flex;
    justify-content: center;
  }

  .card-image-apps img {
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

  .horizontal-align {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap: 20px;
  }

  /* -- ↓ ↓ ↓ some responsiveness ↓ ↓ ↓ -- */

  @media (max-width: 1000px) {
    body {
      align-items: flex-start;
      overflow: auto;
    }
    .content {
      justify-content: center;
      align-items: center;
      justify-self: center;
    }
    .heroT {
      justify-content: center;
      margin: 20px;
      height: 50%;
      padding: 10px;
    }
    .heroT h1 {
      font-size: 35px;
      justify-self: center;
      justify-content: center;
      margin: 20px;
      text-align: center;
    }
    .info-card {
      width: 90%;
      padding-top: 70px;
    }
    .rhetorical {
      flex-direction: column;
    }
    .rhetorical h2 {
      width: 85%;
    }

    .rhetorical p {
      width: 85%;
    }

    #cards {
      max-width: 1000px;
      padding: 10px 0px;
      flex-direction: column;
      gap: 10px;
      align-items: center;
      justify-content: center;
      justify-self: center;
    }

    .card {
      flex-shrink: 1;
      width: calc(50% - 4px);
    }
  }

  @media (max-width: 500px) {
    .card {
      width: 90%;
    }

    .solution h3 {
      font-size: 30px;
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
