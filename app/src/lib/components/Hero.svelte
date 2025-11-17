<!-- src/lib/components/Hero.svelte -->
<script>
  import { onMount } from 'svelte';
  
  export let brideName = 'Ain';
  export let groomName = 'Hidayat';
  export let fullBrideName = 'Norain Binti Shahrudin';
  export let fullGroomName = 'Nur Hidayat Bin Suradi';
  export let date = '19 February 2027';
  export let hijriDate = '15 Rajab 1448 H';
  export let location = 'Forest Valley Hall, Jalan Permaisuri 10/6, Bandar Mahkota Cheras, 43200 Cheras, Selangor';
  export let eventType = 'Walimatul Urus';

  let mounted = false;
  let daysLeft = 0;
  let hoursLeft = 0;
  let minutesLeft = 0;

  onMount(() => {
    mounted = true;
    calculateCountdown();
    const interval = setInterval(calculateCountdown, 1000);
    return () => clearInterval(interval);
  });

  function calculateCountdown() {
    const weddingDate = new Date('February 19, 2027').getTime();
    const now = new Date().getTime();
    const distance = weddingDate - now;

    if (distance > 0) {
      daysLeft = Math.floor(distance / (1000 * 60 * 60 * 24));
      hoursLeft = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      minutesLeft = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
    }
  }
</script>

<svelte:head>
  <title>Walimatul Urus {brideName} & {groomName}</title>
  <meta name="description" content="You are cordially invited to celebrate the Walimatul Urus of {fullBrideName} and {fullGroomName}" />
</svelte:head>

