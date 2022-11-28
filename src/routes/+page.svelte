<script>
  let scrollY;
</script>

<svelte:window bind:scrollY={scrollY} />

<!-- Change navbar colour on scroll -->
{#if scrollY > 150}
  <style>
    .navbar {
      background-image: linear-gradient(black, hsla(0, 0%, 0%, 60%));
    }
  </style>
{/if}



<div class="content">
  <nav class="navbar">
    <img src="svg/logo.svg" alt="" class="navbar__logo">
    <ul class="navbar__items">
      <li class="navbar__item">About</li>
      <li class="navbar__item">Discover</li>
      <li class="navbar__item">Get Started</li>
    </ul>
    <img src="svg/icon-hamburger.svg" alt="" class="navbar__menu">
    <img src="svg/icon-close-menu.svg" alt="" class="navbar__close">
  </nav>
  <main class="main">
    <article class="summary">
      <img src="svg/logo-mastercraft.svg" alt="logo-mastercraft" class="summary__logo">
      <h1 class="summary__title">Mastercraft Bamboo Monitor Riser</h1>
      <p class="summary__desc">A beautiful & handcrafted monitor stand to reduce neck and eye strain.</p>
      <div class="summary__actions">
        <button class="button">Back this project</button>
        <button class="button button--dark button--small">
          <span class="button__label">Bookmark</span>
          <img class="button__icon" src="svg/icon-bookmark.svg" alt="icon-bookmark">
        </button>
      </div>
    </article>
    
    <section class="stats">
      <div class="stats__metrics">
        <div class="stats__section">
          <span class="stats__metric">$89,914</span>
          <span class="stats__label">of $100,000 backed</span>
        </div>
        <div class="stats__sep"></div>
        <div class="stats__section">
          <span class="stats__metric">5007</span>
          <span class="stats__label">total backers</span>
        </div>
        <div class="stats__sep"></div>
        <div class="stats__section">
          <span class="stats__metric">56</span>
          <span class="stats__label">days left</span>
        </div>
      </div>
      <progress class="stats__progress" value=0.8></progress>
    </section>

    <section class="info">
      <h2 class="info__title">About this project</h2>
      <p class="info__desc">
        The Mastercraft Bamboo Monitor Riser is a sturdy and stylish platform that elevates your screen 
        to a more comfortable viewing height. Placing your monitor at eye level has the potential to improve 
        your posture and make you more comfortable while at work, helping you stay focused on the task at hand.
      </p>
      <p class="info__desc">
        Featuring artisan craftsmanship, the simplicity of design creates extra desk space below your computer 
        to allow notepads, pens, and USB sticks to be stored under the stand.
      </p>
      <div class="card">
        <header class="card__header">
          <h3 class="card__title">Bamboo Stand</h3>
          <h4 class="card__subtitle">Pledge $25 or more</h4>
        </header>
        <p class="card__desc">
          You get an ergonomic stand made of natural bamboo. You've helped us launch our promotional campaign, and 
          you’ll be added to a special Backer member list.
        </p>
        <footer class="card__footer">
          <div class="card__stat">
            <span class="card__rem">101</span>
            <span class="card__label">left</span>
          </div>
          <button class="button">Select Reward</button>
        </footer>
      </div>
      <div class="card">
        <header class="card__header">
          <h3 class="card__title">Black Edition Stand</h3>
          <h4 class="card__subtitle">Pledge $75 or more</h4>
        </header>
        <p class="card__desc">
          You get a Black Special Edition computer stand and a personal thank you. You’ll be added to our Backer 
          member list. Shipping is included.
        </p>
        <footer class="card__footer">
          <div class="card__stat">
            <span class="card__rem">64</span>
            <span class="card__label">left</span>
          </div>
          <button class="button">Select Reward</button>
        </footer>
      </div>
      <div class="card">
        <header class="card__header">
          <h3 class="card__title">Mahogany Special Edition</h3>
          <h4 class="card__subtitle">Pledge $200 or more</h4>
        </header>
        <p class="card__desc">
          You get two Special Edition Mahogany stands, a Backer T-Shirt, and a personal thank you. You’ll be added 
          to our Backer member list. Shipping is included.
        </p>
        <footer class="card__footer">
          <div class="card__stat">
            <span class="card__rem">0</span>
            <span class="card__label">left</span>
          </div>
          <button class="button">Out of Stock</button>
        </footer>
      </div>
    </section>

    <div class="menu">
      <ul class="menu__items">
        <li class="menu__item"></li>
        <li class="menu__item"></li>
        <li class="menu__item"></li>
      </ul>
    </div>
  </main>

  <dialog class="modal">
    <div class="modal__header">
      <h2 class="modal__title"></h2>
      <img src="svg/icon-close-menu.svg" alt="" class="modal__close">
    </div>
    <p class="modal__desc"></p>
    <div class="card">
      <header class="card__header">
        <input type="radio" name="" id="" class="card__radio">
        <h3 class="card__title"></h3>
      </header>
      <p class="card__desc"></p>
    </div>
    <div class="card">
      <header class="card__header">
        <input type="radio" name="" id="" class="card__radio">
        <h3 class="card__title"></h3>
      </header>
      <p class="card__desc"></p>
      <div class="card__stat">
        <span class="card__rem"></span>
        <span class="card__label"></span>
      </div>
      <div class="card__sep"></div>
      <footer class="card__footer">
        <h5 class="card__amounts"></h5>
        <input type="number" name="" id="" class="card__amount">
        <button class="button"></button>
      </footer>
    </div>
  </dialog>

  <dialog class="modal">
    <div class="icon-confirm"></div>
    <h2 class="modal__title"></h2>
    <p class="modal__desc"></p>
    <button class="button"></button>
  </dialog>
</div>







<!-- Selection modal start -->

Back this project
Want to support us in bringing Mastercraft Bamboo Monitor Riser out in the world?

Pledge with no reward
Choose to support us without a reward if you simply believe in our project. As a backer, 
you will be signed up to receive product updates via email.

Bamboo Stand
Pledge $25 or more
You get an ergonomic stand made of natural bamboo. You've helped us launch our promotional campaign, and
you’ll be added to a special Backer member list.
101 left

<!-- Selected pledge start -->
Enter your pledge
$25
Continue
<!-- Selected pledge end -->

Black Edition Stand
Pledge $75 or more
You get a Black Special Edition computer stand and a personal thank you. You’ll be added to our Backer
member list. Shipping is included.
64 left

<!-- Selected pledge start -->
Enter your pledge
$75
Continue
<!-- Selected pledge end -->

Mahogany Special Edition
Pledge $200 or more
You get two Special Edition Mahogany stands, a Backer T-Shirt, and a personal thank you. You’ll be added
to our Backer member list. Shipping is included.
0 left

<!-- Selected pledge  start -->
Enter your pledge
$200
Continue
<!-- Selected pledge end -->

<!-- Selection modal end -->

<!-- Success modal start -->

Thanks for your support!
Your pledge brings us one step closer to sharing Mastercraft Bamboo Monitor Riser worldwide. You will get
an email once our campaign is completed.
Got it!

<!-- Success modal end -->
