<template>
  <div class="mycard">
    <div class="rank"><lang-flag :iso="language" /></div>
    <div class="front">
      <img class="thumbnail" :src="imgUrl" :alt="title" />
      <h3 class="name">{{ title }}</h3>
      <div class="info">
        <p class="year">{{ date }}</p>
        <div class="stars">
          <font-awesome-icon
            v-for="star in score.score"
            :key="star"
            icon="fa-solid fa-star"
            :style="{ color: 'yellow' }"
          />
          <font-awesome-icon
            v-for="star in score.maxScore - score.score"
            :key="star"
            icon="fa-regular fa-star"
            :style="{ color: 'yellow' }"
          />
        </div>
      </div>
    </div>
    <div class="back">
      <div class="cards-info">
        <p class="game-stat">{{ date }}<span>Release Date</span></p>
      </div>
      <button class="mybtn">See more</button>
      <div class="stars">
        <font-awesome-icon
          v-for="item in score.score"
          :key="item"
          icon="fa-solid fa-star"
          :style="{ color: 'yellow' }"
        />
        <font-awesome-icon
          v-for="item in score.maxScore - score.score"
          :key="item"
          icon="fa-regular fa-star"
          :style="{ color: 'yellow' }"
        />
      </div>
    </div>

    <div class="background"></div>
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";
export default {
  name: "PageCard",
  components: {
    LangFlag,
  },
  props: {
    title: String,
    originalTitle: String,
    language: String,
    score: Object,
    imgUrl: String,
    date: String,
  },
};
</script>

<style lang="scss" scoped>
h1,
h2,
h3,
p {
  margin: 0;
}
img {
  max-width: 100%;
}
.mybtn {
  cursor: pointer;
  border: 0;
  background: gray;
  border-radius: 100vw;
  padding: 0.5em 1.5em;
}
.mycard {
  position: relative;
  width: 12.5em;
  cursor: pointer;
}
.stars {
  display: flex;
  text-align: center;

  img {
    width: 2em;
    height: 2em;
    background: red;
  }
}
.rank {
  position: absolute;
  top: 0;
  right: 1em;
  z-index: 1000;
  font-weight: bold;
  background: rgba(0, 0, 0, 0.65);
  padding: 0.5em 0.5em 0.75em;
  clip-path: polygon(100% 0%, 100% 100%, 50% 85%, 0% 100%, 0 0);
  transition: transform 250ms ease-in-out;
}
.front {
  transition: 250ms;
  .thumbnail {
    border-radius: 0.5em;
  }
  .name {
    margin: 0.75em 0;
  }
  .info {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .stars img {
    border: 1px solid blue;
  }
}
.back {
  opacity: 0;
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1em;

  .cards-info {
    columns: 2;
    column-rule: 1px solid rgba(255, 255, 255, 0.25);
  }

  .game-stat {
    font-size: 1.125rem;
    text-align: center;

    span {
      font-size: 0.85rem;
      display: block;
    }
  }
}

.background {
  background: #234;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: -1;
  transform: scale(0.2, 0.9);
  opacity: 0;
  border-radius: 0.5em;
}

.mycard:hover {
  .rank {
    transform: translate(-13%, -53%);
  }
  .front {
    transform: translateY(-30%) scale(0.8);

    .name {
      animation: cardName 250ms forwards;
    }

    .info {
      opacity: 0;
    }
  }
  .back {
    opacity: 1;
  }
  .background {
    transition: transform 200ms cubic-bezier(0.21, 1, 0.81, 1),
      opacity 100ms linear;
    opacity: 1;
    transform: scale(0.9, 1.1);
  }
}

@keyframes cardName {
  0% {
    text-align: left;
    opacity: 1;
  }

  20% {
    text-align: left;
    opacity: 0;
  }

  50% {
    text-align: center;
    opacity: 0;
    transform: scale(1.2);
  }

  100% {
    text-align: center;
    opacity: 1;
    transform: scale(1.2);
  }
}
</style>
