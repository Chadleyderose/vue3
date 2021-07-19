  <template>
  <h1> Books </h1>
      <table>
        <tr>
          <th>ID</th>
          <th>Title</th>
          <th>Author</th>
          <th>Genre</th>
          <th>Release Date</th>
        </tr>
      <tablebody>
        <tr v-for="book in books" :key="books.id">
          <td>
            {{books.id}}
            <button id="button2" @click="deleteBook(book)">Delete</button>
            </td>
          <td>{{book.Title}}</td>
          <td>{{book.Author}}</td>
          <td>{{book.Genre}}</td>
          <td>{{book.ReleaseDate}}</td>
        </tr> 
      </tbody>
    </table>
</template>

<script>
export default {
  name: "Add",
    data() {
        return{
            books: []
        }
    },
    mounted() {
      fetch('')
        .then(res => res.json())
        .then(data => this.books = data)
        .catch(error => console.log(error.message))
    },
    methods: {
    deleteBook(book) {
      this.books = this.books.filter((item) => {
        return book !== item
      })
    }
    }
}
</script>

<style>
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
th, td {
  padding: 15px;
}
table {
  width: 50%;
  margin-left: 25%;
}
tr:hover {
  background-color:#f5f5f5
}
#button2 {
  padding: 5px;
  background: rgb(162, 255, 162);
  text-align: center;
  cursor: pointer;
  margin: 10px;
}
</style