<script>
  import { onMount } from 'svelte';

  let showQRCode = false;

  const toggleQRCode = () => {
    showQRCode = !showQRCode;
  };

  onMount(() => {
    // Load the Stripe buy-button.js script dynamically
    const script = document.createElement('script');
    script.src = 'https://js.stripe.com/v3/buy-button.js';
    script.async = true;
    document.head.appendChild(script);
  });
</script>

<style>
  /* Common styles for both light and dark themes */
  :global(body) {
    font-family: Arial, sans-serif;
    text-align: center;
    background-color: #412a61; /* Darker purple for the entire page */
    margin: 0;
    padding: 0;
    color: #fff; /* White text */
  }

  .container {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    background-color: #412a61; /* Darker purple for the container */
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
    border-radius: 5px;
    color: #fff; /* White text */
  }

  h1 {
    font-size: 28px;
  }

  .logo {
    max-width: 200px;
    margin: 20px auto;
    display: block;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    margin-bottom: 10px;
  }

  a {
    text-decoration: none;
    font-weight: bold;
    color: #9aabe5; /* Lighter purple for links */
    font-size: 18px; /* Increase link font size */
  }

  a:hover {
    text-decoration: underline;
  }

  /* Light theme */
  .light-theme {
    background-color: #412a61; /* Darker purple for the entire page */
    color: #fff; /* White text */
  }

  /* Dark theme */
  .dark-theme {
    background-color: #333; /* You can adjust this if needed */
    color: #fff;
  }

  /* Stripe button styles */
  stripe-buy-button {
    margin-bottom: 20px;
  }

  /* QR Code styles */
  .qr-code {
    display: none;
    margin-top: 20px;
  }

  .show-qr-code {
    display: block;
  }

  .qr-image {
    max-width: 200px; /* Adjust the maximum width as needed */
    width: 100%;
    height: auto;
  }

  /* Customize the toggle button */
  .toggle-button {
    font-size: 16px; /* Reduce button font size */
    padding: 8px 12px; /* Adjust button padding */
    background-color: #9aabe5; /* Lighter purple for the button */
    color: #fff; /* White text for the button */
    cursor: pointer;
  }
</style>

<main class="container light-theme">
  <header>
    <h1>StripeJS with Svelte</h1>
    <a href="https://github.com/mattmajestic/stripejs-starter" target="_blank">GitHub</a>
    <a href="https://svelte.dev/tutorial" target="_blank">Svelte Tutorials</a>
  </header>

  <stripe-buy-button
    buy-button-id="buy_btn_1OE057BY7L5WREAJ6K34t1rV"
    publishable-key="update-with-your-stripe-credentials"
  >
  </stripe-buy-button>

  <div class="line-break"></div>

  <button on:click={toggleQRCode} class="toggle-button">
    {showQRCode ? 'Hide QR Code' : 'Show QR Code'}
  </button>

  {#if showQRCode}
    <div class="qr-code show-qr-code">
      <img src="donate.png" alt="Stripe QR Code" class="qr-image" />
    </div>
  {/if}
</main>
