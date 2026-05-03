<script lang="ts">
  const books = [
    {
      title: "Bio 101",
      author: "John Doe",
      details: false,
      cover:
        "https://i.pinimg.com/736x/1e/08/a2/1e08a2bd6acf19fd9530717d84a4a86c.jpg",
      summary: "An introduction to biology for beginners.",
      bids: [
        { bidder: "Alice", amount: 10 },
        { bidder: "Bob", amount: 15 },
      ],
    },
  ];
</script>

<div>
  {#each books as book}
    <div class="book">
      <img src={book.cover} alt={book.title} class="cover" />
      <h2>{book.title}</h2>
      <p class="author"><strong>Author:</strong> {book.author}</p>
      <p>{book.summary}</p>
      <button
        on:click={() =>
          book.details == !book.details
            ? (book.details = book.details = true)
            : (book.details = false)}><h2>details</h2></button
      >
      {#if book.details === true}
        <div class="bids">
          <h3>Bids:</h3>
          {#each book.bids as bid}
            <p>
              <strong>{bid.bidder}:</strong> ${bid.amount}
            </p>
          {/each}
        </div>
      {:else}{/if}
    </div>
  {/each}
</div>

<style>
  button {
    background: transparent;
    border: none;
    outline: none;
    position: relative;
    left: 20px;
    bottom: 60px;
    transition: border-bottom 0.3s ease;
  }

  button:hover {
    border-bottom: 2px solid white;
  }

  div {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
  }
  .book {
    border: 1px solid #ccc;
    padding: 16px;
    margin: 16px;
    border-radius: 8px;
    max-width: 400px;
  }
  .book .author {
    font-style: italic;
    position: relative;
    top: 10px;
    left: 10px;
  }
  .cover {
    width: 100%;
    height: auto;
    border-radius: 4px;
  }
</style>
