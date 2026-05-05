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
  .book {
    /* Charter is beautiful, Merriweather is a great backup */
    font-family: "Charter", "Bitstream Charter", "Sitka Text", "Cambria", serif;

    /* This CSS property is a 'cheat code' to force numbers to line up 
    if the font supports it (works for many modern serifs) */
    font-variant-numeric: lining-nums;

    background-color: #1a2a3a;
    color: white;
    border: 1px solid #334e68;
    padding: 24px;
    margin: 16px auto;
    border-radius: 12px;
    max-width: 400px;
    display: flex;
    flex-direction: column;
    gap: 15px;
  }

  .cover {
    width: 100%;
    height: auto;
    object-fit: contain;
    border-radius: 8px;
  }

  h2 {
    margin: 0;
    font-size: 1.5rem;
  }

  /* Remove those weird relative offsets */
  .summary,
  .author,
  .trader {
    position: static;
    margin: 0;
    line-height: 1.5;
  }

  .author {
    font-style: italic;
    opacity: 0.9;
  }

  button {
    font-family: system-ui, sans-serif;
    background: rgba(255, 255, 255, 0.1);
    border: 1px solid white;
    color: white;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    width: fit-content;
    transition: background 0.2s;
  }

  button:hover {
    background: rgba(255, 255, 255, 0.2);
  }

  .bids {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-top: 10px;
    padding-top: 10px;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
  }

  ul {
    list-style-type: disc;
    padding-left: 20px;
    margin: 0;
  }

  li {
    margin-bottom: 5px;
  }

  input {
    width: 100%;
    padding: 10px;
    box-sizing: border-box;
    background: transparent;
    border: none;
    border-bottom: 2px solid white;
    color: white;
    font-family: system-ui, sans-serif;
    outline: none;
  }

  input::placeholder {
    color: rgba(255, 255, 255, 0.5);
  }
</style>
