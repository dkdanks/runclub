<!-- src/routes/profile/Setup.svelte -->
<script>
  import { supabase } from '$lib/supabaseClient';
  import { goto } from '$app/navigation';

  let profile = {
    name: '',
    dateOfBirth: '',
    runFrequency: 'flexible', // 'fixed' for specific days and times
    runDay: 'Monday',
    runTime: '6 AM',
    runLocation: '5km', // or 'current' for current location
    distancePreference: '5km',
    isFlexibleDistance: false,
    speed: 5,
    mainGoal: 'social', // or 'training'
  };

  async function createProfile() {
    const { data, error } = await supabase.from('profiles').insert([profile]);

    if (error) {
      console.error('Error creating profile:', error);
      alert('There was an error saving your profile.');
    } else {
      console.log('Profile created:', data);
      goto('/dashboard'); // Redirect to the dashboard or next step
    }
  }
</script>
<style>
    .form-container {
      display: flex;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      background-color: #f7f7f7;
    }
  
    .form-box {
      background-color: #fff;
      padding: 2rem;
      border-radius: 8px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      width: 100%;
      max-width: 400px;
      margin: 1rem auto;
    }
  
    label {
      display: block;
      color: #333;
      margin-bottom: 0.5rem;
    }
  
    input, select {
      width: 100%;
      padding: 10px;
      margin-bottom: 1rem;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
  
    .button-group button {
      padding: 10px 20px;
      border: 1px solid rgb(103, 133, 178);
      background-color: #fff;
      color: rgb(103, 133, 178);
      margin-right: 10px;
      cursor: pointer;
    }
  
    .button-group button.active {
      background-color: rgb(103, 133, 178);
      color: #fff;
    }
  
    .submit-button {
      width: 100%;
      padding: 10px;
      background-color: rgb(103, 133, 178);
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
  </style>
  
  <div class="form-container">
    <div class="form-box">
      <form on:submit|preventDefault={createProfile}>
        <label for="name">Name</label>
        <input id="name" type="text" bind:value={profile.name} placeholder="Your Name" required>
  
        <label for="dateOfBirth">Date of Birth</label>
        <input id="dateOfBirth" type="date" bind:value={profile.dateOfBirth} required>
        <label for="runFrequency">When will you run?</label>
        <select id="runFrequency" bind:value={profile.runFrequency}>
          <option value="flexible">I'm flexible</option>
          <option value="fixed">Fixed Schedule</option>
        </select>
      
        {#if profile.runFrequency === 'fixed'}
          <label for="runDay">Which day?</label>
          <select id="runDay" bind:value={profile.runDay}>
            <option value="Monday">Every Monday</option>
            <!-- Add other days of the week as needed -->
          </select>
      
          <label for="runTime">At what time?</label>
          <select id="runTime" bind:value={profile.runTime}>
            <option value="6 AM">6 AM</option>
            <!-- Add other times as needed -->
          </select>
        {/if}
      
        <label for="runLocation">Where will you run?</label>
        <select id="runLocation" bind:value={profile.runLocation}>
          <option value="5km">Within 5km</option>
          <option value="current">Current Location</option>
        </select>
      
        <label for="distancePreference">Distance</label>
        <select id="distancePreference" bind:value={profile.distancePreference}>
          <option value="<5km">5km</option>
          <option value="5km">5km</option>
          <option value="10km">10km</option>
          <option value="15km">15km</option>
          <!-- Add other distance options as needed -->
        </select>
        <input id="isFlexibleDistance" type="checkbox" bind:checked={profile.isFlexibleDistance}>
        <label for="isFlexibleDistance">I'm flexible</label>
      
        <label for="speed">Speed</label>
        <input id="speed" type="range" min="1" max="10" bind:value={profile.speed}>
      
        <!-- Add your other form fields here -->
  
        <div class="button-group">
          <button type="button" class:active={profile.mainGoal === 'social'} on:click={() => profile.mainGoal = 'social'}>Social</button>
          <button type="button" class:active={profile.mainGoal === 'training'} on:click={() => profile.mainGoal = 'training'}>Training</button>
        </div>
  
        <button type="submit" class="submit-button">Continue</button>
      </form>
    </div>
  </div>
