<!-- src/routes/+page.svelte -->
<script lang="ts">
  import Hero from '$lib/components/Hero.svelte';
  import Story from '$lib/components/Story.svelte';

  let formData = {
    name: '',
    email: '',
    guests: '1',
    dietary: ''
  };

  let submitted = false;

  function handleSubmit(e: Event) {
    e.preventDefault();
    submitted = true;
    setTimeout(() => {
      submitted = false;
      formData = { name: '', email: '', guests: '1', dietary: '' };
    }, 4000);
  }
</script>

<svelte:head>
  <title>Walimatul Urus - Ain & Hidayat</title>
  <meta name="description" content="You are cordially invited to celebrate the wedding reception of Ain and Hidayat" />
</svelte:head>

<Hero 
  brideName="Ain"
  groomName="Hidayat"
  fullBrideName="Norain Binti Shahrudin"
  fullGroomName="Nur Hidayat Bin Suradi"
  date="19 February 2027"
  hijriDate="15 Rajab 1448 H"
  location="Forest Valley Hall, Jalan Permaisuri 10/6, Bandar Mahkota Cheras, 43200 Cheras, Selangor"
  eventType="Walimatul Urus"
/>

<Story />

<!-- Timeline Section -->
<section class="timeline-section">
  <div class="timeline-container">
    <h2>Atur Acara (Event Schedule)</h2>
    <p class="timeline-subtitle">A blessed day of celebration and unity</p>
    
    <div class="timeline">
      <div class="timeline-item">
        <div class="timeline-time">11:00 AM</div>
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <h3>Doors Open</h3>
          <p>Meal service begins</p>
        </div>
      </div>

      <div class="timeline-item">
        <div class="timeline-time">12:30 PM</div>
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <h3>Kehadiran Pengantin (Couple Arrival)</h3>
          <p>Ain & Hidayat arrive to celebration</p>
        </div>
      </div>

      <div class="timeline-item">
        <div class="timeline-time">12:30 PM - 3:00 PM</div>
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <h3>Bertandang (Photo Session)</h3>
          <p>Beautiful moments with family and friends</p>
        </div>
      </div>

      <div class="timeline-item">
        <div class="timeline-time">4:00 PM</div>
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <h3>Event Concludes</h3>
          <p>Terima kasih atas kehadiran Anda</p>
        </div>
      </div>
    </div>
  </div>

  <div class="floral-decoration timeline-floral">
    <svg viewBox="0 0 100 100" width="90" height="90">
      <g opacity="0.5">
        <circle cx="50" cy="20" r="10" fill="#ec4899"/>
        <circle cx="80" cy="50" r="10" fill="#ec4899"/>
        <circle cx="50" cy="80" r="10" fill="#ec4899"/>
        <circle cx="20" cy="50" r="10" fill="#ec4899"/>
        <circle cx="70" cy="30" r="8" fill="#fbbf24"/>
        <circle cx="70" cy="70" r="8" fill="#fbbf24"/>
        <circle cx="30" cy="70" r="8" fill="#fbbf24"/>
        <circle cx="30" cy="30" r="8" fill="#fbbf24"/>
        <circle cx="50" cy="50" r="12" fill="#ddd6fe" opacity="0.6"/>
      </g>
    </svg>
  </div>
</section>

