<!-- src/routes/+page.svelte -->
<script>
  import Hero from '$lib/components/Hero.svelte';
</script>

<svelte:head>
  <title>Sarah & John's Wedding</title>
  <meta name="description" content="You are invited to celebrate the wedding of Sarah and John" />
</svelte:head>

<Hero 
  brideName="Sarah"
  groomName="John"
  date="Saturday, December 14, 2024"
  location="The Grand Ballroom, New York"
/>

<!-- Details Section -->
<section class="details-section">
  <div class="details-container">
    <div class="detail-card">
      <div class="detail-icon">
        <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
          <rect x="3" y="4" width="18" height="18" rx="2" ry="2"></rect>
          <line x1="16" y1="2" x2="16" y2="6"></line>
          <line x1="8" y1="2" x2="8" y2="6"></line>
          <line x1="3" y1="10" x2="21" y2="10"></line>
        </svg>
      </div>
      <h3>Date & Time</h3>
      <p>December 14, 2024</p>
      <p class="detail-sub">6:00 PM</p>
    </div>

    <div class="detail-card">
      <div class="detail-icon">
        <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
          <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path>
          <circle cx="12" cy="10" r="3"></circle>
        </svg>
      </div>
      <h3>Venue</h3>
      <p>The Grand Ballroom</p>
      <p class="detail-sub">New York, NY</p>
    </div>

    <div class="detail-card">
      <div class="detail-icon">
        <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
          <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path>
        </svg>
      </div>
      <h3>Contact</h3>
      <p>For inquiries</p>
      <p class="detail-sub">hello@example.com</p>
    </div>
  </div>
</section>

<!-- Footer -->
<footer class="footer">
  <div class="footer-content">
    <p>&copy; 2024 Sarah & John. All rights reserved.</p>
  </div>
</footer>

<style>
  .details-section {
    width: 100%;
    padding: 100px 20px;
    background: #ffffff;
    border-top: 1px solid #f0f0f0;
  }

  .details-container {
    max-width: 1200px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 40px;
  }

  .detail-card {
    text-align: center;
    padding: 40px 30px;
    background: linear-gradient(135deg, #ffffff 0%, #f8f7ff 100%);
    border: 1px solid #f0f0f0;
    border-radius: 4px;
    transition: all 0.3s ease;
  }

  .detail-card:hover {
    border-color: #e5e7eb;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.05);
    transform: translateY(-4px);
  }

  .detail-icon {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 60px;
    height: 60px;
    margin: 0 auto 24px;
    background: #f3f4f6;
    border-radius: 4px;
    color: #1f2937;
    transition: all 0.3s ease;
  }

  .detail-card:hover .detail-icon {
    background: #e5e7eb;
  }

  .detail-card h3 {
    font-size: 18px;
    font-weight: 500;
    color: #1f2937;
    margin: 0 0 8px 0;
  }

  .detail-card p {
    font-size: 16px;
    color: #4b5563;
    margin: 0;
  }

  .detail-card p.detail-sub {
    font-size: 14px;
    color: #9ca3af;
    margin-top: 4px;
  }

  .footer {
    width: 100%;
    padding: 40px 20px;
    background: #1f2937;
    color: #ffffff;
    text-align: center;
    border-top: 1px solid #374151;
  }

  .footer-content p {
    font-size: 14px;
    color: #d1d5db;
    margin: 0;
  }

  @media (max-width: 768px) {
    .details-section {
      padding: 60px 20px;
    }

    .details-container {
      gap: 30px;
    }

    .detail-card {
      padding: 30px 20px;
    }
  }
</style>