<script lang="ts">
  const books = [
    {
      title: "Bio 101",
      author: "John Doe",
      cover:
        "https://i.pinimg.com/736x/1e/08/a2/1e08a2bd6acf19fd9530717d84a4a86c.jpg",
      summary: "An introduction to biology for beginners.",
    },
    {
      title: "Bio 101",
      author: "John Doe",
      cover:
        "https://i.pinimg.com/736x/1e/08/a2/1e08a2bd6acf19fd9530717d84a4a86c.jpg",
      summary: "An introduction to biology for beginners.",
    },
    {
      title: "Bio 101",
      author: "John Doe",
      cover:
        "https://i.pinimg.com/736x/1e/08/a2/1e08a2bd6acf19fd9530717d84a4a86c.jpg",
      summary: "An introduction to biology for beginners.",
    },
    {
      title: "Bio 101",
      author: "John Doe",
      cover:
        "https://i.pinimg.com/736x/1e/08/a2/1e08a2bd6acf19fd9530717d84a4a86c.jpg",
      summary: "An introduction to biology for beginners.",
    },

    {
      title: "Bio 101",
      author: "John Doe",
      cover:
        "https://i.pinimg.com/736x/1e/08/a2/1e08a2bd6acf19fd9530717d84a4a86c.jpg",
      summary: "An introduction to biology for beginners.",
    },

    {
      title: "Bio 101",
      author: "John Doe",
      cover:
        "https://i.pinimg.com/736x/1e/08/a2/1e08a2bd6acf19fd9530717d84a4a86c.jpg",
      summary: "An introduction to biology for beginners.",
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
    </div>
  {/each}
</div>

<style>
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
