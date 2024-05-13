<script>
  import { onMount } from 'svelte';

  let imageLoaded = false;

  export let websiteImage;
  export let websiteName;
  export let websiteUrl;
  export let websiteCode;
  export let codeLinkBoolean;
  export let websiteGif;
  export let websiteIframe; // New variable for iframe URL
  export let closeModal;
  export let nextModal;
  export let prevModal;  

  function handleOverlayClick(event) {
    const isOverlayClick = event.target === event.currentTarget;
    if (isOverlayClick) {
      closeModal();
    }
  }

  function handleKeyDown(event) {
    switch (event.key) {
      case 'Escape':
        closeModal();
        break;
      case 'ArrowRight':
        nextModal();
        break;
      case 'ArrowLeft':
        prevModal();
        break;
      default:
        break;
    }
  }

  const handleImageLoad = () => {
    imageLoaded = true;
  };

  onMount(() => {
    const image = new Image();
    image.src = websiteGif ? websiteGif : websiteImage;
    image.onload = handleImageLoad;

    document.addEventListener('keydown', handleKeyDown);
    return () => {
      document.removeEventListener('keydown', handleKeyDown);
    };
  });
</script>

<style>
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(0, 0, 0, 0.8);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal {
    background: #000;
    width: 90vw;
    height: 90vh;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    color: white;
  }

  .iframe-big {
    width: 100%;
    height: 100%;
    border: none;
  }

  .img-big {
    max-width: 100%;
    max-height: 100%;
  }

  .card-info {
    margin: 20px;
  }

  .modal-nav {
    display: flex;
    justify-content: space-between;
    width: 100%;
  }

  .modal-nav-button {
    cursor: pointer;
  }

  .outbound {
    display: flex;
    align-items: center;
    text-decoration: none;
    color: #000000;
    color: white;
  }

  .code-link {
    margin-right: 10px;
  }

  .site-link {
    margin-left: 10px;
  }
</style>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div class="modal-overlay" on:click|stopPropagation={handleOverlayClick}>
  <div class="modal" aria-modal="true">
    <div class="card-info">
      <h2><a href={websiteUrl} target="_blank">{websiteName}</a></h2>
      <div class="modal-nav">
        <svg on:click={prevModal} class="modal-nav-button" width="30" height="29" viewBox="0 0 30 29" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M12.7413 19.422L7.70703 14.3879L12.7413 9.35359" stroke="white"/>
          <path d="M7.89587 14.3878L22.442 14.3878" stroke="white"/>
        </svg>

        <svg on:click={nextModal} class="modal-nav-button" width="30" height="29" viewBox="0 0 30 29" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M16.7011 9.35359L21.7354 14.3878L16.7011 19.422" stroke="white"/>
          <path d="M21.5465 14.3878H7.00037" stroke="white"/>
        </svg>

        <button class="modal-nav-button" on:click={closeModal}>esc</button>
      </div>
    </div>

    <!-- Render iframe if present, otherwise render image -->
    {#if websiteIframe}
      <iframe src={websiteIframe} class="iframe-big" frameborder="0" allowfullscreen title="{websiteName}"></iframe>
    {:else if !imageLoaded}
      <img src={websiteImage} alt={websiteName} class="img-big" />
    {:else}
      <img src={websiteGif ? websiteGif : websiteImage} alt={websiteName} class="img-big" />
    {/if}

    <div class="card-info">
      {#if websiteCode && websiteCode !== null}
        <a href={websiteCode} target="_blank" class="outbound code-link">
          <span>Check Code</span>
          <svg width="30" height="29" viewBox="0 0 30 29" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect width="30" height="29" rx="3" fill="transparent"/>
            <path d="M19 7L26 14L19 21" stroke="white"/>
            <path d="M12 21L5 14L12 7" stroke="white"/>
          </svg>                   
        </a>
      {:else if !codeLinkBoolean} 
        <a href="https://forms.gle/7gi8eLZZoQmbVyst5" target="_blank" class="outbound code-link empty-code">
          <span>Add CodePen Link</span>
          <svg width="30" height="29" viewBox="0 0 30 29" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect width="30" height="29" rx="3" fill="transparent"/>
            <path d="M19 7L26 14L19 21" stroke="white"/>
            <path d="M12 21L5 14L12 7" stroke="white"/>
          </svg>                   
        </a>
      {/if}

      <a href={websiteUrl} target="_blank" class="outbound site-link">
        <span>Visit Site</span>
        <svg width="30" height="29" viewBox="0 0 30 29" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect width="30" height="29" rx="3" fill="transparent"/>
          <path d="M10.454 7.36396H23.182V20.0919" stroke="white"/>
          <path d="M23 7.54596L9 21.546" stroke="white"/>
        </svg>
      </a>
    </div>
  </div>
</div>
