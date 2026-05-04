<div>upload some books =D</div>
<script lang="ts">
  import { username } from "./library";
  let books = [
    {
      title: "The Great Gatsby",
      trader: "John Doe",
      author: "F. Scott Fitzgerald",
      summary:
        "The Great Gatsby is a novel by F. Scott Fitzgerald that explores themes of wealth, love, and the American Dream in the 1920s.",
      cover: "https://images-na.ssl-images-amazon.com/images/I/81af+MCATTL.jpg",
      details: false,
      bids: [
        { bidder: "Alice", amount: 20 },
        { bidder: "Bob", amount: 25 },
      ],
    },
  ];

  let userBid: string = "";
</script>

<div>
  {#each books as book}
    <div class="book">
      <img src={book.cover} alt={book.title} class="cover" />
      <h2>{book.title}</h2>
      <p class="author"><strong>Author:</strong> {book.author}</p>
      <p class="trader"><strong>Trader:</strong> {book.trader}</p>
      <p class="summary">{book.summary}</p>
      <h2>
        <button
          onclick={() => {
            book.details = !book.details;
            books = books;
          }}
        >
          details
        </button>
      </h2>
      {#if book.details === true}
        <div class="bids">
          <h3>Bids:</h3>
          <ul>
            {#each book.bids as bid}
              <li>
                <p class="bid">
                  <strong>{bid.bidder}:</strong> ${bid.amount}
                </p>
              </li>
            {/each}
          </ul>

          <input
            type="number"
            placeholder="Enter your bid"
            bind:value={userBid}
            onchange={() => {
              const value = parseFloat(userBid);

              if (!isNaN(value)) {
                book.bids.push({ bidder: $username, amount: value });
                books = books; // trigger update
                userBid = ""; // clear input
              }
            }}
          />
        </div>
      {:else}{/if}
    </div>
  {/each}
</div>

<style>
  .summary {
    position: relative;
    top: 10px;
  }
  button {
    color: white;
    font-family:
      system-ui,
      -apple-system,
      BlinkMacSystemFont,
      "Segoe UI",
      Roboto,
      Oxygen,
      Ubuntu,
      Cantarell,
      "Open Sans",
      "Helvetica Neue",
      sans-serif;
    background-color: transparent;
    border: 2px solid white;
    border-radius: 4px;
    cursor: pointer;
    outline: none;
    font-size: 16px;
    width: 80px;
  }

  .book {
    display: flex;
    flex-direction: column;
    gap: 10px;
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
    height: 250px;
    object-fit: cover;
    border-radius: 6px;
  }

  .bids {
    display: flex;
    gap: 20px;
  }

  ul {
    list-style-type: none;
    padding: 0;
    position: relative;
    right: 60px;
    top: 20px;
  }

  input {
    height: 20px;
    color: white;
    position: relative;
    left: 60px;
    top: 85px;
    outline: none;
    border: none;
    border-radius: 4px;
    background-color: #203d5b;
    background-color: transparent;
    font-family:
      system-ui,
      -apple-system,
      BlinkMacSystemFont,
      "Segoe UI",
      Roboto,
      Oxygen,
      Ubuntu,
      Cantarell,
      "Open Sans",
      "Helvetica Neue",
      sans-serif;
    border-bottom: white solid 2px;
    position: relative;
    right: 60px;
  }

  input::placeholder {
    color: white;
  }
</style>
