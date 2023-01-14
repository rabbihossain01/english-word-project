<template>
  <div class="home-page">
    <div class="english-app-table-box">
      <h2>English learning strategies</h2>
      <div class="english-app-box">
        <div class="input-box">
          <label for="englishWord">English Word</label>
          <input
            id="englishWord"
            v-model="englishWord"
            type="text"
            placeholder="Type a word"
          />
        </div>
        <div class="input-box">
          <label for="banglaMeanig">Bangla Meanig</label>
          <input
            id="banglaMeanig"
            v-model="banglaMeaning"
            type="text"
            placeholder="The word meaning"
          />
        </div>
        <div class="input-box">
          <label for="sentence">Sentence</label>
          <input
            id="sentence"
            v-model="sentence"
            type="text"
            placeholder="Make an easy sentence"
          />
        </div>
      </div>
      <button
        v-if="!isEditing"
        class="add-word primary-btn-full-width"
        @click="postItem"
      >
        Add To Word
      </button>
      <button
        v-else
        class="add-word primary-btn-full-width"
        @click="updateBookList"
      >
        Update Book List
      </button>
      <div class="table-section">
        <table>
          <tr>
            <th>English Word</th>
            <th>Bangla Meaning</th>
            <th>Sentence</th>
            <th>Update</th>
            <th>Delete</th>
          </tr>
          <tr v-for="(bookList, id) in booksList" :key="id">
            <td>{{ bookList.englishWord }}</td>
            <td>{{ bookList.banglaMeaning }}</td>
            <td>{{ bookList.sentence }}</td>
            <td class="icon" @click="updateItem(bookList.id, bookList)">
              <svg
                version="1.0"
                xmlns="http://www.w3.org/2000/svg"
                width="20.000000pt"
                height="20.000000pt"
                viewBox="0 0 48.000000 48.000000"
                preserveAspectRatio="xMidYMid meet"
              >
                <g
                  transform="translate(0.000000,48.000000) scale(0.100000,-0.100000)"
                  fill="#000000"
                  stroke="none"
                >
                  <path
                    d="M354 415 c-18 -13 -18 -15 14 -47 32 -32 34 -32 47 -14 16 22 6 49
-24 65 -13 7 -24 6 -37 -4z"
                  />
                  <path
                    d="M182 247 c-106 -106 -122 -127 -122 -155 0 -30 3 -32 33 -32 28 0 48