<section class="hero-section">
  <!-- Floral decorations top -->
  <div class="floral-decoration floral-top-left">
    <svg viewBox="0 0 100 100" width="120" height="120">
      <circle cx="50" cy="50" r="8" fill="#ec4899"/>
      <circle cx="50" cy="25" r="12" fill="#ec4899"/>
      <circle cx="75" cy="35" r="12" fill="#ec4899"/>
      <circle cx="75" cy="65" r="12" fill="#ec4899"/>
      <circle cx="50" cy="75" r="12" fill="#ec4899"/>
      <circle cx="25" cy="65" r="12" fill="#ec4899"/>
      <circle cx="25" cy="35" r="12" fill="#ec4899"/>
      <circle cx="40" cy="50" r="6" fill="#fbbf24"/>
      <circle cx="60" cy="50" r="6" fill="#fbbf24"/>
    </svg>
  </div>

  <div class="floral-decoration floral-top-right">
    <svg viewBox="0 0 100 100" width="100" height="100">
      <path d="M50 20 Q70 30 75 50 Q70 70 50 80 Q30 70 25 50 Q30 30 50 20" fill="#ddd6fe" opacity="0.6"/>
      <circle cx="50" cy="50" r="8" fill="#ec4899"/>
    </svg>
  </div>

  <!-- Background -->
  <div class="hero-bg"></div>
  
  <!-- Decorative circles -->
  <div class="decoration decoration-1"></div>
  <div class="decoration decoration-2"></div>
  
  <!-- Content -->
  <div class="hero-content">
    <div class="content-wrapper">
      <!-- Subtitle with Malay greeting -->
      <p class="subtitle {mounted ? 'show' : ''}">Assalamualaikum Warahmatullahi Wabarakatuh</p>
      
      <!-- Event Type -->
      <p class="event-type {mounted ? 'show' : ''}">{eventType}</p>
      
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

      <!-- Full Names -->
      <div class="full-names {mounted ? 'show' : ''}">
        <p class="full-name bride-full">{fullBrideName}</p>
        <p class="full-name groom-full">{fullGroomName}</p>
      </div>
      
      <!-- Countdown Timer -->
      <div class="countdown-container {mounted ? 'show' : ''}">
        <div class="countdown-label">Days until celebration</div>
        <div class="countdown-display">
          <div class="countdown-item">
            <span class="countdown-value">{daysLeft}</span>
            <span class="countdown-label-small">Days</span>
          </div>
          <div class="countdown-divider">:</div>
          <div class="countdown-item">
            <span class="countdown-value">{hoursLeft.toString().padStart(2, '0')}</span>
            <span class="countdown-label-small">Hours</span>
          </div>
          <div class="countdown-divider">:</div>
          <div class="countdown-item">
            <span class="countdown-value">{minutesLeft.toString().padStart(2, '0')}</span>
            <span class="countdown-label-small">Minutes</span>
          </div>
        </div>
      </div>
      
      <!-- Date and Location -->
      <div class="event-details {mounted ? 'show' : ''}">
        <p class="event-date">{date}</p>
        <p class="hijri-display">{hijriDate}</p>
        <p class="event-location">{location}</p>
        <p class="rsvp-deadline">RSVP by: 17 December 2025</p>
      </div>
      
      <!-- CTA Button -->
      <div class="cta-container {mounted ? 'show' : ''}">
        <a href="#rsvp" class="cta-button">
          RSVP Now
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

  /* Floral decorations */
  .floral-decoration {
    position: absolute;
    opacity: 0.6;
    z-index: 2;
  }

  .floral-top-left {
    top: 40px;
    left: 40px;
    animation: float 4s ease-in-out infinite;
  }

  .floral-top-right {
    top: 60px;
    right: 50px;
    animation: float 5s ease-in-out infinite 0.5s;
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
    color: #ec4899;
    margin-bottom: 12px;
    font-weight: 500;
    opacity: 0;
    animation: fadeInDown 0.8s ease-out 0.2s forwards;
  }

  .subtitle.show {
    opacity: 1;
  }

  /* Event Type */
  .event-type {
    font-size: 16px;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    color: #6b7280;
    margin-bottom: 32px;
    font-weight: 500;
    opacity: 0;
    animation: fadeInDown 0.8s ease-out 0.3s forwards;
  }

  .event-type.show {
    opacity: 1;
  }

  /* Names */
  .names-container {
    margin-bottom: 20px;
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

  /* Full Names */
  .full-names {
    margin-bottom: 32px;
    opacity: 0;
    animation: fadeInUp 0.8s ease-out 0.5s forwards;
  }

  .full-names.show {
    opacity: 1;
  }

  .full-name {
    font-size: 14px;
    color: #6b7280;
    margin: 4px 0;
    font-weight: 400;
    letter-spacing: 0.3px;
  }

  .bride-full {
    font-weight: 500;
    color: #4b5563;
  }

  .groom-full {
    font-weight: 500;
    color: #4b5563;
  }

  /* Countdown Timer */
  .countdown-container {
    margin: 50px 0;
    opacity: 0;
    animation: fadeInUp 0.8s ease-out 0.6s forwards;
  }

  .countdown-container.show {
    opacity: 1;
  }

  .countdown-label {
    font-size: 12px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: #9ca3af;
    margin-bottom: 16px;
    font-weight: 500;
  }

  .countdown-display {
    display: flex;
    align-items: flex-end;
    justify-content: center;
    gap: 12px;
    flex-wrap: wrap;
  }

  .countdown-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    background: rgba(236, 72, 153, 0.08);
    padding: 16px 20px;
    border-radius: 8px;
    border: 1px solid rgba(236, 72, 153, 0.2);
    min-width: 70px;
  }

  .countdown-value {
    font-size: 32px;
    font-weight: 600;
    color: #ec4899;
    line-height: 1;
    margin-bottom: 4px;
  }

  .countdown-label-small {
    font-size: 11px;
    letter-spacing: 1px;
    text-transform: uppercase;
    color: #9ca3af;
    font-weight: 500;
  }

  .countdown-divider {
    font-size: 24px;
    color: #d1d5db;
    margin: 0 4px;
    margin-bottom: 20px;
  }

  /* Event Details */
  .event-details {
    margin: 30px 0 60px;
    opacity: 0;
    animation: fadeInUp 0.8s ease-out 0.8s forwards;
  }

  .event-details.show {
    opacity: 1;
  }

  .event-date {
    font-size: 16px;
    color: #4b5563;
    letter-spacing: 0.5px;
    margin: 0 0 8px 0;
    font-weight: 500;
  }

  .hijri-display {
    font-size: 13px;
    color: #9ca3af;
    margin: 0 0 16px 0;
    font-weight: 400;
    letter-spacing: 0.5px;
  }

  .event-location {
    font-size: 12px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: #9ca3af;
    margin: 0 0 12px 0;
    font-weight: 400;
  }

  .rsvp-deadline {
    font-size: 12px;
    letter-spacing: 1px;
    color: #ec4899;
    margin: 0;
    font-weight: 600;
  }

  /* CTA Button */
  .cta-container {
    margin-bottom: 60px;
    opacity: 0;
    animation: fadeInUp 0.8s ease-out 1s forwards;
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
    animation: fadeInUp 0.8s ease-out 1.2s forwards, bounce 2s ease-in-out 2s infinite;
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

  @keyframes float {
    0%, 100% {
      transform: translateY(0px);
    }
    50% {
      transform: translateY(-15px);
    }
  }

  /* Responsive */
  @media (max-width: 768px) {
    .hero-section {
      height: auto;
      min-height: 100vh;
      padding: 60px 20px;
    }

    .floral-top-left {
      width: 60px;
      height: 60px;
    }

    .floral-top-right {
      width: 50px;
      height: 50px;
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
      margin-bottom: 30px;
    }

    .ampersand-divider {
      gap: 16px;
      margin: 20px 0;
    }

    .ampersand-divider .line {
      max-width: 80px;
    }

    .countdown-container {
      margin: 30px 0;
    }

    .countdown-display {
      gap: 8px;
    }

    .countdown-item {
      padding: 12px 14px;
      min-width: 60px;
    }

    .countdown-value {
      font-size: 24px;
    }

    .event-details {
      margin: 20px 0 40px;
    }

    .cta-container {
      margin-bottom: 40px;
    }

    .scroll-indicator {
      bottom: 20px;
    }
  }
</style>
