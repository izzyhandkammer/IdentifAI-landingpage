<script>
  const logo = "/white_logo.png";
  const twitter = "/twitter.png";
  const linkedin = "/linkedin.png";
</script>

<header>
  <div class="header-left">
    <h1>
      <a href="https://www.landing.identifai.info/"
        ><img src={logo} alt="logo" /></a
      >
    </h1>
  </div>
  <div class="header-right">
    <a href="/team"> Team </a>
    <a href="/contact"> Contact </a>
    <a href="https://identifai.substack.com/" target="_blank"> Blog </a>
    <a
      href="https://calendly.com/d/cpw3-4qv-vc6/identifai-demo?month=2024-04"
      target="_blank"
    >
      <button id="buttons" class="glow-button">Schedule a Demo</button></a
    >
  </div>
</header>
<slot />
<footer class="layout-footer">
  <div class="footer-left">
    <p>COPYRIGHT © 2023 IDENTIFAI, INC - ALL RIGHTS RESERVED.</p>
    <a
      href="https://app.termly.io/document/privacy-policy/78de9a51-4bc1-47e2-95bf-465ff0cb2b39"
      target="_blank">PRIVACY POLICY</a
    >
    <a
      href="https://app.termly.io/document/terms-of-service/970ce6ce-a4fb-4f2e-b3af-cac13b1b668f"
      target="_blank">TERMS OF USE</a
    >
  </div>
  <div class="footer-right">
    <a href="https://twitter.com/identifAI_" target="_blank"
      ><img src={twitter} alt="twitter" /></a
    >
    <a
      href="https://www.linkedin.com/company/identifai-llc/?lipi=urn%3Ali%3Apage%3Ad_flagship3_search_srp_all%3BAnUAoZ9eTvq4EYVWSKn3UQ%3D%3D"
      target="_blank"><img src={linkedin} alt="linkedin" /></a
    >
  </div>
</footer>

<style>
  * {
    transition: all 0.3s;
  }
  header {
    width: 100%;
    max-width: 100%;
    min-height: 5rem;
    display: flex;
    flex-direction: row;
    background-color: transparent;
    align-items: center;
    position: relative;
  }

  header:after {
    content: "";
    display: block;
    height: 1px; /* adjust as needed */
    width: 100%;
    background: radial-gradient(white 30%, transparent 70%);
    position: absolute;
    bottom: 0;
  }

  h1 {
    color: white;
    font-size: 1.5rem;
    font-weight: 500;
    display: flex;
    align-items: center;
  }

  .header-left {
    padding-left: 20px;
    width: calc(50vw - 40px);
  }

  .header-right {
    width: calc(50vw - 20px);
    display: flex;
    justify-content: end;
    flex-direction: row;
    gap: 20px;
    margin: auto;
    vertical-align: center;
    font-family: "Syne";
  }
  .header-right a {
    color: white;
    text-decoration: none;
    align-self: center;
    opacity: 0.6;
  }

  .header-right a:hover {
    opacity: 1;
  }

  img {
    max-height: 20px;
  }

  footer {
    width: 100%;
    max-width: 100%;
    min-height: 5rem;
    max-height: 80px;
    display: flex;
    flex-direction: row;
    background-color: transparent;
    align-items: center;
    position: relative;
    color: white;
    font-size: 0.8rem;
    padding-top: 20px;
  }
  footer:before {
    content: "";
    display: block;
    height: 1px; /* adjust as needed */
    width: 100%;
    background: radial-gradient(white 30%, transparent 70%);
    position: absolute;
    top: 0;
  }
  .footer-left {
    padding-left: 20px;
    width: calc(50vw - 40px);
    display: flex;
    flex-direction: inherit;
  }
  .footer-left a {
    color: white;
    text-decoration: underline;
    flex-direction: row;
    margin: auto;
    margin-left: 20px;
    margin-right: 20px;
  }
  .footer-right {
    width: calc(50vw - 20px);
    display: flex;
    justify-content: end;
    color: white;
  }
  .footer-right img {
    max-height: 25px;
    opacity: 0.5;
    margin: 10px;
  }
  .footer-right img:hover {
    opacity: 0.7;
  }

  .glow-button {
    font-weight: 500;
    padding: 10px 20px;
    border: 1px solid #d0afe5;
    border-radius: 5px;
    font-family: "Syne";
    font-weight: 500;
    background: white;
    color: black;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 4px 100px 50px #55556b;
  }

  .glow-button:hover {
    box-shadow: 0 0 15px 3px #d0afe5;
    opacity: 0.9;
    background-color: #1e0e34;
    color: white;
  }
</style>
