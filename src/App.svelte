<script>
  import Member from './lib/Member.svelte'
  import { fade } from 'svelte/transition'

  import photo1 from './assets/photo1.png'
  import photo2 from './assets/photo2.png'
  import photo3 from './assets/photo3.png'
  import photo4 from './assets/photo4.png'
  import photo5 from './assets/photo5.png'
  import photo6 from './assets/photo6.png'

  const members = [
    { name: 'Bill Mahoney', role: 'Product owner', src: photo1, },
    { name: 'Saba Cabrera', role: 'Art director', src: photo2, },
    { name: 'Shae Le', role: 'Tech Lead', src: photo3, },
    { name: 'Skylah Lu', role: 'UX Designer', src: photo4, },
    { name: 'Griff Richards', role: 'Developer', src: photo5, },
    { name: 'Stan John', role: 'Developer', src: photo6, },
  ]
</script>

<main>
  <header>
    <h1 in:fade={{delay: 500}}>The creative crew</h1>

    <div in:fade={{delay: 500}}>
      <h2>WHO WE ARE</h2>
      <p>
        We are team of creatively diverse.  driven.  innovative individuals working in various locations from the world.
      </p>
    </div>
  </header>

  <section>
    {#each members as member, i}
      <div in:fade={{ delay: i * 200 + 500 }}>
        <Member delay={i * 200 + 600} src={member.src} alt={`${member.name} as ${member.role}`}>
          <svelte:fragment slot="name">{member.name}</svelte:fragment>
          <svelte:fragment slot="role">{member.role}</svelte:fragment>
        </Member>
      </div>
    {/each}
  </section>
</main>

<style>
  @import url('https://fonts.googleapis.com/css2?family=PT+Serif:wght@400;700&family=Poppins:wght@400;600&display=swap');

  :global(*) {
    margin: 0;
    padding: 0;
  }
  
  :global(h1) {
    font-family: 'PT Serif', serif;
  }

  main {
    font-family: 'Poppins', sans-serif;
    padding: 110px 243px;
    padding-right: 275px;
  }


  header {
    display: grid;
    grid-template-columns: 1fr 1fr;

    font-size: 18px;
    line-height: 27px;
    color: black;
  }

  header h1 {
    letter-spacing: -0.045em;
  }

  header h2 {
    font-family: 'Poppins', sans-serif;
    font-size: 18px;
    font-weight: 600;
  }

  header p {
    width: clamp(0ch, 85%, 42ch);
    margin-top: 10px;
  }

  section {
    display: grid;
    grid-template-columns: repeat(3, 264px);
    gap: 132px 60px;

    margin-top: 96px;
  }

  section > :global(div):nth-child(3n + 2) {
    transform: translateY(30%);
  }

  @media (min-width: 1756px) {
    section {
      grid-template-columns: repeat(auto-fit, minmax(156px, 264px));
    }

    section > :global(div):nth-child(3n + 2) {
      transform: translateY(0%);
    }
  }

  @media (max-width: 1303px) {
    main {
      padding: 71px 19px;
    }

    header {
      place-items: center;
    }

    section {
      grid-template-columns: repeat(2, minmax(156px, 264px));
      justify-content: center;
      gap: 64px 25px;
    }

    section > :global(div):nth-child(3n + 2) {
      transform: translateY(0%);
    }

    section > :global(div):nth-child(2n) {
      transform: translateY(30%);
    }
  }

  @media (max-width: 750px) {
    header {
      grid-template-columns: 1fr;
      grid-template-rows: min-content 1fr;

      place-items: start;
      gap: 38px 0;
    }

    header p {
      font-size: 14px;
      line-height: 21px;
    }
  }
</style>
