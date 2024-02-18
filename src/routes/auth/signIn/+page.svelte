
<script>
  import { supabase } from '$lib/supabaseClient';
  import { goto } from '$app/navigation';

  let email = '';
  let password = '';

  async function signIn() {
    const { user, error } = await supabase.auth.signIn({ email, password });
    if (error) {
      alert(error.message);
    } else {
      goto('/profile'); // Redirect to profile page or wherever you like
    }
  }
  
</script>
  
  <style>
    .login-container {
      display: flex;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      background: #f7f7f7;
    }
  
    .login-box {
      background: #fff;
      padding: 2rem;
      border-radius: 8px;
      box-shadow: 0 8px 16px rgba(0,0,0,0.1);
      width: 100%;
      max-width: 400px;
      text-align: center;
      margin: 1rem;
    }
  
    .login-title {
      font-size: 1.5rem;
      color: #333;
      margin-bottom: 1.5rem;
    }
  
    input[type="email"],
    input[type="password"] {
      width: calc(100% - 2rem);
      padding: 1rem;
      margin-bottom: 1rem;
      border: 1px solid #ccc;
      border-radius: 4px;
      box-sizing: border-box;
    }
  
  
    .login-button {
      width: calc(100% - 2rem);
      padding: 1rem;
      background-color: rgb(103, 133, 178); /* Red color for club names */
      color: white;
      border: none;
      border-radius: 4px;
      margin-bottom: 1rem;
      cursor: pointer;
    }
  
    .login-button:hover {
      background-color: #555;
    }
  
    .login-footer {
      font-size: 0.9rem;
      margin-bottom: 1rem;
    }
  
    .sign-up-link {
        color: rgb(103, 133, 178); /* Red color for club names */
      text-decoration: none;
    }
  
    
    a{
        color: rgb(103, 133, 178); /* Red color for club names */
    }

    .back-button {
        border: none;
        background: url('/chevron-left.svg') no-repeat center / contain;
        width: 24px; /* Width of the button */
        height: 24px; /* Height of the button */
        cursor: pointer;
        padding: 0;
        position: absolute;
        top: 1rem;
        left: 1rem;
    }
  </style>
  
  <div class="login-container">
    
    <div class="login-box">
      <a href="/"><button class="back-button"></button></a>
      <div class="login-title">Ready to <i>thrive</i>?</div>
      <form on:submit|preventDefault={signIn}>
        <input type="email" bind:value={email} placeholder="Email" required>
        <input type="password" bind:value={password} placeholder="Password" required>
        <button class="login-button" type="submit">Sign In</button>
      </form>
      
      <div class="login-footer">
        Don’t have an account? <a href="/auth/signUp" class="sign-up-link">Sign up</a>
      </div>
    </div>
  </div>
  
  <!-- src/routes/auth/Signin.svelte -->