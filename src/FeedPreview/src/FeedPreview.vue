<template>
  <div class="feed-preview">
    <div v-if="response" class="feed-response">
      <input v-model="searchQuery" placeholder="search" type="text" class="search-query" />
      <ul>
        <li v-for="(item, index) in resultQuery" v-bind:key="index" :class="listItemClass(index)">
          <h1>{{ item.title[0] }}</h1>
          <a v-bind:href="item.link[0]" target="_blank">(Full article link)</a>
          <div v-html="item.description[0]" class="item-description"></div>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    url: String
  },
  data() {
    return {
      response: null,
      searchQuery: null
    };
  },
  created() {
    const xml2js = require("xml2js");
    fetch(`https://cors-anywhere.herokuapp.com/${this.url}`)
      .then(resp => {
        if (!resp.ok) {
          alert("Błąd połączenia - spróbuj ponownie");
        }
        return resp.text();
      })
      .then(resp => xml2js.parseStringPromise(resp))
      .then(resp => (this.response = resp.rss.channel[0].item));
  },
  computed: {
    resultQuery() {
      if (this.searchQuery) {
        return this.response.filter(item => {
          return this.searchQuery
            .toLowerCase()
            .split(" ")
            .every(e => item.title[0].toLowerCase().includes(e));
        });
      } else {
        return this.response;
      }
    }
  },
  methods: {
    listItemClass(index) {
      return index % 2 === 0 ? "even-item" : "odd-item";
    }
  }
};
</script>
<style lang="scss">
.feed-preview {
  max-width: 90vw;
  margin: 0 auto;

  ul {
    margin: 2rem 0 2rem 0;
    li {
      padding: 2rem;
      list-style: none;
      border-radius: 10px;
      margin: 1rem 0 1rem 0;
    }
  }
  img {
    width: 100%;
  }

  .feed-response {
    display: flex;
    flex-direction: column;
    align-items: center;

    .search-query {
      padding: 1rem;
      margin-top: 2rem;
      border: 2px solid rgba(0, 0, 0, 0.3);
      border-radius: 10px;
      text-align: center;
      transition: all 200ms ease;
      &:focus {
        border: 2px solid rgb(74, 158, 238);
      }
    }
  }
}

.even-item {
  background-color: rgb(74, 158, 238);
  color: rgb(255, 255, 255);
  a {
    color: rgb(0, 0, 0);
  }
}

.odd-item {
  background-color: rgb(197, 197, 197);
  a {
    color: rgb(0, 111, 214);
  }
}
</style>
