<template>
  <div class="gallery">
    <div v-if="selectedCat" class="img-container img-container__lg">
      <img :src="selectedCat.url" />
    </div>
    <div class="grid-container">
      <div v-for="cat in cats" :key="cat.id" class="img-container">
        <button class="img-container__del-btn" @click="removeCat(cat)">
          <i class="fa-solid fa-x"></i>
        </button>
        <img :src="cat.url" @click="selectedCat = cat" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "meow-gallery",
  props: ["width", "height"],
  data() {
    return {
      cats: [],
      selectedCat: null,
    };
  },
  computed: {
    numCats() {
      return this.width * this.height;
    },
  },
  mounted() {
    fetch(`https://api.thecatapi.com/v1/images/search?limit=${this.numCats}`)
      .then((res) => res.json())
      .then((cats) => {
        console.log(cats);
        this.cats = cats;
      });
  },
  methods: {
    removeCat(cat) {
      if (this.selectedCat.id === cat.id) {
        this.selectedCat = null;
      }

      this.cats = this.cats.filter((c) => c.id !== cat.id);
    },
  },
};
</script>

<style lang="scss" scoped>
.gallery {
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 100%;
  width: 100%;
}

.grid-container {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-gap: 0.5rem;
}

.img-container {
  background-color: grey;
  border-radius: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0.5rem;
  max-width: 200px;
  max-height: 200px;
  min-width: 200px;
  overflow: hidden;
  opacity: 60%;
  transition: opacity 0.2s ease-in-out;
  box-shadow: 4px 4px 8px rgba(0, 0, 0, 0.2);
  position: relative;

  &:hover {
    opacity: 100%;

    .img-container__del-btn {
      opacity: 0.8;
    }
  }

  &__lg {
    max-width: fit-content;
    max-height: 500px;
    width: 100%;
    height: unset;
    opacity: 100%;

    img {
      min-width: 100%;
      min-height: 100%;
      object-fit: cover;
    }
  }

  &__del-btn {
    position: absolute;
    top: 1rem;
    right: 1rem;
    width: 2rem;
    height: 2rem;
    background-color: #ccc;
    border-radius: 50%;
    border: none;
    cursor: pointer;
    transition: background-color 0.2s ease-in-out;
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
  }

  img {
    min-width: 250px;
    min-height: 250px;
    object-fit: cover;
  }
}
</style>
