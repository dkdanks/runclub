<!-- src/routes/auth/Signup.svelte -->
<script>
    import { supabase } from '$lib/supabaseClient';
    import { goto } from '$app/navigation';

    let email = '';
    let password = '';
  
    async function signUp() {
      const { data, error } = await supabase.auth.signUp({ email, password });
      if (error) {
        alert(error.message);
      } else {
        
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
          background: #989898; /* Darker box background */
          color: #f7f7f7; /* Light text */
          padding: 2rem;
          border-radius: 8px;
          box-shadow: 0 8px 16px rgba(255,255,255,0.1); /* Lighter shadow */
          width: 100%;
          max-width: 400px;
          text-align: center;
          margin: 1rem;
        }
      
        .login-title {
          font-size: 1.5rem;
          margin-bottom: 1.5rem;
        }
      
        input[type="email"],
        input[type="password"] {
          width: calc(100% - 2rem);
          padding: 1rem;
          margin-bottom: 1rem;
          border: 1px solid #aaa; /* Lighter border */
          background: #222; /* Dark input background */
          color: #f7f7f7; /* Light text */
          border-radius: 4px;
          box-sizing: border-box;
        }
      
        .login-button {
          width: calc(100% - 2rem);
          padding: 1rem;
          background-color: rgb(103, 133, 178); /* Lighter button background */
          color: #f7f7f7; /* Light text */
          border: none;
          border-radius: 4px;
          margin-bottom: 1rem;
          cursor: pointer;
        }
      
        .login-button:hover {
          background-color: #777; /* Hover state */
        }
      
        .login-footer {
          font-size: 0.9rem;
          margin-bottom: 1rem;
        }
      
        .sign-up-link {
          color: #f7f7f7; /* Light link color */
          text-decoration: none;
        }
      
        .back-button {
          border: none;
          background: url('/chevron-left.svg') no-repeat center / contain; /* Use an inverted chevron icon */
          width: 24px;
          height: 24px;
          cursor: pointer;
          padding: 0;
          position: absolute;
          top: 1rem;
          left: 1rem;
        }
      
        a {
          color: #f7f7f7; /* Light link color */
        }
      </style>
      
    
    <div class="login-container">
      <div class="login-box">
        <a href="/"><button class="back-button"></button></a>
        <div class="login-title">Ready to <i>thrive</i>?</div>
        <form on:submit|preventDefault={signUp}>
            <input type="email" bind:value={email} placeholder="Email" required>
            <input type="password" bind:value={password} placeholder="Password" required>
            <button class="login-button" type="submit">Sign Up</button>
          </form>
          
        
        <div class="login-footer">
          Already have an account? <a href="/auth/signIn" class="sign-up-link">Sign In</a>
        </div>
      </div>
    </div>