<script>
  let navbarHeight;
  let navbarMenu;
  let navbarClose;
  let scrollY;
  let modalThanks;
  let modalMenu;
  let menuPledge;
  let pledgeAmount;
  let pledgeInput;
  let pledge;
  let pledge0;
  let pledge1;
  let total = 89914;
  let bookmarked = false;
  let pledges = [
    {
      'id': 0,
      'title': "Pledge with no reward",
      'description': "Choose to support us without a reward if you simply believe in our project. As a backer, you will be signed up to receive product updates via email.",
      'amount': 0,
    },
    {
      'id': 1,
      'title': 'Bamboo Stand',
      'minAmount': 25,
      'description': "You get an ergonomic stand made of natural bamboo. You've helped us launch our promotional campaign, and you'll be added to a special Backer member list.",
      'remaining': 101,
      'amount': 25,
    },
    {
      'id': 2,
      'title': 'Black Edition Stand',
      'minAmount': 75,
      'description': "You get a Black Special Edition computer stand and a personal thank you. You’ll be added to our Backer member list. Shipping is included.",
      'remaining': 64,
      'amount': 75,
    },
    {
      'id': 3,
      'title': 'Mahogany Special Edition',
      'minAmount': 200,
      'description': "You get two Special Edition Mahogany stands, a Backer T-Shirt, and a personal thank you. You’ll be added to our Backer member list. Shipping is included.",
      'remaining': 0,
      'amount': 200,
    },
  ]

  function showMenuPledge() {
    menuPledge.showModal();
  }

  const selectPledge = (id) => () => {
    if (pledges.filter((x) => x.id === id)[0].remaining === 0) {
      return;
    }
    pledgeInput = id;
    menuPledge.showModal();
  }

  function hideMenuPledge() {
    menuPledge.close();
  }

	const submit = pledgeId => () => {
    total += pledges[pledgeId].amount;
    pledges[pledgeId].amount = pledges[pledgeId].minAmount ?? 0;
    if (pledges[pledgeId].hasOwnProperty("remaining")) {
      pledges[pledgeId].remaining -= 1;
    }
    hideMenuPledge();
    modalThanks.showModal();
	};

  function toggleModalMenu() {
    modalMenu.classList.toggle("menu--hidden");
    navbarMenu.classList.toggle("hidden");
    navbarClose.classList.toggle("hidden");
  }

  $: console.log(pledge);
</script>

<svelte:window bind:scrollY={scrollY} />

