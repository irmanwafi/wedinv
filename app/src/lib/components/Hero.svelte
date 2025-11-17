<!-- src/lib/components/Hero.svelte -->
<script>
  import { onMount } from 'svelte';
  
  export let groomName = "Alexander";
  export let brideName = "Isabella";
  export let date = "December 14, 2024";
  export let location = "The Grand Ballroom, Italy";

  let mounted = false;

  onMount(() => {
    mounted = true;
  });
</script>

<svelte:head>
  <title>{groomName} & {brideName}'s Wedding</title>
  <meta name="description" content="Join us in celebrating the wedding of {brideName} and {groomName}" />
</svelte:head>

<section class="hero-section">
  <!-- Background -->
  <div class="hero-bg"></div>
  
  <!-- Decorative circles -->
  <div class="decoration decoration-1"></div>
  <div class="decoration decoration-2"></div>
  
  <!-- Content -->
  <div class="hero-content">
    <div class="content-wrapper">
      <!-- Subtitle -->
      <p class="subtitle {mounted ? 'show' : ''}">The celebration of love</p>
      
      <!-- Main heading -->
      <div class="names-container {mounted ? 'show' : ''}">
        <h1 class="bride-name">{brideName}</h1>
        <div class="ampersand-divider">
          <div class="line"></div>
          <span>&</span>
          <div class="line"></div>
        </div>
        <h2 class="groom-name">{groomName}</h2>
      </div>
      
      <!-- Date and Location -->
      <div class="event-details {mounted ? 'show' : ''}">
        <p class="event-date">{date}</p>
        <p class="event-location">{location}</p>
      </div>
      
      <!-- CTA Button -->
      <div class="cta-container {mounted ? 'show' : ''}">
        <a href="#rsvp" class="cta-button">
          Explore Celebration
          <span class="arrow">→</span>
        </a>
      </div>
      
      <!-- Scroll indicator -->
      <div class="scroll-indicator {mounted ? 'show' : ''}">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <polyline points="6 9 12 15 18 9"></polyline>
        </svg>
      </div>
    </div>
  </div>
