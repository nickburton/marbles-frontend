<script>
  let marbleCards = [
    {
      id: 1,
      name: "Marble 1",
      image: "https://example.com/marble1.png",
      material: "Glass",
      rarity: "Common",
    },
    {
      id: 2,
      name: "Marble 2",
      image: "https://example.com/marble2.png",
      material: "Marble",
      rarity: "Rare",
    },
    {
      id: 3,
      name: "Marble 3",
      image: "https://example.com/marble3.png",
      material: "Granite",
      rarity: "Common",
    },
  ];

  let selectedMarbles = [];

  function handleCardClick(marble) {
    if (selectedMarbles.includes(marble)) {
      selectedMarbles = selectedMarbles.filter((m) => m.id !== marble.id);
    } else {
      selectedMarbles = [...selectedMarbles, marble];
    }
  }

  function handleTrade() {
    // code for handling the trade logic goes here
    console.log(selectedMarbles);
  }
</script>

<h1>Marble Trading</h1>

<p>Select up to 3 marbles to trade:</p>

<div class="marble-grid">
  {#each marbleCards as marble}
    <div
      class="marble-card {selectedMarbles.includes(marble) ? 'selected' : ''}"
      on:click={() => handleCardClick(marble)}
    >
      <img src={marble.image} alt={marble.name} />
      <h2>{marble.name}</h2>
      <p>Material: {marble.material}</p>
      <p>Rarity: {marble.rarity}</p>
    </div>
  {/each}
</div>

<button on:click={handleTrade} disabled={selectedMarbles.length !== 3}
  >Trade</button
>

<style>
  .marble-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
  }

  .marble-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 20px;
    border: 1px solid black;
    border-radius: 10px;
    cursor: pointer;
  }

  .marble-card img {
    width: 100%;
    max-height: 200px;
    object-fit: contain;
    margin-bottom: 10px;
  }

  .marble-card.selected {
    background-color: lightblue;
  }

  button {
    margin-top: 20px;
    padding: 10px;
    border-radius: 10px;
    cursor: pointer;
  }

  button[disabled] {
    opacity: 0.5;
    cursor: not-allowed;
  }
</style>