<!-- Venue Section -->
<section class="venue-section">
  <div class="venue-container">
    <h2>Lokasi Majlis (Venue)</h2>
    <div class="venue-details">
      <div class="venue-card">
        <h3>Forest Valley Hall</h3>
        <p class="venue-address">Jalan Permaisuri 10/6</p>
        <p class="venue-address">Bandar Mahkota Cheras</p>
        <p class="venue-address">43200 Cheras, Selangor</p>
        <p class="venue-time">📅 19 February 2027</p>
        <p class="venue-time">🕐 11:00 AM - 4:00 PM</p>
        <p class="venue-time">RSVP Deadline: 17 December 2025</p>
      </div>

      <div class="hosts-card">
        <h3>Tuan Rumah (Hosts)</h3>
        <p class="host-names">Shahrudin Bin Ahmad</p>
        <p class="host-names">Norhayati Binti Hussin</p>
        <div class="host-divider"></div>
        <p class="host-label">Parents of the Bride</p>
      </div>
    </div>
  </div>

  <div class="floral-accent venue-floral">
    <svg viewBox="0 0 100 100" width="80" height="80">
      <g opacity="0.4">
        <circle cx="50" cy="30" r="8" fill="#fbbf24"/>
        <circle cx="50" cy="30" r="12" fill="none" stroke="#ec4899" stroke-width="1"/>
        <circle cx="65" cy="45" r="8" fill="#fbbf24"/>
        <circle cx="65" cy="45" r="12" fill="none" stroke="#ec4899" stroke-width="1"/>
        <circle cx="50" cy="65" r="8" fill="#fbbf24"/>
        <circle cx="50" cy="65" r="12" fill="none" stroke="#ec4899" stroke-width="1"/>
        <circle cx="35" cy="45" r="8" fill="#fbbf24"/>
        <circle cx="35" cy="45" r="12" fill="none" stroke="#ec4899" stroke-width="1"/>
        <circle cx="50" cy="45" r="10" fill="#ec4899"/>
      </g>
    </svg>
  </div>
</section>