</section>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
  }

  .hero-section {
    position: relative;
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    background: #ffffff;
  }

  .hero-bg {
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, #ffffff 0%, #f8f7ff 50%, #fff5f7 100%);
    z-index: 0;
  }

  /* Decorative circles */
  .decoration {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    opacity: 0.5;
    z-index: 1;
  }

  .decoration-1 {
    width: 600px;
    height: 600px;
    background: radial-gradient(circle, rgba(236, 72, 153, 0.2) 0%, transparent 70%);
    top: -200px;
    right: -200px;
  }

  .decoration-2 {
    width: 500px;
    height: 500px;
    background: radial-gradient(circle, rgba(236, 72, 153, 0.15) 0%, transparent 70%);
    bottom: -150px;
    left: -150px;
  }

  .hero-content {
    position: relative;
    z-index: 10;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 40px 20px;
  }

  .content-wrapper {
    text-align: center;
    max-width: 1000px;
    width: 100%;
  }

  /* Subtitle */
  .subtitle {
    font-size: 13px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: #9ca3af;
    margin-bottom: 40px;
    font-weight: 400;
    opacity: 0;
    animation: fadeInDown 0.8s ease-out 0.2s forwards;
  }

  .subtitle.show {
    opacity: 1;
  }

  /* Names */
  .names-container {
    margin-bottom: 50px;
    opacity: 0;
    animation: fadeInScale 1s ease-out 0.4s forwards;
  }

  .names-container.show {
    opacity: 1;
  }

  .bride-name {
    font-size: clamp(48px, 10vw, 96px);
    font-weight: 300;
    color: #1f2937;
    letter-spacing: -1px;
    margin: 0;
    line-height: 1;
  }

  .ampersand-divider {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 24px;
    margin: 30px 0;
  }

  .ampersand-divider .line {
    flex: 1;
    max-width: 120px;
    height: 1px;
    background: linear-gradient(90deg, transparent, #d1d5db, transparent);
  }

  .ampersand-divider span {
    font-size: clamp(36px, 6vw, 56px);
    color: #d1d5db;
    font-weight: 300;
  }

  .groom-name {
    font-size: clamp(48px, 10vw, 96px);
    font-weight: 300;
    color: #1f2937;
    letter-spacing: -1px;
    margin: 0;
    line-height: 1;
  }

  /* Event Details */
  .event-details {
    margin-bottom: 60px;
    opacity: 0;
    animation: fadeInUp 0.8s ease-out 0.6s forwards;
  }

  .event-details.show {
    opacity: 1;
  }

  .event-date {
    font-size: 16px;
    color: #4b5563;
    letter-spacing: 0.5px;
    margin: 0 0 12px 0;
    font-weight: 400;
  }

  .event-location {
    font-size: 12px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: #9ca3af;
    margin: 0;
    font-weight: 400;
  }

  /* CTA Button */
  .cta-container {
    margin-bottom: 60px;
    opacity: 0;
    animation: fadeInUp 0.8s ease-out 0.8s forwards;
  }

  .cta-container.show {
    opacity: 1;
  }

  .cta-button {
    display: inline-flex;
    align-items: center;
    gap: 12px;
    padding: 16px 48px;
    background: #1f2937;
    color: #ffffff;
    text-decoration: none;
    font-size: 15px;
    font-weight: 500;
    letter-spacing: 0.5px;
    border: 2px solid #1f2937;
    border-radius: 2px;
    transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    cursor: pointer;
    position: relative;
    overflow: hidden;
  }

  .cta-button::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: #000000;
    transition: left 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    z-index: -1;
  }

  .cta-button:hover {
    color: #ffffff;
    border-color: #000000;
    letter-spacing: 1px;
  }

  .cta-button:hover::before {
    left: 0;
  }

  .cta-button .arrow {
    display: inline-block;
    transition: transform 0.3s ease;
    font-size: 18px;
  }

  .cta-button:hover .arrow {
    transform: translateX(4px);
  }

  .cta-button:active {
    transform: scale(0.98);
  }

  /* Scroll indicator */
  .scroll-indicator {
    position: absolute;
    bottom: 40px;
    left: 50%;
    transform: translateX(-50%);
    color: #d1d5db;
    opacity: 0;
    animation: fadeInUp 0.8s ease-out 1s forwards, bounce 2s ease-in-out 2s infinite;
  }

  .scroll-indicator.show {
    opacity: 1;
  }

  .scroll-indicator svg {
    width: 24px;
    height: 24px;
  }

  /* Animations */
  @keyframes fadeInDown {
    from {
      opacity: 0;
      transform: translateY(-20px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  @keyframes fadeInUp {
    from {
      opacity: 0;
      transform: translateY(20px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  @keyframes fadeInScale {
    from {
      opacity: 0;
      transform: scale(0.95);
    }
    to {
      opacity: 1;
      transform: scale(1);
    }
  }

  @keyframes bounce {
    0%, 100% {
      transform: translateX(-50%) translateY(0);
    }
    50% {
      transform: translateX(-50%) translateY(8px);
    }
  }

  /* Responsive */
  @media (max-width: 768px) {
    .hero-section {
      height: auto;
      min-height: 100vh;
      padding: 60px 20px;
    }

    .decoration-1 {
      width: 300px;
      height: 300px;
      top: -100px;
      right: -100px;
    }

    .decoration-2 {
      width: 250px;
      height: 250px;
      bottom: -80px;
      left: -80px;
    }

    .subtitle {
      margin-bottom: 30px;
      font-size: 12px;
    }

    .names-container {
      margin-bottom: 40px;
    }

    .ampersand-divider {
      gap: 16px;
      margin: 20px 0;
    }

    .ampersand-divider .line {
      max-width: 80px;
    }

    .event-details {
      margin-bottom: 50px;
    }

    .cta-container {
      margin-bottom: 40px;
    }

    .scroll-indicator {
      bottom: 20px;
    }
  }
</style>
