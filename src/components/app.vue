<script setup>



const articles = [
  {
    title: "Surreal Portrait: Exploring Isolation By Ben Zank",
    meta: "Photography / Concept",
    image: "head/photo-1500648767791-00dcc994a43e.avif",
  },
  {
    title: "The Art Of Waiting By Ignant Production",
    meta: "Art / Conceptual",
    image: "head/photo-1506794778202-cad84cf45f1d.avif",
  },
  {
    title: "Time Is Defined As The Indefinite Continued Progress",
    meta: "Photography / Concept",
    image: "head/photo-1507003211169-0a1dd7228f2d.avif",
  },
]

const topStories = [
  { number: "1.", title: "The Understated Charm of Jack", category: "Johnstones / Photography" },
  { number: "2.", title: "Photographer Drew Vickers Shoots", category: "The Spectrum Of Emotion" },
  { number: "3.", title: "The Understated Charm of Jack", category: "Johnstones / Photography" },
]

const menu = ["Home", "About us", "Art", "Blog", "Articles", "News", "Pinterest", "Gallery", "Contact"]
</script>

<template>
  <main class="page-shell">
    <section class="magazine">
      <aside class="sidebar">
        <a class="brand" href="#">TETRAD</a>

        <nav class="main-nav" aria-label="Główna nawigacja">
          <a v-for="item in menu" :key="item" href="#">{{ item }}</a>
        </nav>

        <div class="social-block">
          <span>Follow us on social media</span>
          <div class="social-links">
            <a href="#" aria-label="Facebook">f</a>
            <a href="#" aria-label="Twitter">♥</a>
            <a href="#" aria-label="Pinterest">p</a>
          </div>
        </div>
      </aside>

      <div class="content">
        <header class="top-stories">
          <article v-for="story in topStories" :key="story.number" class="top-story">
            <strong>{{ story.number }}</strong>
            <div>
              <h2>{{ story.title }}</h2>
              <p>{{ story.category }}</p>
              <small>08.03.2026</small>
            </div>
          </article>
        </header>

        <section class="latest">
          <div class="section-heading">
            <h1>LATEST ARTICLES</h1>
            <span>12 956 article</span>
          </div>

          <div class="cards">
            <article v-for="article in articles" :key="article.title" class="article-card">
              <div class="card-copy">
                <h3>{{ article.title }}</h3>
                <p>{{ article.meta }}</p>
              </div>
              <img :src="article.image" :alt="article.title" />
            </article>
          </div>
        </section>

        <footer class="feature-footer">
          <div class="footer-title">
            <h3>The Understated Charm of Jack</h3>
            <span>Johnstones / Photography</span>
          </div>

          <p class="footer-text">
            American photographer Ben Zank, who we featured previously, shares
            a new series of surreal portraits following his move from New York
            City to New Zealand. His images represent an ongoing experience of
            isolation and discovery.
          </p>

          <div class="recommend">
            <em>Recommended For You</em>
            <div class="share-box">
              <span>231</span>
              <button>f</button>
              <button>♥</button>
              <button>p</button>
            </div>
          </div>
        </footer>
      </div>

      <aside class="right-panel">
        <article class="featured">
          <img
            src="head/photo-1487958449943-2429e8be8625.avif"
            alt="Modernistyczny budynek"
          />
          <div class="featured-copy">
            <h2>Techeles Reopens Its Doors For A Visually Stimulating Cinematic Experience</h2>
            <span>08.03.2026</span>
            <p>
              An impressive treatment to Berlin's past, present era, the former
              iconic Kunsthaus Tacheles in the Berlin district of Mitte.
            </p>
          </div>
        </article>

        <form class="subscribe" @submit.prevent>
          <h3>Subscribe Now</h3>

          <label>
            <span>Name</span>
            <input type="text" />
          </label>

          <div class="split-fields">
            <label>
              <span>Email</span>
              <input type="email" />
            </label>
            <label>
              <span>Mobile</span>
              <input type="tel" />
            </label>
          </div>

          <label>
            <span>Info</span>
            <input type="text" />
          </label>

          <label>
            <span>Subject</span>
            <input type="text" />
          </label>

          <button type="submit">SEND</button>
        </form>

        <div class="copyright">ALL RIGHTS RESERVED</div>
      </aside>
    </section>
  </main>
</template>
