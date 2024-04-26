<script>
    import { onMount } from 'svelte';
    const videoAnim = "/videocall.mp4";
    const videoPoster = "/videoposter.png";
    let video;
    onMount(() => {
        video.play(); // Ensures the video plays on mount, considering autoplay might fail.
    });
    function pauseVideo() {
        video.pause();
    }
    function playVideo() {
        video.play();
    }
</script>

<style>
    .video-container {
        max-width: 800px; /* Adjust this to fit your layout */
        margin: auto;
        padding: 8% 0; /* Padding above and below the video */
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.5); /* Optional: adds shadow for depth */
        border-radius: 20px; /* Rounded corners */
        overflow: hidden; /* Ensures the video corners are clipped to the border radius */
    }
    video {
        width: 100%; /* Ensure video fills the container */
        height: auto; /* Maintain aspect ratio */
        display: block; /* Removes bottom space/gap */
        border-radius: 30px; /* Consistent rounded corners */
    }
</style>

<div class="video-container">
    <video
        autoplay
        loop
        muted
        poster={videoPoster}
        src={videoAnim}
        bind:this={video}
        on:mouseenter={pauseVideo}
        on:mouseleave={playVideo}>
        <track kind="captions" />
    </video>
</div>
