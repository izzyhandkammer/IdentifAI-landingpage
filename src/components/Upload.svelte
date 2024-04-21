<script>
  const uploadStatic = "/uploadStatic.png";
  const uploadAnim = "/upload.gif";
  const profileStatic = "/profile.png";
  let currentImage = uploadStatic;
  let timeoutId;

  function handleMouseOver() {
    currentImage = uploadAnim;
    timeoutId = setTimeout(() => {
      currentImage = profileStatic;
    }, 3500); // Make sure this matches the exact duration of your GIF
  }

  function handleMouseOut() {
    clearTimeout(timeoutId);
    if (currentImage !== profileStatic) {
      currentImage = uploadStatic;
    }
  }
</script>

<img
  src={currentImage}
  on:mouseover={handleMouseOver}
  on:focus={handleMouseOver}
  on:mouseout={handleMouseOut}
  on:blur={handleMouseOut}
  alt="upload"
/>

<style>
  img {
    width: 175%;
    height: 175%;
    transform: translate(0, -60px);
  }
</style>
