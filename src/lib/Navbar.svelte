<!-- src/lib/Navbar.svelte -->
<script>
    // You can include props or functions if needed
  </script>
  
  <style>
    .navbar {
      width: 100%;
      padding: 16px 0; /* Add vertical padding for the navbar */
      display: flex;
      justify-content: flex-end; /* Aligns the child element to the end of the container */
      align-items: center;
      background-color: #fff;
      position: fixed;
      top: 0;
      z-index: 10;
    }
  
    /* Placeholder for a logo or title, even if it's invisible, it helps with spacing */
  
    .signin-button {
      padding: 8px 16px;
      background-color: rgb(103, 133, 178);
      color: #fff;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-size: 1em;
      text-decoration: none;
      margin-right: 50px; /* Right margin for spacing from the edge */
    }
  
    /* Add a hover effect for the button */
    .signin-button:hover {
      background-color: rgb(72, 93, 123);
    }
  </style>
  
  <nav class="navbar">
    <a href="/auth/signIn"><button class="signin-button">Sign In</button></a>
  </nav>
  
  