16 157 125 l124 125 -29 30 c-16 16 -31 30 -35 30 -3 0 -60 -55 -128 -123z
m144 72 c7 -13 -203 -229 -223 -229 -7 0 -13 6 -13 12 0 13 209 228 222 228 4
0 10 -5 14 -11z"
                  />
                </g>
              </svg>
            </td>
            <td class="icon" @click="removeItem(bookList.id)">
              <svg
                data-v-009b3438=""
                data-v-23a7914a=""
                xmlns="http://www.w3.org/2000/svg"
                version="1.0"
                width="15px"
                height="15px"
                viewBox="0 0 512.000000 512.000000"
                preserveAspectRatio="xMidYMid meet"
              >
                <g
                  data-v-009b3438=""
                  data-v-23a7914a=""
                  transform="translate(0.000000,512.000000) scale(0.100000,-0.100000)"
                  fill="#000000"
                  stroke="none"
                >
                  <path
                    data-v-009b3438=""
                    data-v-23a7914a=""
                    d="M1871 5109 c-128 -25 -257 -125 -311 -241 -37 -79 -50 -146 -50 -259 l0 -89 -389 0 c-222 0 -411 -4 -442 -10 -187 -36 -330 -184 -361 -376 -30 -181 66 -371 231 -458 l69 -36 6 -58 c4 -31 65 -763 136 -1627 72 -863 134 -1587 139 -1608 36 -155 177 -295 335 -332 91 -22 2561 -22 2652 0 158 37 299 177 335 332 5 21 67 745 139 1608 71 864 132 1596 136 1627 l6 58 69 36 c165 87 261 277 231 458 -31 192 -174 340 -361 376 -31 6 -220 10 -442 10 l-389 0 0 89 c0 48 -5 112 -10 142 -34 180 -179 325 -359 359 -66 12 -1306 12 -1370 -1z m1359 -309 c60 -31 80 -78 80 -190 l0 -90 -750 0 -750 0 0 90 c0 110 20 159 78 189 36 19 60 20 670 21 615 0 634 -1 672 -20z m1200 -600 c45 -23 80 -80 80 -130 0 -50 -35 -107 -80 -130 -39 -20 -55 -20 -1870 -20 -1815 0 -1831 0 -1870 20 -45 23 -80 80 -80 130 0 48 35 107 78 129 36 20 65 20 1870 21 1818 0 1833 0 1872 -20z m-236 -622 c-2 -24 -63 -747 -134 -1606 -140 -1694 -129 -1598 -193 -1646 l-28 -21 -1279 0 -1279 0 -28 21 c-64 48 -53 -48 -193 1646 -71 859 -132 1582 -134 1606 l-6 42 1640 0 1640 0 -6 -42z"
                  ></path>
                  <path
                    data-v-009b3438=""
                    data-v-23a7914a=""
                    d="M1587 3299 c-25 -13 -45 -34 -58 -62 l-21 -43 76 -1234 c85 -1381 76 -1299 155 -1340 51 -25 91 -25 142 0 27 14 46 34 60 63 l21 43 -76 1234 c-85 1381 -76 1299 -155 1340 -50 25 -95 25 -144 -1z"
                  ></path>
                  <path
                    data-v-009b3438=""
                    data-v-23a7914a=""
                    d="M2488 3299 c-23 -12 -46 -35 -58 -59 -20 -39 -20 -57 -20 -1280 0 -1224 0 -1241 20 -1280 23 -45 80 -80 130 -80 50 0 107 35 130 80 20 39 20 56 20 1280 0 1224 0 1241 -20 1280 -37 73 -127 99 -202 59z"
                  ></path>
                  <path
                    data-v-009b3438=""
                    data-v-23a7914a=""
                    d="M3387 3299 c-77 -41 -68 37 -153 -1339 l-76 -1234 21 -43 c14 -29 33 -49 60 -63 51 -25 91 -25 142 0 79 41 70 -41 155 1340 l76 1234 -21 43 c-37 75 -127 103 -204 62z"
                  ></path>
                </g>
              </svg>
            </td>
          </tr>
        </table>
      </div>
      <vue-confirm-dialog />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      englishWord: '',
      banglaMeaning: '',
      sentence: '',
      selectIndex: null,
      booksList: [],
      isEditing: false,
    }
  },

  mounted() {
    this.fetchTodoListData()
  },
  methods: {
    async fetchTodoListData() {
      const { data } = await this.$axios.get('http://localhost:3001/books/all')
      this.booksList = data.books
    },
    async postItem() {
      try {
        const { data } = await this.$axios.post('http://localhost:3001/book', {
          englishWord: this.englishWord,
          banglaMeaning: this.banglaMeaning,
          sentence: this.sentence,
        })

        this.booksList.push({
          englishWord: this.englishWord,
          banglaMeaning: this.banglaMeaning,
          sentence: this.sentence,
        })
        this.englishWord = ''
        this.banglaMeaning = ''
        this.sentence = ''
        console.log(data)
      } catch (error) {
        console.log(error)
      }
    },

    updateBookList() {
      try {
        this.$confirm({
          title: 'Confirm',
          message: 'Are you sure you want to update this item?',
          button: {
            no: 'Cancel',
            yes: 'Yes',
          },
          callback: async (confirm) => {
            if (confirm) {
              await this.$axios.put(
                `http://localhost:3001/book/${this.selectIndex}`,
                {
                  englishWord: this.englishWord,
                  banglaMeaning: this.banglaMeaning,
                  sentence: this.sentence,
                }
              )
              this.fetchTodoListData()
              this.englishWord = ''
              this.banglaMeaning = ''
              this.sentence = ''
            }
          },
        })
      } catch (error) {
        console.log(error)
      } finally {
        this.isEditing = false
      }
    },

    updateItem(id, bookList) {
      this.englishWord = bookList.englishWord
      this.banglaMeaning = bookList.banglaMeaning
      this.sentence = bookList.sentence
      this.selectIndex = id
      this.isEditing = true
    },

    removeItem(id) {
      try {
        this.$confirm({
          title: 'Confirm',
          message: 'Are you sure you want to delete item?',
          button: {
            no: 'Cancel',
            yes: 'Yes',
          },
          callback: async (confirm) => {
            if (confirm) {
              await this.$axios.delete(`http://localhost:3001/book/${id}`)
              const item = this.booksList.filter((el) => el.id !== id)
              this.booksList = item
            }
          },
        })
      } catch (error) {
        console.log(error)
      }
    },
  },
}
</script>

<style lang="scss" scoped>
@import '~/styles/style.scss';
.home-page {
  padding-top: 2rem;
  background: #f1f1f9;
  max-width: 1200px;
  width: 90%;
  min-height: calc(100vh - 4rem);
  .english-app-table-box {
    padding: 2rem;
    h2 {
      color: $color-secondary;
      font-size: 2rem;
      text-transform: capitalize;
      margin-bottom: 2rem;
    }
    .english-app-box {
      .input-box {
        padding: 0.7rem 0;
      }
    }

    .add-word {
      margin-top: 1.5rem;
    }
    .table-section {
      margin-top: 3rem;
      table {
        font-family: arial, sans-serif;
        border-collapse: collapse;
        width: 100%;
      }
      .icon {
        padding-left: 2rem;
        cursor: pointer;
      }

      td,
      th {
        border: 1px solid rgba(0, 75, 99, 1);
        text-align: left;
        padding: 8px;
      }

      tr:nth-child(even) {
        background-color: rgb(200, 241, 255);
      }
    }
  }
}
</style>
