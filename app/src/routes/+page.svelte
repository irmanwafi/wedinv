<!-- src/routes/+page.svelte -->
<script lang="ts">
  import Hero from '$lib/components/Hero.svelte';
  
  let formData = {
    name: '',
    email: '',
    guests: '1'
  };

  let submitted = false;
  let currentTab = 'invitation';

  function handleSubmit(e: Event) {
    e.preventDefault();
    submitted = true;
    setTimeout(() => {
      submitted = false;
      formData = { name: '', email: '', guests: '1' };
    }, 3000);
  }

  function addToCalendar() {
    const event = {
      title: 'Wedding Celebration - Ain & Hidayat',
      description: 'You are invited to the wedding of Norain Shahrudin & Nur Hidayat Suradi',
      location: 'Forest Valley Hall, Jalan Permaisuri 10/6, Bandar Mahkota Cheras, 43200 Cheras, Selangor',
      startTime: '2027-02-19T11:00:00',
      endTime: '2027-02-19T16:00:00'
    };

    const icsContent = `BEGIN:VCALENDAR
VERSION:2.0
PRODID:-//Ain & Hidayat Wedding//EN
BEGIN:VEVENT
UID:wedding-2027-${Date.now()}@aindhidayat.com
DTSTAMP:${new Date().toISOString().replace(/[-:]/g, '').split('.')[0]}Z
DTSTART:20270219T110000
DTEND:20270219T160000
SUMMARY:${event.title}
DESCRIPTION:${event.description}
LOCATION:${event.location}
END:VEVENT
END:VCALENDAR`;

    const blob = new Blob([icsContent], { type: 'text/calendar' });
    const url = window.URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url;
    a.download = 'wedding-invitation.ics';
    document.body.appendChild(a);
    a.click();
    window.URL.revokeObjectURL(url);
    document.body.removeChild(a);
  }
</script>

<svelte:head>
  <title>Wedding - Ain & Hidayat</title>
  <meta name="description" content="Wedding Celebration of Norain Shahrudin & Nur Hidayat Suradi" />
  <meta name="theme-color" content="#fdf2f8" />
</svelte:head>

<!-- Hero Section -->
<Hero 
  brideName="Ain"
  groomName="Hidayat"
  fullBrideName="Norain Shahrudin"
  fullGroomName="Nur Hidayat Suradi"
  date="19 February 2027"
  hijriDate="24 Rabiulawal 1448 H"
  location="Forest Valley Hall, Jalan Permaisuri 10/6, Bandar Mahkota Cheras, 43200 Cheras, Selangor"
  eventType="Wedding Celebration"
/>

<!-- Bride Gallery Section with Glossy Frames -->
<section class="bride-gallery-section">
  <div class="gallery-container">
    <h2 class="gallery-title">The Bride & Groom</h2>
    <div class="bride-gallery">
      <div class="gallery-item">
        <div class="glossy-frame">
          <img src="/bride-image/bride-holding-name-together.png" alt="Bride and Groom" />
        </div>
        <p class="image-caption">Together in Love</p>
      </div>
      <div class="gallery-item">
        <div class="glossy-frame">
          <img src="/bride-image/main-bride.png" alt="Bride" />
        </div>
        <p class="image-caption">The Beautiful Bride</p>
      </div>
      <div class="gallery-item">
        <div class="glossy-frame">
          <img src="/bride-image/bride-point-right.png" alt="Bride" />
        </div>
        <p class="image-caption">Elegance</p>
      </div>
    </div>
  </div>
</section>

<!-- Navigation Tabs -->
<nav class="nav-tabs">
  <div class="nav-container">
    <button 
      class="nav-tab {currentTab === 'invitation' ? 'active' : ''}"
      on:click={() => currentTab = 'invitation'}
    >
      Invitation
    </button>
    <button 
      class="nav-tab {currentTab === 'schedule' ? 'active' : ''}"
      on:click={() => currentTab = 'schedule'}
    >
      Schedule
    </button>
    <button 
      class="nav-tab {currentTab === 'location' ? 'active' : ''}"
      on:click={() => currentTab = 'location'}
    >
      Location
    </button>
    <button 
      class="nav-tab {currentTab === 'rsvp' ? 'active' : ''}"
      on:click={() => currentTab = 'rsvp'}
    >
      RSVP
    </button>
  </div>
