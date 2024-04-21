<script>
  const uploadStatic = "/uploadStatic.png";
  const uploadAnim = "/upload.gif";
  const profileStatic = "/profileStatic.png";

  let currentImage = uploadStatic;
  let timeoutId;

  function handleMouseOver() {
    currentImage = uploadAnim;
    timeoutId = setTimeout(() => {
      currentImage = profileStatic;
    }, 3000); // Change this to the duration of your GIF
  }

  function handleMouseOut() {
    clearTimeout(timeoutId);
    if (currentImage !== profileStatic) {
      currentImage = uploadStatic;
    }
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
    class="card profile-creation"
    on:mouseover={handleMouseOver}
    on:focus={handleMouseOver}
    on:mouseout={handleMouseOut}
    on:blur={handleMouseOut}
    role="presentation"
  >
    <div class="card-content">
      <div class="card-image-profile-creation">
        <img src={currentImage} alt="Upload animation" />
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
    justify-self: center;
    max-width: 916px;
  }

  #cards:hover > .card::after {
    opacity: 1;
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
    color: white;
  }
</style>
