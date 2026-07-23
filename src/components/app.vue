<script setup>
import { ref } from "vue";

const message = ref("");

const initiatives = [
  ["Sadzenie drzew", "zieleń i klimat", "12/03/26"],
  ["Sprzątanie plaż", "dla przyszłych pokoleń", "29/05/26"],
  ["Edukacja ekologiczna", "warsztaty", "06/06/26"],
  ["Ochrona miejskich parków", "lokalne działania", "18/08/26"],
];

const problems = [
  {
    title: "Zanieczyszczenie oceanów",
    image: "/assets/hero-landscape.png",
    label: "Woda",
  },
  {
    title: "Topnienie lodowców",
    image: "/assets/glacier.png",
    label: "Klimat",
  },
  {
    title: "Utrata lasów",
    image: "/assets/forest.png",
    label: "Natura",
  },
  {
    title: "Emisje gazów",
    image: "/assets/hero-landscape.png",
    label: "Powietrze",
  },
];

function problemBackground(image) {
  return {
    backgroundImage: `linear-gradient(180deg, transparent 24%, rgba(5, 18, 16, 0.78) 100%), url("${image}")`,
  };
}

function subscribe(event) {
  message.value = "Dziękujemy! Jesteś na liście.";
  event.currentTarget.reset();
}
</script>

<template>
  <main class="site-shell">
    <div class="page">
      <header class="topbar">
        <a
          class="brand brand-mobile"
          href="#start"
          aria-label="Terra Nova — strona główna"
        >
          <span class="brand-mark">✣</span>
          Terra Nova
        </a>

        <nav class="nav nav-left" aria-label="Główna nawigacja">
          <a class="active" href="#start">Start</a>
          <a href="#dzialania">Działania</a>
          <a href="#misja">Nasza misja</a>
        </nav>

        <a class="brand brand-desktop" href="#start">
          <span class="brand-mark">✣</span>
          Terra Nova
        </a>

        <nav class="nav nav-right" aria-label="Dodatkowa nawigacja">
          <a href="#problemy">Problemy</a>
          <a href="#projekty">Projekty</a>
          <a class="contact-link" href="mailto:kontakt@terranova.pl">Kontakt</a>
        </nav>

        <details class="mobile-menu">
          <summary aria-label="Otwórz menu">
            <span></span>
            <span></span>
          </summary>
          <div>
            <a href="#misja">Nasza misja</a>
            <a href="#dzialania">Działania</a>
            <a href="#problemy">Problemy</a>
            <a href="mailto:kontakt@terranova.pl">Kontakt</a>
          </div>
        </details>
      </header>

      <section id="start" class="hero">
        <div class="hero-copy">
          <p class="eyebrow"><span>✣</span> Fundacja Terra Nova</p>
          <h1>
            Ratujmy naturę.<br />
            Zmieniajmy <u>klimat</u><br />
            razem.
          </h1>

          <form class="hero-form" @submit.prevent="subscribe">
            <label class="sr-only" for="hero-email">Adres e-mail</label>
            <input
              id="hero-email"
              type="email"
              required
              placeholder="Twój adres e-mail"
            />
            <button type="submit">Dołącz <span>→</span></button>
          </form>

          <div class="community">
            <div class="avatars" aria-hidden="true">
              <i>AK</i><i>MJ</i><i>OL</i>
            </div>
            <p><strong>1,7 mln+</strong> osób<br />działa razem z nami</p>
          </div>
        </div>

        <div class="hero-visual">
          <span class="hotspot hotspot-one">○ Emisje CO₂</span>
          <span class="hotspot hotspot-two">○ Zanieczyszczenie wód</span>
          <span class="hotspot hotspot-three">○ Utrata bioróżnorodności</span>

          <div class="volunteer-card">
            <span>17</span>
            <p>lat wspólnych<br />działań</p>
          </div>

          <p class="visual-note">
            Chronimy środowisko<br />i odbudowujemy naturę.
          </p>
        </div>
      </section>

      <section id="misja" class="mission">
        <div class="orbit-photo orbit-one"></div>

        <div class="mission-copy">
          <p class="section-kicker">Nasza wspólna przyszłość</p>
          <h2>Zróbmy świat<br />czystszym i bardziej zielonym.</h2>
          <p>
            Łączymy ludzi, naukę i lokalne społeczności, aby odwracać skutki
            zmian klimatu.
          </p>

          <div class="mission-actions">
            <a class="button-light" href="#projekty">
              Zobacz projekty <span>→</span>
            </a>
            <a class="text-link" href="#dzialania">
              <i></i> Dowiedz się więcej
            </a>
          </div>
        </div>

        <div class="orbit-photo orbit-two"></div>
        <div class="orbit-photo orbit-three"></div>
      </section>

      <section class="statement" aria-label="Chronimy naturę">
        <div class="statement-word dark">My</div>
        <div class="statement-word photo glacier-small">Chronimy</div>
        <div class="statement-arrow" aria-hidden="true">→</div>
        <div class="statement-word photo earth-small">Naturę</div>
      </section>

      <section id="dzialania" class="initiatives">
        <div class="section-heading">
          <h2>Nasze inicjatywy</h2>
          <p>
            Poznaj projekty, dzięki którym<br />natura odzyskuje równowagę.
          </p>
        </div>

        <div class="initiative-head">
          <span>Nazwa</span>
          <span>Obszar</span>
          <span>Data</span>
          <span></span>
        </div>

        <div class="initiative-list">
          <a
            v-for="([title, tag, date], index) in initiatives"
            :key="title"
            href="#projekty"
            class="initiative-row"
          >
            <strong>{{ title }}</strong>
            <span :class="['tag', { accent: index === 1 }]">{{ tag }}</span>
            <time>{{ date }}</time>
            <i>→</i>
          </a>
        </div>
      </section>

      <section id="problemy" class="problems">
        <div class="problem-grid">
          <article
            v-for="(problem, index) in problems"
            :key="problem.title"
            :class="['problem-card', `card-${index + 1}`]"
            :style="problemBackground(problem.image)"
          >
            <span class="card-label">{{ problem.label }}</span>

            <a
              class="card-arrow"
              href="#projekty"
              :aria-label="`Poznaj: ${problem.title}`"
            >
              <span aria-hidden="true">↗</span>
            </a>

            <div class="card-copy">
              <h3>{{ problem.title }}</h3>
              <p>
                Małe decyzje budują wielką zmianę. Zobacz, jak możesz pomóc.
              </p>
            </div>

            <a class="card-button" href="#projekty">
              Poznaj problem <span>→</span>
            </a>
          </article>
        </div>
      </section>

      <section id="projekty" class="newsletter">
        <span class="pill">newsletter</span>

        <div>
          <h2>
            Otrzymuj najnowsze informacje<br />o naszych projektach i
            inicjatywach.
          </h2>

          <form @submit.prevent="subscribe">
            <label class="sr-only" for="footer-email">Adres e-mail</label>
            <input
              id="footer-email"
              type="email"
              required
              placeholder="Adres e-mail"
            />
            <button type="submit">Zapisz się <span>→</span></button>
          </form>

          <p class="form-message" aria-live="polite">{{ message }}</p>
        </div>
      </section>

      <footer>
        <p>©2026 Terra Nova. Wszelkie prawa zastrzeżone.</p>

        <a class="brand" href="#start">
          <span class="brand-mark">✣</span>
          Terra Nova
        </a>


        <div class="socials">
          <a href="#">Facebook</a>
          <a href="#">Instagram</a>
          <a href="#">LinkedIn</a>
        </div>
      </footer>
    </div>
  </main>
</template>
