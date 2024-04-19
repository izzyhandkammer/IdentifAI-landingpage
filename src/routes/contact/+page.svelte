<script>
  import Background from "../../components/Background.svelte";
  import Form from "../../components/Form.svelte";

  const favicon = "/eyecon.png";
</script>

<head>
  <title>Contact Us | IdentifAI</title>
  <link rel="icon" type="image/x-icon" src={favicon} />
</head>
<body>
  <Background />
  <div class="content">
    <h2>Get in Touch</h2>
    <Form />
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

  h2 {
    color: white;
    font-size: 50px;
    font-weight: 750;
    width: 40%;
    color: #9dc3f7;
    text-align: center;
    margin: auto;
  }

  .content {
    display: flex;
    flex-direction: column;
    gap: 10px;
    align-items: center;
    justify-content: center;
    margin-top: 50px;
  }
</style>