<!-- Change navbar colour on scroll -->
{#if scrollY > navbarHeight}
  <style>
    .navbar {
      background-image: linear-gradient(black, hsla(0, 0%, 0%, 60%));
    }
  </style>
{/if}

<div class="content">
  <div class="menu menu--hidden" bind:this={modalMenu}>
    <ul class="menu__items">
      <li class="menu__item"><a class="menu__link" href="./">About</a></li>
      <li class="menu__item"><a class="menu__link" href="./">Discover</a></li>
      <li class="menu__item"><a class="menu__link" href="./">Get Started</a></li>
    </ul>
  </div>

  <nav class="navbar" bind:offsetHeight={navbarHeight}>
    <a class="navbar__logo" href=""><img src="svg/logo.svg" alt=""></a>
    <ul class="navbar__items">
      <li class="navbar__item">About</li>
      <li class="navbar__item">Discover</li>
      <li class="navbar__item">Get Started</li>
    </ul>
    <button class="navbar__menu" bind:this={navbarMenu} on:click={toggleModalMenu}><img src="svg/icon-hamburger.svg" alt=""></button>
    <button class="navbar__menu hidden" bind:this={navbarClose} on:click={toggleModalMenu}><img src="svg/icon-close-menu.svg" alt=""></button>
  </nav>

  <main class="main">
    <article class="summary">
      <img src="svg/logo-mastercraft.svg" alt="logo-mastercraft" class="summary__logo">
      <h1 class="summary__title">Mastercraft Bamboo Monitor Riser</h1>
      <p class="summary__desc">A beautiful & handcrafted monitor stand to reduce neck and eye strain.</p>
      <div class="summary__actions">
        <button class="button" on:click={showMenuPledge}>Back this project</button>
        <button class="button button--dark button--small" class:button--enabled={bookmarked} on:click={() => bookmarked = !bookmarked}>
          <span class="button__label">Bookmark</span>
          <svg width="56" height="56" xmlns="http://www.w3.org/2000/svg"><g fill-rule="evenodd"><circle fill="var(--bkmk-circle)" cx="28" cy="28" r="28"/><path fill="var(--bkmk-tag)" d="M23 19v18l5-5.058L33 37V19z"/></g></svg>
        </button>
      </div>
    </article>
    
    <section class="stats">
      <div class="stats__metrics">
        <div class="stats__section">
          <span class="stats__metric">${total}</span>
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
      <progress class="stats__progress" value={total} max=100000></progress>
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

      {#each pledges as p}
        {#if p.minAmount ?? 0 > 0}
          <div class="card" class:card--disabled={p.remaining === 0}>
            <header class="card__titles">
              <h3 class="card__title">{p.title}</h3>
              <h4 class="card__subtitle">Pledge ${p.minAmount} or more</h4>
            </header>
            <p class="card__desc">{p.description}</p>
            <footer class="card__footer">
              <div class="card__stat">
                <span class="card__rem">{p.remaining}</span>
                <span class="card__label">left</span>
              </div>
              <button class="button" on:click={selectPledge(p.id)} class:button--disabled={p.remaining === 0} >{p.remaining > 0 ? "Select Reward" : "Out of Stock"}</button>
            </footer>
          </div>
        {/if}
      {/each}
    </section>
  </main>

  <dialog bind:this={menuPledge} class="modal">
    <div class="modal__content">
      <div class="modal__header">
        <h2 class="modal__title">Back this project</h2>
        <button class="modal__close" on:click={hideMenuPledge}>
          <img src="svg/icon-close-menu.svg" alt="">
        </button>
      </div>
      <p class="modal__desc">
        Want to support us in bringing Mastercraft Bamboo Monitor Riser out in the world?
      </p>
  
      {#each pledges as p}
        <label for="pledge{p.id}">
          <div class="card" class:card--disabled={p.remaining === 0} class:card--selected={pledgeInput == p.id}>
            <header class="card__header">
              <input type="radio" name="pledge" id="pledge{p.id}" class="card__radio" value={p.id} bind:group={pledgeInput} disabled={p.remaining === 0}>
              <div class="card__titles">
                <h3 class="card__title">{p.title}</h3>
                {#if p.minAmount}
                  <h4 class="card__subtitle">Pledge ${p.minAmount} or more</h4>
                {/if}
              </div>
            </header>
            <p class="card__desc">{p.description}</p>
            {#if p.remaining !== undefined}
              <div class="card__stat">
                <span class="card__rem card__rem--small">{p.remaining}</span>
                <span class="card__label">left</span>
              </div>
            {/if}
            {#if pledgeInput == p.id}
              <div class="card__sep"></div>
              <footer class="card__footer card__footer--small flex-centred">
                <h5 class="card__amounts">Enter your pledge</h5>
                <div class="card__pledge">
                  <div class="card__input">
                    <div class="card__amount-unit">$</div>
                    <input type="number" class="card__amount" min=0 step=1 bind:value={p.amount}>
                  </div>
                  <button class="button button--slim" on:click={submit(p.id)}>Continue</button>
                </div>
              </footer>
            {/if}
          </div>
        </label>
      {/each}
    </div>
  </dialog>

  <dialog class="modal" bind:this={modalThanks}>
    <div class="modal__content modal__content--centred">
      <img src="svg/icon-check.svg" alt="icon-check">
      <h2 class="modal__title">Thanks for your support!</h2>
      <p class="modal__desc">Your pledge brings us one step closer to sharing Mastercraft Bamboo Monitor Riser worldwide. You will get an email once our campaign is completed.</p>
      <button class="button" on:click={() => modalThanks.close()}>Got it!</button>
    </div>
  </dialog>
</div>
