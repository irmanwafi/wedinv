<!-- src/lib/components/Story.svelte -->
<script>
  let stories = [
    {
      id: 1,
      title: "How We Met",
      description: "A chance encounter at a coffee shop turned into a lifelong connection. Sometimes the best stories start with the simplest moments.",
      image: "/bride-image/main-bride.png",
      date: "Summer 2020"
    },
    {
      id: 2,
      title: "Our Journey",
      description: "From that first coffee date to countless adventures, every moment has been special. We can't wait to share our joy with all of you.",
      image: "/bride-image/bride-holding-name-together.png",
      date: "2020 - 2024"
    },
    {
      id: 3,
      title: "The Proposal",
      description: "On a starlit evening, amidst whispered promises and endless love, the question was finally asked. And the answer was an instant, resounding yes.",
      image: "/bride-image/bride-point-right.png",
      date: "Spring 2024"
    }
  ];
</script>

<section class="story-section">
  <!-- Top floral decoration -->
  <div class="floral-accent floral-top">
    <svg viewBox="0 0 100 100" width="80" height="80">
      <g opacity="0.7">
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

  <div class="container">
    <div class="section-header">
      <h2>Our Story</h2>
      <p>A journey of love, laughter, and cherished moments</p>
    </div>

    <div class="stories-grid">
      {#each stories as story (story.id)}
        <div class="story-card">
          <div class="story-image-wrapper">
            <img 
              src={story.image} 
              alt={story.title}
              loading="lazy"
            />
            <div class="story-date">{story.date}</div>
          </div>
          <div class="story-content">
            <h3>{story.title}</h3>
            <p>{story.description}</p>
          </div>
        </div>
      {/each}
    </div>
  </div>

  <!-- Bottom floral decoration -->
  <div class="floral-accent floral-bottom">
    <svg viewBox="0 0 100 100" width="70" height="70">
      <g opacity="0.6">
        <path d="M50 20 Q70 30 75 50 Q70 70 50 80 Q30 70 25 50 Q30 30 50 20" fill="#ddd6fe" opacity="0.5"/>
        <circle cx="50" cy="50" r="12" fill="#ec4899"/>
        <circle cx="50" cy="30" r="8" fill="#fbbf24"/>
        <circle cx="70" cy="50" r="8" fill="#fbbf24"/>
        <circle cx="50" cy="70" r="8" fill="#fbbf24"/>
        <circle cx="30" cy="50" r="8" fill="#fbbf24"/>
      </g>
    </svg>
  </div>
</section>

<style>
  .story-section {
    position: relative;
    width: 100%;
    padding: 120px 20px;
    background: linear-gradient(180deg, #ffffff 0%, #f8f7ff 100%);
    border-top: 1px solid #f0f0f0;
  }

  .floral-accent {
    position: absolute;
    opacity: 0.4;
  }

  .floral-top {
    top: 40px;
    right: 60px;
    animation: float 5s ease-in-out infinite;
  }

  .floral-bottom {
    bottom: 40px;
    left: 60px;
    animation: float 6s ease-in-out infinite 0.5s;
  }

  .container {
    position: relative;
    z-index: 10;
    max-width: 1200px;
    margin: 0 auto;
  }

  .section-header {
    text-align: center;
    margin-bottom: 80px;
  }

  .section-header h2 {
    font-size: 48px;
    font-weight: 300;
    color: #1f2937;
    margin: 0 0 16px 0;
    letter-spacing: -0.5px;
  }

  .section-header p {
    font-size: 16px;
    color: #6b7280;
    margin: 0;
  }

  .stories-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 40px;
  }

  .story-card {
    background: #ffffff;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
    transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    border: 1px solid #f0f0f0;
  }

  .story-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 16px 32px rgba(0, 0, 0, 0.1);
    border-color: #e5e7eb;
  }

  .story-image-wrapper {
    position: relative;
    width: 100%;
    height: 280px;
    overflow: hidden;
    background: linear-gradient(135deg, #f8f7ff 0%, #fff5f7 100%);
  }

  .story-image-wrapper img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.6s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  }

  .story-card:hover .story-image-wrapper img {
    transform: scale(1.05);
  }

  .story-date {
    position: absolute;
    bottom: 16px;
    left: 16px;
    background: rgba(31, 41, 55, 0.9);
    color: #ffffff;
    padding: 8px 16px;
    border-radius: 4px;
    font-size: 12px;
    font-weight: 500;
    letter-spacing: 0.5px;
  }

  .story-content {
    padding: 32px 24px;
  }

  .story-content h3 {
    font-size: 20px;
    font-weight: 500;
    color: #1f2937;
    margin: 0 0 12px 0;
  }

  .story-content p {
    font-size: 14px;
    color: #6b7280;
    line-height: 1.6;
    margin: 0;
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
    .story-section {
      padding: 60px 20px;
    }

    .section-header h2 {
      font-size: 36px;
    }

    .section-header {
      margin-bottom: 50px;
    }

    .stories-grid {
      gap: 24px;
    }

    .floral-top {
      width: 60px;
      height: 60px;
    }

    .floral-bottom {
      width: 50px;
      height: 50px;
    }
  }
</style>