</nav>

<!-- Invitation Card Section -->
{#if currentTab === 'invitation'}
<section id="invitation" class="invitation-section">
  <div class="card-container">
    <div class="invitation-card">
      <!-- Header -->
      <div class="card-header">
        <h3 class="card-title">Wedding Invitation</h3>
        <p class="card-subtitle">Celebration of Marriage</p>
      </div>

      <!-- Greeting -->
      <div class="card-greeting">
        <p>Assalamualaikum wbt & Warmest Greetings</p>
      </div>

      <!-- Parents -->
      <div class="parents-section">
        <p class="parent-name">Shahrudin Ahmad</p>
        <p class="parent-name">Norhayati Hussin</p>
      </div>

      <!-- Invitation Text -->
      <div class="invitation-text">
        <p>Together with joy and gratitude, we invite you to</p>
        <p class="invitation-titles">Attend the Marriage Celebration of</p>
      </div>

      <!-- Couple Names -->
      <div class="couple-names">
        <h2 class="couple-name">Norain Shahrudin</h2>
        <p class="ampersand">&</p>
        <h2 class="couple-name">Nur Hidayat Suradi</h2>
      </div>

      <!-- Date -->
      <div class="date-section">
        <div class="date-day">Saturday</div>
        <div class="date-main">19th February 2027</div>
        <div class="date-hijri">24 Rabiulawal 1448H</div>
      </div>

      <!-- Location Card -->
      <div class="location-card">
        <h4>VENUE</h4>
        <p>Forest Valley Hall</p>
        <p>Jalan Permaisuri 10/6</p>
        <p>Bandar Mahkota Cheras</p>
        <p>43200 Cheras, Selangor</p>
      </div>

      <!-- Schedule Card -->
      <div class="schedule-card">
        <h4>EVENT SCHEDULE</h4>
        <div class="schedule-item">
          <p class="schedule-label">Reception:</p>
          <p class="schedule-time">11:00 AM - 4:00 PM</p>
        </div>
        <div class="schedule-item">
          <p class="schedule-label">Couple Arrival:</p>
          <p class="schedule-time">12:30 PM</p>
        </div>
      </div>

      <!-- RSVP Notice -->
      <div class="rsvp-notice">
        <p>Please Confirm Your Attendance</p>
        <p>by 17th December 2025</p>
      </div>

      <!-- Action Buttons -->
      <div class="action-buttons">
        <button class="btn btn-calendar" on:click={addToCalendar}>
          📅 Add to Calendar
        </button>
        <button class="btn btn-rsvp" on:click={() => currentTab = 'rsvp'}>
          ✓ RSVP Now
        </button>
      </div>
    </div>
  </div>
</section>
{/if}

<!-- Schedule Section -->
{#if currentTab === 'schedule'}
<section class="content-section schedule-section">
  <div class="container">
    <h2>Event Schedule</h2>
    <p class="section-subtitle">A Glimpse of Our Special Day</p>

    <div class="schedule-timeline">
      <div class="timeline-item">
        <div class="timeline-marker">
          <div class="timeline-dot"></div>
        </div>
        <div class="timeline-content">
          <h3>11:00 AM</h3>
          <p class="timeline-label">Gates Open</p>
          <p class="timeline-description">Reception begins, welcome refreshments</p>
        </div>
      </div>

      <div class="timeline-item">
        <div class="timeline-marker">
          <div class="timeline-dot"></div>
        </div>
        <div class="timeline-content">
          <h3>12:30 PM</h3>
          <p class="timeline-label">Couple Arrival</p>
          <p class="timeline-description">Norain & Hidayat make their entrance</p>
        </div>
      </div>

      <div class="timeline-item">
        <div class="timeline-marker">
          <div class="timeline-dot"></div>
        </div>
        <div class="timeline-content">
          <h3>12:30 PM - 3:00 PM</h3>
          <p class="timeline-label">Photo Session</p>
          <p class="timeline-description">Memorable moments with family and friends</p>
        </div>
      </div>

      <div class="timeline-item">
        <div class="timeline-marker">
          <div class="timeline-dot"></div>
        </div>
        <div class="timeline-content">
          <h3>4:00 PM</h3>
          <p class="timeline-label">Closing Ceremony</p>
          <p class="timeline-description">Thank you for celebrating with us</p>
        </div>
      </div>
    </div>
  </div>
</section>
{/if}

<!-- Location Section -->
{#if currentTab === 'location'}
<section class="content-section location-section">
  <div class="container">
    <h2>Venue Information</h2>
    <p class="section-subtitle">Where We Celebrate</p>

    <div class="location-card-large">
      <div class="location-info">
        <h3>Forest Valley Hall</h3>
        <div class="location-details">
          <p><strong>Jalan Permaisuri 10/6</strong></p>
          <p>Bandar Mahkota Cheras</p>
          <p>43200 Cheras, Selangor</p>
        </div>
        <div class="location-meta">
          <p>📞 Available during business hours</p>
          <p>📍 Easily accessible from Kuala Lumpur</p>
        </div>
      </div>
      <div class="location-map">
        <iframe 
          title="Forest Valley Hall Location"
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3983.8234567890!2d101.6234567!3d3.1234567!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x31cc5e9e7f1f1f1f%3A0x1234567890abcdef!2sForest%20Valley%20Hall!5e0!3m2!1sen!2smy!4v1234567890"
          width="100%"
          height="300"
          style="border:0; border-radius: 12px;"
          allowfullscreen
          loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
        ></iframe>
      </div>
    </div>

    <div class="location-directions">
      <a href="https://maps.google.com/?q=Forest+Valley+Hall,+Jalan+Permaisuri+10/6,+Bandar+Mahkota+Cheras,+43200+Cheras,+Selangor" target="_blank" class="btn btn-primary">
        🗺️ View on Google Maps
      </a>
    </div>
  </div>
</section>
{/if}

<!-- RSVP Section -->
{#if currentTab === 'rsvp'}
<section class="content-section rsvp-section">
  <div class="container">
    <h2>Confirm Your Attendance</h2>
    <p class="section-subtitle">Please RSVP by 17th December 2025</p>

    {#if submitted}
      <div class="success-message">
        <div class="success-icon">✓</div>
        <h3>Thank You!</h3>
        <p>Your RSVP has been received. We look forward to celebrating with you!</p>
      </div>
    {:else}
      <form on:submit={handleSubmit} class="rsvp-form">
        <div class="form-group">
          <label for="name">Full Name *</label>
          <input
            type="text"
            id="name"
            bind:value={formData.name}
            required
            placeholder="Enter your name"
          />
        </div>

        <div class="form-group">
          <label for="email">Email Address *</label>
          <input
            type="email"
            id="email"
            bind:value={formData.email}
            required
            placeholder="your@email.com"
          />
        </div>

        <div class="form-group">
          <label for="guests">Number of Guests *</label>
          <select id="guests" bind:value={formData.guests} required>
            <option value="1">1 Guest</option>
            <option value="2">2 Guests</option>
            <option value="3">3 Guests</option>
            <option value="4">4 Guests</option>
            <option value="5">5 Guests</option>
          </select>
        </div>

        <button type="submit" class="btn btn-primary btn-large">Submit RSVP</button>
      </form>
    {/if}

    <div class="contact-info">
      <h4>Contact Us</h4>
      <p>📧 hello@aindhidayat.com</p>
      <p>📱 WhatsApp: <a href="https://wa.me/60123456789">(+60) 123-456-789</a></p>
    </div>
  </div>
</section>
{/if}

<!-- Footer -->
<footer class="footer">
  <div class="footer-content">
    <p>Ain & Hidayat | 19th February 2027 | 24 Rabiulawal 1448H</p>
    <p class="footer-doa">May this marriage be a path to happiness in both this world and the hereafter</p>
    <p class="footer-copyright">&copy; 2025 Wedding Celebration. All rights reserved.</p>
  </div>
</footer>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    background: linear-gradient(135deg, #fdf2f8 0%, #f3e8ff 50%, #fef3f8 100%);
    font-family: 'Poppins', sans-serif;
    overflow-x: hidden;
  }

  :global(html) {
    scroll-behavior: smooth;
    overflow-x: hidden;
  }

  /* Subtle Flower Background */
  :global(body)::before {
    content: '';
    position: fixed;
    top: 300px;
    right: -100px;
    width: 600px;
    height: 600px;
    background: url('/flower/flower.jpg') no-repeat center;
    background-size: contain;
    opacity: 0.06;
    pointer-events: none;
    z-index: 0;
    transform: rotate(45deg);
  }

  :global(body)::after {
    content: '';
    position: fixed;
    bottom: 50px;
    left: -150px;
    width: 550px;
    height: 550px;
    background: url('/flower/flower.jpg') no-repeat center;
    background-size: contain;
    opacity: 0.05;
    pointer-events: none;
    z-index: 0;
    transform: rotate(-25deg);
  }

  /* Bride Gallery Section - Glossy Theme */
  .bride-gallery-section {
    width: 100%;
    padding: 100px 20px;
    background: linear-gradient(135deg, rgba(253, 242, 248, 0.95) 0%, rgba(243, 232, 255, 0.95) 50%, rgba(254, 243, 248, 0.95) 100%);
    position: relative;
    z-index: 20;
    backdrop-filter: blur(10px);
  }

  .gallery-container {
    max-width: 1200px;
    margin: 0 auto;
  }

  .gallery-title {
    font-size: 48px;
    font-weight: 300;
    color: #1f2937;
    text-align: center;
    margin: 0 0 60px 0;
    letter-spacing: -0.5px;
  }

  .bride-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 40px;
    padding: 0 20px;
  }

  .gallery-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    animation: fadeInUp 0.8s ease-out forwards;
  }

  .gallery-item:nth-child(1) {
    animation-delay: 0.2s;
  }

  .gallery-item:nth-child(2) {
    animation-delay: 0.4s;
  }

  .gallery-item:nth-child(3) {
    animation-delay: 0.6s;
  }

  .glossy-frame {
    position: relative;
    width: 260px;
    height: 360px;
    background: linear-gradient(135deg, rgba(255, 255, 255, 0.98) 0%, rgba(255, 255, 255, 0.92) 100%);
    border-radius: 24px;
    padding: 18px;
    box-shadow: 
      0 20px 60px rgba(236, 72, 153, 0.2),
      0 0 0 1.5px rgba(255, 255, 255, 0.8) inset,
      inset 0 1px 1px rgba(255, 255, 255, 1),
      inset 0 -8px 16px rgba(0, 0, 0, 0.08),
      0 0 40px rgba(236, 72, 153, 0.1);
    backdrop-filter: blur(20px);
    overflow: hidden;
    transition: all 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
    border: 1px solid rgba(255, 255, 255, 0.6);
  }

  .glossy-frame:hover {
    transform: translateY(-12px) scale(1.03);
    box-shadow: 
      0 30px 80px rgba(236, 72, 153, 0.35),
      0 0 0 1.5px rgba(255, 255, 255, 0.9) inset,
      inset 0 1px 2px rgba(255, 255, 255, 1),
      inset 0 -8px 20px rgba(0, 0, 0, 0.12),
      0 0 60px rgba(236, 72, 153, 0.2);
  }

  .glossy-frame::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 40%;
    background: linear-gradient(180deg, rgba(255, 255, 255, 0.4) 0%, rgba(255, 255, 255, 0) 100%);
    pointer-events: none;
    z-index: 2;
  }

  .glossy-frame img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 16px;
    display: block;
  }

  .image-caption {
    margin-top: 16px;
    font-size: 14px;
    color: #6b7280;
    font-weight: 500;
    text-align: center;
    letter-spacing: 0.5px;
  }

  @keyframes fadeInUp {
    from {
      opacity: 0;
      transform: translateY(30px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  /* Navigation Tabs */
  .nav-tabs {
    position: sticky;
    top: 0;
    z-index: 50;
    background: linear-gradient(180deg, rgba(255, 255, 255, 0.98) 0%, rgba(255, 255, 255, 0.95) 100%);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid rgba(236, 72, 153, 0.1);
    padding: 0;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.05);
  }

  .nav-container {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    gap: 0;
    padding: 0;
  }

  .nav-tab {
    flex: 1;
    padding: 16px 20px;
    border: none;
    background: transparent;
    cursor: pointer;
    font-size: 14px;
    font-weight: 500;
    color: #6b7280;
    transition: all 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    border-bottom: 3px solid transparent;
    font-family: 'Poppins', sans-serif;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  .nav-tab:hover {
    color: #ec4899;
    background: rgba(236, 72, 153, 0.08);
    border-bottom-color: rgba(236, 72, 153, 0.3);
  }

  .nav-tab.active {
    color: #ec4899;
    border-bottom-color: #ec4899;
    background: rgba(236, 72, 153, 0.08);
  }

  /* Invitation Section */
  .invitation-section {
    width: 100%;
    padding: 60px 20px;
    background: linear-gradient(135deg, #fdf2f8 0%, #f3e8ff 100%);
    position: relative;
    z-index: 20;
  }

  .card-container {
    max-width: 600px;
    margin: 0 auto;
  }

  .invitation-card {
    background: linear-gradient(135deg, rgba(255, 255, 255, 0.98) 0%, rgba(255, 255, 255, 0.94) 100%);
    border-radius: 28px;
    padding: 50px 40px;
    box-shadow: 
      0 20px 70px rgba(236, 72, 153, 0.15),
      0 0 0 1.5px rgba(255, 255, 255, 0.7) inset,
      inset 0 1px 1px rgba(255, 255, 255, 1),
      inset 0 -8px 20px rgba(0, 0, 0, 0.08);
    backdrop-filter: blur(20px);
    text-align: center;
    border: 1px solid rgba(255, 255, 255, 0.5);
    transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  }

  .invitation-card:hover {
    box-shadow: 
      0 25px 90px rgba(236, 72, 153, 0.25),
      0 0 0 1.5px rgba(255, 255, 255, 0.8) inset,
      inset 0 1px 2px rgba(255, 255, 255, 1),
      inset 0 -8px 24px rgba(0, 0, 0, 0.1);
  }

  .card-header {
    margin-bottom: 30px;
  }

  .card-title {
    font-size: 28px;
    font-weight: 300;
    color: #1f2937;
    margin: 0;
    letter-spacing: 1px;
  }

  .card-subtitle {
    font-size: 14px;
    color: #9ca3af;
    margin: 8px 0 0 0;
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  .card-greeting {
    margin-bottom: 30px;
    padding-bottom: 30px;
    border-bottom: 1px solid rgba(236, 72, 153, 0.2);
  }

  .card-greeting p {
    font-size: 14px;
    color: #ec4899;
    margin: 0;
    letter-spacing: 0.5px;
    font-weight: 500;
  }

  .parents-section {
    margin-bottom: 30px;
  }

  .parent-name {
    font-size: 15px;
    font-weight: 600;
    color: #1f2937;
    margin: 8px 0;
  }

  .invitation-text {
    margin-bottom: 40px;
    line-height: 1.8;
  }

  .invitation-text p {
    font-size: 14px;
    color: #4b5563;
    margin: 8px 0;
  }

  .invitation-titles {
    font-weight: 600;
    color: #1f2937;
    letter-spacing: 0.5px;
  }

  .couple-names {
    margin-bottom: 40px;
  }

  .couple-name {
    font-size: 24px;
    font-weight: 500;
    color: #1f2937;
    margin: 12px 0;
    letter-spacing: 0.5px;
  }

  .ampersand {
    font-size: 20px;
    color: #ec4899;
    margin: 12px 0;
    font-weight: 300;
  }

  .date-section {
    margin-bottom: 40px;
    padding: 30px;
    background: linear-gradient(135deg, #fdf2f8 0%, #f3e8ff 100%);
    border-radius: 16px;
  }

  .date-day {
    font-size: 14px;
    color: #9ca3af;
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 8px;
  }

  .date-main {
    font-size: 28px;
    font-weight: 600;
    color: #1f2937;
    margin-bottom: 8px;
  }

  .date-hijri {
    font-size: 13px;
    color: #6b7280;
  }

  .location-card {
    background: linear-gradient(135deg, rgba(236, 72, 153, 0.08) 0%, rgba(236, 72, 153, 0.04) 100%);
    padding: 24px;
    border-radius: 16px;
    margin-bottom: 20px;
    text-align: left;
    border: 1px solid rgba(236, 72, 153, 0.15);
    backdrop-filter: blur(10px);
    transition: all 0.3s ease;
  }

  .location-card:hover {
    background: linear-gradient(135deg, rgba(236, 72, 153, 0.12) 0%, rgba(236, 72, 153, 0.06) 100%);
    border-color: rgba(236, 72, 153, 0.25);
  }

  .location-card h4 {
    font-size: 12px;
    text-transform: uppercase;
    letter-spacing: 1.5px;
    color: #ec4899;
    margin: 0 0 12px 0;
    font-weight: 600;
  }

  .location-card p {
    font-size: 14px;
    color: #4b5563;
    margin: 6px 0;
    line-height: 1.6;
  }

  .schedule-card {
    background: linear-gradient(135deg, rgba(236, 72, 153, 0.08) 0%, rgba(236, 72, 153, 0.04) 100%);
    padding: 24px;
    border-radius: 16px;
    margin-bottom: 30px;
    text-align: left;
    border: 1px solid rgba(236, 72, 153, 0.15);
    backdrop-filter: blur(10px);
    transition: all 0.3s ease;
  }

  .schedule-card:hover {
    background: linear-gradient(135deg, rgba(236, 72, 153, 0.12) 0%, rgba(236, 72, 853, 0.06) 100%);
    border-color: rgba(236, 72, 153, 0.25);
  }

  .schedule-card h4 {
    font-size: 12px;
    text-transform: uppercase;
    letter-spacing: 1.5px;
    color: #ec4899;
    margin: 0 0 16px 0;
    font-weight: 600;
  }

  .schedule-item {
    margin-bottom: 12px;
  }

  .schedule-label {
    font-size: 13px;
    font-weight: 600;
    color: #1f2937;
    margin: 0;
  }

  .schedule-time {
    font-size: 14px;
    color: #4b5563;
    margin: 4px 0 0 0;
  }

  .rsvp-notice {
    padding: 20px;
    background: rgba(236, 72, 153, 0.1);
    border-left: 4px solid #ec4899;
    border-radius: 8px;
    margin-bottom: 30px;
  }

  .rsvp-notice p {
    font-size: 14px;
    color: #4b5563;
    margin: 6px 0;
    text-align: center;
  }

  .action-buttons {
    display: flex;
    gap: 12px;
    flex-direction: column;
  }

  /* Content Sections */
  .content-section {
    padding: 80px 20px;
    position: relative;
    z-index: 20;
  }

  .container {
    max-width: 1000px;
    margin: 0 auto;
  }

  .content-section h2 {
    font-size: 48px;
    font-weight: 300;
    color: #1f2937;
    text-align: center;
    margin: 0 0 12px 0;
    letter-spacing: -0.5px;
  }

  .section-subtitle {
    text-align: center;
    color: #6b7280;
    font-size: 16px;
    margin: 0 0 60px 0;
  }

  /* Schedule Timeline */
  .schedule-section {
    background: linear-gradient(135deg, #fdf2f8 0%, #f3e8ff 100%);
  }

  .schedule-timeline {
    position: relative;
    display: flex;
    flex-direction: column;
    gap: 40px;
  }

  .schedule-timeline::before {
    content: '';
    position: absolute;
    left: 30px;
    top: 0;
    bottom: 0;
    width: 2px;
    background: linear-gradient(180deg, #ec4899, rgba(236, 72, 153, 0.2));
  }

  .timeline-item {
    position: relative;
    margin-left: 100px;
    padding: 24px;
    background: white;
    border-radius: 12px;
    box-shadow: 0 4px 16px rgba(0, 0, 0, 0.05);
  }

  .timeline-marker {
    position: absolute;
    left: -90px;
    top: 24px;
  }

  .timeline-dot {
    width: 28px;
    height: 28px;
    background: white;
    border: 3px solid #ec4899;
    border-radius: 50%;
    box-shadow: 0 0 0 2px #fdf2f8;
  }

  .timeline-item h3 {
    font-size: 18px;
    font-weight: 600;
    color: #1f2937;
    margin: 0 0 8px 0;
  }

  .timeline-label {
    font-size: 13px;
    color: #ec4899;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    font-weight: 600;
    margin: 0;
  }

  .timeline-description {
    font-size: 14px;
    color: #6b7280;
    margin: 4px 0 0 0;
  }

  /* Location Section */
  .location-section {
    background: linear-gradient(135deg, #f3e8ff 0%, #fdf2f8 100%);
  }

  .location-card-large {
    background: white;
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
    margin-bottom: 40px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0;
  }

  .location-info {
    padding: 40px;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .location-card-large h3 {
    font-size: 28px;
    font-weight: 600;
    color: #1f2937;
    margin: 0 0 24px 0;
  }

  .location-details p {
    font-size: 15px;
    color: #4b5563;
    margin: 8px 0;
    line-height: 1.6;
  }

  .location-details p strong {
    font-weight: 600;
    color: #1f2937;
  }

  .location-meta {
    margin-top: 24px;
    padding-top: 24px;
    border-top: 1px solid #e5e7eb;
  }

  .location-meta p {
    font-size: 13px;
    color: #6b7280;
    margin: 8px 0;
  }

  .location-map {
    background: #f9fafb;
  }

  .location-directions {
    text-align: center;
  }

  /* RSVP Section */
  .rsvp-section {
    background: linear-gradient(135deg, #fdf2f8 0%, #f3e8ff 100%);
  }

  .success-message {
    background: linear-gradient(135deg, rgba(255, 255, 255, 0.98) 0%, rgba(255, 255, 255, 0.94) 100%);
    border-radius: 24px;
    padding: 60px 40px;
    text-align: center;
    box-shadow: 
      0 15px 50px rgba(0, 0, 0, 0.1),
      0 0 0 1.5px rgba(255, 255, 255, 0.7) inset;
    backdrop-filter: blur(20px);
    max-width: 500px;
    margin: 40px auto;
    border: 1px solid rgba(255, 255, 255, 0.5);
  }

  .success-icon {
    width: 64px;
    height: 64px;
    background: linear-gradient(135deg, #d1fae5 0%, #a7f3d0 100%);
    color: #059669;
    font-size: 32px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    margin: 0 auto 24px;
    font-weight: 600;
    box-shadow: 0 8px 20px rgba(5, 150, 105, 0.25);
  }

  .success-message h3 {
    font-size: 28px;
    color: #1f2937;
    margin: 0 0 12px 0;
  }

  .success-message p {
    font-size: 15px;
    color: #6b7280;
    margin: 0;
  }

  .rsvp-form {
    background: linear-gradient(135deg, rgba(255, 255, 255, 0.98) 0%, rgba(255, 255, 255, 0.94) 100%);
    border-radius: 24px;
    padding: 40px;
    max-width: 500px;
    margin: 40px auto;
    box-shadow: 
      0 15px 50px rgba(236, 72, 153, 0.15),
      0 0 0 1.5px rgba(255, 255, 255, 0.7) inset;
    backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.5);
  }

  .form-group {
    margin-bottom: 24px;
  }

  .form-group label {
    display: block;
    font-size: 13px;
    font-weight: 600;
    color: #1f2937;
    margin-bottom: 8px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  .form-group input,
  .form-group select {
    width: 100%;
    padding: 12px 16px;
    border: 1.5px solid #e5e7eb;
    border-radius: 12px;
    font-size: 14px;
    font-family: 'Poppins', sans-serif;
    transition: all 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    box-sizing: border-box;
    background: linear-gradient(135deg, rgba(255, 255, 255, 0.9) 0%, rgba(255, 255, 255, 0.85) 100%);
  }

  .form-group input:focus,
  .form-group select:focus {
    outline: none;
    border-color: #ec4899;
    box-shadow: 0 0 0 4px rgba(236, 72, 153, 0.15), inset 0 1px 2px rgba(255, 255, 255, 0.5);
  }

  .contact-info {
    background: linear-gradient(135deg, rgba(255, 255, 255, 0.98) 0%, rgba(255, 255, 255, 0.94) 100%);
    border-radius: 24px;
    padding: 40px;
    max-width: 500px;
    margin: 40px auto;
    text-align: center;
    box-shadow: 
      0 15px 50px rgba(236, 72, 153, 0.15),
      0 0 0 1.5px rgba(255, 255, 255, 0.7) inset;
    backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.5);
  }

  .contact-info h4 {
    font-size: 18px;
    font-weight: 600;
    color: #1f2937;
    margin: 0 0 16px 0;
  }

  .contact-info p {
    font-size: 14px;
    color: #6b7280;
    margin: 8px 0;
  }

  .contact-info a {
    color: #ec4899;
    text-decoration: none;
    font-weight: 600;
  }

  /* Buttons */
  .btn {
    padding: 12px 24px;
    border: none;
    border-radius: 8px;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
    font-family: 'Poppins', sans-serif;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    text-decoration: none;
    display: inline-block;
    text-align: center;
  }

  .btn-primary {
    background: linear-gradient(135deg, #ec4899 0%, #d946a6 100%);
    color: white;
  }

  .btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(236, 72, 153, 0.3);
  }

  .btn-calendar {
    background: white;
    color: #ec4899;
    border: 2px solid #ec4899;
  }

  .btn-calendar:hover {
    background: rgba(236, 72, 153, 0.05);
  }

  .btn-rsvp {
    background: linear-gradient(135deg, #ec4899 0%, #d946a6 100%);
    color: white;
  }

  .btn-rsvp:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(236, 72, 153, 0.3);
  }

  .btn-large {
    width: 100%;
    padding: 14px 24px;
    font-size: 15px;
  }

  /* Footer */
  .footer {
    background: #1f2937;
    color: white;
    padding: 60px 20px;
    text-align: center;
    position: relative;
    z-index: 20;
  }

  .footer-content p {
    font-size: 14px;
    margin: 8px 0;
  }

  .footer-doa {
    font-size: 13px;
    color: #d1d5db;
    font-style: italic;
    margin: 16px 0 !important;
  }

  .footer-copyright {
    font-size: 12px;
    color: #9ca3af;
  }

  /* Responsive */
  @media (max-width: 768px) {
    .bride-gallery-section {
      padding: 60px 20px;
    }

    .gallery-title {
      font-size: 36px;
      margin-bottom: 40px;
    }

    .bride-gallery {
      grid-template-columns: 1fr;
      gap: 30px;
      padding: 0;
    }

    .glossy-frame {
      width: 100%;
      max-width: 260px;
      height: 360px;
      margin: 0 auto;
    }

    .nav-container {
      flex-wrap: wrap;
    }

    .nav-tab {
      flex: 0 1 50%;
      padding: 12px 16px;
      font-size: 12px;
    }

    .invitation-card {
      padding: 40px 24px;
    }

    .content-section h2 {
      font-size: 36px;
    }

    .schedule-timeline::before {
      left: 20px;
    }

    .timeline-item {
      margin-left: 70px;
      padding: 20px;
    }

    .timeline-marker {
      left: -60px;
    }

    .location-card-large {
      grid-template-columns: 1fr;
    }

    .location-map {
      height: 250px;
    }

    .rsvp-form {
      padding: 24px;
    }

    .couple-name {
      font-size: 20px;
    }

    .date-main {
      font-size: 24px;
    }

    .action-buttons {
      gap: 8px;
    }
  }

  @media (max-width: 480px) {
    .bride-gallery-section {
      padding: 40px 16px;
    }

    .gallery-title {
      font-size: 28px;
      margin-bottom: 30px;
    }

    .bride-gallery {
      gap: 24px;
    }

    .glossy-frame {
      width: 100%;
      max-width: 220px;
      height: 300px;
      padding: 16px;
    }

    .image-caption {
      font-size: 12px;
      margin-top: 12px;
    }

    .nav-tab {
      flex: 0 1 50%;
      padding: 10px 12px;
      font-size: 11px;
    }

    .invitation-card {
      padding: 30px 20px;
      border-radius: 16px;
    }

    .card-title {
      font-size: 24px;
    }

    .couple-name {
      font-size: 18px;
    }

    .location-card,
    .schedule-card {
      padding: 20px;
    }

    .content-section {
      padding: 60px 16px;
    }

    .timeline-item {
      margin-left: 60px;
    }

    .timeline-marker {
      left: -50px;
    }
  }
</style>
