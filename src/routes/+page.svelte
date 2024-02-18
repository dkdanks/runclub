<meta name="viewport" content="width=device-width, initial-scale=1.0">

<script>
    // JavaScript section can be used for dynamic data or page interactions
  import Navbar from "$lib/Navbar.svelte";

  </script>
  
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
    

    body {
      margin: 0;
      padding: 0;
      font-family: "adobe-caslon-pro", serif;
      background: #fff;
      color: #333;
    }
    .page-container {
    padding-top: 80px;
    }
  
    .page-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      padding: 50px;
    }
  
    .title {
      font-size: 64px;
      font-weight: 700;
      color: #000;
      margin-bottom: 32px;
    }
  
    .subtitle {
      font-size: 24px;
      color: #555;
      margin-bottom: 16px;
    }
  
    .address {
      font-size: 18px;
      color: #666;
      margin-bottom: 40px;
    }
  
    .club-name {
      font-size: 30px;
      font-family: "adobe-caslon-pro", serif;
      color: rgb(103, 133, 178); /* Red color for club names */
      margin: 8px 0;
      font-weight: 700;
    }
  
    /* Add more styles as needed */
  </style>
  <Navbar />
  <body>
    <div class="page-container">
        <div class="title">THRIVE</div>
        <div class="subtitle">A Community for Runners</div>
        <div class="address">Find Your Running Club</div>
        <!-- Replace these placeholders with actual data -->
        <!-- <div class="club-name">Morning Runners</div>
        <div class="club-name">Urban Trailblazers</div>
        <div class="club-name">Sunset Sprinters</div> -->
        <!-- ... add more clubs as needed -->
      </div>
  </body>
  
  