<script>
  const uploadStatic = "/uploadStatic.png";
  const uploadAnim = "/upload.gif";
  const profileStatic = "/profileStatic.png";

  const mobileGif = "/mobileView.gif";
  const mobileStatic = "/mobileStatic.png";

  let currentImageUpload = uploadStatic;
  let timeoutIdUpload;

  let currentImageMobile = mobileStatic;
  let timeoutIdMobile;

  function handleMouseOverUpload() {
    currentImageUpload = uploadAnim;
    timeoutIdUpload = setTimeout(() => {
      currentImageUpload = profileStatic;
    }, 3000); // Change this to the duration of your GIF
  }

  function handleMouseOverMobile() {
    currentImageMobile = mobileGif;
    timeoutIdMobile = setTimeout(() => {
      currentImageMobile = mobileStatic;
    }, 3000); // Change this to the duration of your GIF
  }

  function handleMouseOutUpload() {
    clearTimeout(timeoutIdUpload);
    if (currentImageUpload !== profileStatic) {
      currentImageUpload = uploadStatic;
    }
  }

  function handleMouseOutMobile() {
    clearTimeout(timeoutIdMobile);
    currentImageMobile = mobileStatic;
  }

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

<div
  id="cards"
  bind:this={cards}
  on:mousemove={handleMouseMove}
  role="presentation"
>
  <div
    class="card mobile"
    on:mouseover={handleMouseOverMobile}
    on:focus={handleMouseOverMobile}
    on:mouseout={handleMouseOutMobile}
    on:blur={handleMouseOutMobile}
    role="presentation"
  >
    <div class="card-content">
      <div class="card-image-mobile">
        <img src={currentImageMobile} alt="mobile" />
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
  <div
    class="card profile-creation"
    on:mouseover={handleMouseOverUpload}
    on:focus={handleMouseOverUpload}
    on:mouseout={handleMouseOutUpload}
    on:blur={handleMouseOutUpload}
    role="presentation"
  >
    <div class="card-content">
      <div class="card-image-profile-creation">
        <img src={currentImageUpload} alt="Upload animation" />
      </div>
      <div class="card-info-wrapper-profile-creation">
        <div class="card-info">
          <div class="card-info-title">
            <h3>
              Create profiles for your employees, business associates, and more
            </h3>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  /* -- ↓ ↓ ↓ card effects ↓ ↓ ↓ -- */

  #cards {
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    justify-self: center;
    max-width: 916px;
    gap: 8px;
  }

  #cards:hover > .card::after {
    opacity: 1;
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

  .card {
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 10px;
    cursor: pointer;
    display: flex;
    position: relative;
    transition: transform 0.3s ease-in-out;
  }

  .profile-creation {
    width: 550px;
    height: 416px;
  }

  .mobile {
    width: 350px;
    height: 416px;
  }

  .card-info-wrapper-profile-creation {
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

  .card-image-mobile {
    align-content: center;
    display: flex;
    justify-content: center;
  }

  .card-image-mobile img {
    height: 80%;
    width: auto;
    max-height: 416px;
    transform: scale(0.8);
    transition: transform 0.3s ease-in-out;
    user-select: none;
    opacity: 0.8;
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

  .card-image-profile-creation {
    align-content: center;
    display: flex;
    justify-content: center;
    height: 300px;
  }

  .card-image-profile-creation img {
    width: 100%;
    height: 100%;
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
</style>