<!-- RSVP Section -->
<section id="rsvp" class="rsvp-section">
  <div class="rsvp-container">
    {#if submitted}
      <div class="success-message">
        <div class="success-icon">
          <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <polyline points="20 6 9 17 4 12"></polyline>
          </svg>
        </div>
        <h3>Terima Kasih! Thank You!</h3>
        <p>We have received your RSVP. Jazakallah khair for your confirmation!</p>
      </div>
    {:else}
      <div class="rsvp-content">
        <h2>Wassalamualaikum Warahmatullahi Wabarakatuh</h2>
        <p class="rsvp-greeting">We cordially invite you to celebrate our special day</p>
        <p class="rsvp-subtitle">Kindly confirm your attendance</p>

        <form on:submit={handleSubmit} class="rsvp-form">
          <div class="form-group">
            <label for="name">Your Full Name *</label>
            <input
              type="text"
              id="name"
              bind:value={formData.name}
              required
              placeholder="Nama penuh anda / Your full name"
              aria-label="Your name"
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
              aria-label="Your email"
            />
          </div>

          <div class="form-group">
            <label for="guests">Number of Guests *</label>
            <select id="guests" bind:value={formData.guests} required aria-label="Number of guests">
              <option value="1">1 Guest</option>
              <option value="2">2 Guests</option>
              <option value="3">3 Guests</option>
              <option value="4">4 Guests</option>
              <option value="5">5 Guests</option>
            </select>
          </div>

          <div class="form-group">
            <label for="dietary">Dietary Restrictions or Allergies</label>
            <textarea
              id="dietary"
              bind:value={formData.dietary}
              placeholder="Sila beritahu kami jika ada keperluan khas / Please let us know any dietary requirements"
              rows="3"
              aria-label="Dietary restrictions"
            ></textarea>
          </div>

          <button type="submit" class="submit-btn">Konfirmasi Kehadiran (Confirm Attendance)</button>
          <p class="form-helper">* Required fields | * Medan yang diperlukan</p>
        </form>
      </div>
    {/if}

    <div class="rsvp-info">
      <div class="info-card">
        <h4>📧 Email Us</h4>
        <p>For inquiries / Untuk pertanyaan:</p>
        <a href="mailto:hello@aindhidayat.com">hello@aindhidayat.com</a>
      </div>
      <div class="info-card">
        <h4>📱 Contact</h4>
        <p>WhatsApp / Hubungi:</p>
        <a href="tel:+60123456789">(+60) 123-456-789</a>
      </div>
      <div class="info-card">
        <h4>📍 Directions</h4>
        <p>Navigate to venue:</p>
        <a href="https://maps.google.com" target="_blank" rel="noreferrer">View on Google Maps</a>
      </div>
    </div>
  </div>
</section>

<!-- Footer -->
<footer class="footer">
  <div class="footer-content">
    <div class="footer-section">
      <h4>Ain & Hidayat</h4>
      <p>19 February 2027</p>
      <p class="hijri-date">15 Rajab 1448 H</p>
    </div>
    <div class="footer-section">
      <p class="footer-doa">Semoga pernikahan ini menjadi jalan menuju kebahagiaan dunia dan akhirat</p>
      <p>&copy; 2025 Walimatul Urus Ain & Hidayat. All rights reserved.</p>
    </div>
    <div class="footer-section">
      <div class="social-links">
        <a href="https://facebook.com" target="_blank" rel="noreferrer" aria-label="Facebook">f</a>
        <a href="https://instagram.com" target="_blank" rel="noreferrer" aria-label="Instagram">@</a>
        <a href="https://wa.me/60123456789" target="_blank" rel="noreferrer" aria-label="WhatsApp">💬</a>
      </div>
    </div>
  </div>
</footer>

<style>
  /* Timeline Section */
  .timeline-section {
    position: relative;
    width: 100%;
    padding: 120px 20px;
    background: linear-gradient(135deg, #ffffff 0%, #f8f7ff 100%);
    border-top: 1px solid #f0f0f0;
  }

  .timeline-container {
    max-width: 800px;
    margin: 0 auto;
  }

  .timeline-section h2 {
    font-size: 48px;
    font-weight: 300;
    color: #1f2937;
    text-align: center;
    margin: 0 0 12px 0;
    letter-spacing: -0.5px;
  }

  .timeline-subtitle {
    text-align: center;
    color: #6b7280;
    font-size: 16px;
    margin: 0 0 60px 0;
  }

  .timeline {
    position: relative;
    padding: 20px 0;
  }

  .timeline::before {
    content: '';
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    width: 2px;
    height: 100%;
    background: linear-gradient(180deg, transparent, #d1d5db, transparent);
  }

  .timeline-item {
    margin-bottom: 40px;
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    gap: 20px;
    align-items: center;
  }

  .timeline-item:nth-child(odd) .timeline-time {
    text-align: right;
  }

  .timeline-item:nth-child(even) .timeline-time {
    text-align: left;
    grid-column: 3;
  }

  .timeline-item:nth-child(even) .timeline-content {
    grid-column: 1;
  }

  .timeline-time {
    font-weight: 600;
    color: #ec4899;
    font-size: 18px;
  }

  .timeline-dot {
    width: 16px;
    height: 16px;
    background: #ec4899;
    border: 4px solid #ffffff;
    border-radius: 50%;
    margin: 0 auto;
    box-shadow: 0 0 0 2px #f0f0f0;
  }

  .timeline-content {
    background: #ffffff;
    padding: 20px;
    border-radius: 8px;
    border: 1px solid #f0f0f0;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
  }

  .timeline-content h3 {
    margin: 0 0 8px 0;
    font-size: 16px;
    font-weight: 600;
    color: #1f2937;
  }

  .timeline-content p {
    margin: 0;
    font-size: 14px;
    color: #6b7280;
  }

  .timeline-floral {
    position: absolute;
    bottom: 40px;
    right: 40px;
    opacity: 0.3;
    animation: float 6s ease-in-out infinite;
  }

  /* Venue Section */
  .venue-section {
    position: relative;
    width: 100%;
    padding: 100px 20px;
    background: linear-gradient(180deg, #f8f7ff 0%, #fff5f7 100%);
    border-top: 1px solid #f0f0f0;
  }

  .venue-container {
    max-width: 1000px;
    margin: 0 auto;
  }

  .venue-section h2 {
    font-size: 48px;
    font-weight: 300;
    color: #1f2937;
    text-align: center;
    margin: 0 0 60px 0;
    letter-spacing: -0.5px;
  }

  .venue-details {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    gap: 40px;
  }

  .venue-card,
  .hosts-card {
    background: #ffffff;
    padding: 40px;
    border-radius: 12px;
    box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08);
    border: 1px solid #f0f0f0;
    transition: all 0.3s ease;
  }

  .venue-card:hover,
  .hosts-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 24px rgba(236, 72, 153, 0.15);
    border-color: #ec4899;
  }

  .venue-card h3,
  .hosts-card h3 {
    font-size: 24px;
    font-weight: 600;
    color: #1f2937;
    margin: 0 0 16px 0;
  }

  .venue-address {
    font-size: 15px;
    color: #6b7280;
    margin: 0 0 8px 0;
    line-height: 1.6;
  }

  .venue-time {
    font-size: 14px;
    color: #ec4899;
    font-weight: 500;
    margin: 12px 0 0 0;
  }

  .host-names {
    font-size: 16px;
    font-weight: 600;
    color: #1f2937;
    margin: 8px 0;
  }

  .host-divider {
    width: 40px;
    height: 2px;
    background: linear-gradient(90deg, #ec4899, #fbbf24);
    margin: 16px 0;
  }

  .host-label {
    font-size: 13px;
    color: #9ca3af;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    margin: 0;
  }

  .venue-floral {
    position: absolute;
    top: 40px;
    right: 60px;
    opacity: 0.3;
    animation: float 5s ease-in-out infinite;
  }

  /* RSVP Section */
  .rsvp-section {
    width: 100%;
    padding: 120px 20px;
    background: linear-gradient(180deg, #fff5f7 0%, #ffffff 100%);
    border-top: 1px solid #f0f0f0;
  }

  .rsvp-container {
    max-width: 700px;
    margin: 0 auto;
  }

  .rsvp-content {
    background: #ffffff;
    padding: 60px 40px;
    border-radius: 12px;
    box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08);
    border: 1px solid #f0f0f0;
    margin-bottom: 40px;
  }

  .rsvp-content h2 {
    font-size: 28px;
    font-weight: 400;
    color: #ec4899;
    text-align: center;
    margin: 0 0 12px 0;
    letter-spacing: 0.5px;
  }

  .rsvp-greeting {
    text-align: center;
    color: #1f2937;
    font-size: 18px;
    font-weight: 500;
    margin: 0 0 8px 0;
  }

  .rsvp-subtitle {
    text-align: center;
    color: #6b7280;
    font-size: 15px;
    margin: 0 0 40px 0;
  }

  .success-message {
    background: #ffffff;
    padding: 60px 40px;
    border-radius: 12px;
    text-align: center;
    box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08);
    border: 1px solid #f0f0f0;
    margin-bottom: 40px;
  }

  .success-icon {
    width: 64px;
    height: 64px;
    background: #f0fdf4;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto 20px;
    color: #16a34a;
  }

  .success-message h3 {
    font-size: 24px;
    color: #1f2937;
    margin: 0 0 12px 0;
  }

  .success-message p {
    color: #6b7280;
    font-size: 16px;
    margin: 0;
  }

  .rsvp-form {
    display: flex;
    flex-direction: column;
    gap: 24px;
  }

  .form-group {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .form-group label {
    font-size: 14px;
    font-weight: 600;
    color: #1f2937;
    letter-spacing: 0.3px;
  }

  .form-group input,
  .form-group select,
  .form-group textarea {
    padding: 12px 16px;
    border: 1px solid #e5e7eb;
    border-radius: 6px;
    font-family: 'Poppins', sans-serif;
    font-size: 14px;
    color: #1f2937;
    transition: all 0.3s ease;
    background: #ffffff;
  }

  .form-group input:focus,
  .form-group select:focus,
  .form-group textarea:focus {
    outline: none;
    border-color: #ec4899;
    box-shadow: 0 0 0 3px rgba(236, 72, 153, 0.1);
  }

  .form-group input::placeholder,
  .form-group textarea::placeholder {
    color: #d1d5db;
  }

  .submit-btn {
    padding: 14px 32px;
    background: linear-gradient(135deg, #ec4899 0%, #db2777 100%);
    color: #ffffff;
    border: none;
    border-radius: 6px;
    font-family: 'Poppins', sans-serif;
    font-size: 15px;
    font-weight: 600;
    letter-spacing: 0.5px;
    cursor: pointer;
    transition: all 0.3s ease;
    text-transform: uppercase;
    margin-top: 8px;
  }

  .submit-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(236, 72, 153, 0.3);
  }

  .submit-btn:active {
    transform: scale(0.98);
  }

  .form-helper {
    text-align: center;
    font-size: 12px;
    color: #9ca3af;
    margin: -16px 0 0 0;
  }

  .rsvp-info {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 24px;
  }

  .info-card {
    background: #ffffff;
    padding: 24px;
    border-radius: 8px;
    border: 1px solid #f0f0f0;
    text-align: center;
  }

  .info-card h4 {
    font-size: 16px;
    font-weight: 600;
    color: #1f2937;
    margin: 0 0 8px 0;
  }

  .info-card p {
    font-size: 13px;
    color: #6b7280;
    margin: 0 0 8px 0;
  }

  .info-card a {
    color: #ec4899;
    text-decoration: none;
    font-weight: 600;
    font-size: 14px;
    transition: color 0.3s ease;
  }

  .info-card a:hover {
    color: #db2777;
  }

  /* Footer */
  .footer {
    background: #1f2937;
    color: #ffffff;
    padding: 60px 20px;
    border-top: 1px solid #374151;
  }

  .footer-content {
    max-width: 1200px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 40px;
    text-align: center;
  }

  .footer-section h4 {
    font-size: 18px;
    font-weight: 600;
    margin: 0 0 8px 0;
  }

  .footer-section p {
    font-size: 14px;
    color: #d1d5db;
    margin: 0;
  }

  .hijri-date {
    font-size: 13px;
    color: #9ca3af;
  }

  .footer-doa {
    font-size: 13px;
    font-style: italic;
    color: #9ca3af;
    margin-bottom: 12px;
  }

  .social-links {
    display: flex;
    gap: 16px;
    justify-content: center;
  }

  .social-links a {
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 50%;
    color: #ffffff;
    text-decoration: none;
    transition: all 0.3s ease;
    font-weight: 600;
    font-size: 18px;
  }

  .social-links a:hover {
    background: #ec4899;
    transform: translateY(-2px);
  }

  @keyframes float {
    0%, 100% {
      transform: translateY(0px);
    }
    50% {
      transform: translateY(-20px);
    }
  }

  @media (max-width: 768px) {
    .timeline::before {
      left: 0;
      transform: translateX(0);
    }

    .timeline-item {
      grid-template-columns: 1fr;
      margin-bottom: 30px;
    }

    .timeline-item:nth-child(odd) .timeline-time,
    .timeline-item:nth-child(even) .timeline-time {
      text-align: left;
      grid-column: 1;
    }

    .timeline-item:nth-child(even) .timeline-content {
      grid-column: 1;
    }

    .timeline-dot {
      position: absolute;
      left: -8px;
      top: 25px;
    }

    .timeline-content {
      margin-left: 24px;
    }

    .rsvp-content {
      padding: 40px 24px;
    }

    .rsvp-section {
      padding: 60px 20px;
    }

    .timeline-section {
      padding: 60px 20px;
    }

    .venue-section {
      padding: 60px 20px;
    }

    .timeline-floral {
      display: none;
    }

    .venue-floral {
      display: none;
    }

    .venue-section h2 {
      font-size: 36px;
    }

    .rsvp-content h2 {
      font-size: 24px;
    }
  }
</style>
