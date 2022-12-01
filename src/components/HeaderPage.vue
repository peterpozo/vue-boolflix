<template>
  <header>
    <nav>
      <a href="#!"><img class="logo" src="../components/img/logo.png" /></a>
    </nav>
    <section class="jumbotron">
      <div class="background">
        <img src="../components/img/jumbo.jpeg" />
        <div class="gradient"></div>
      </div>
      <div class="content">
        <div>
          <h1>Unlimited films, TV programmes and more.</h1>
          <h2>Watch anywhere. Cancel at any time.</h2>
          <h3>
            Ready to watch? Enter your email to create or restart your
            membership.
          </h3>
          <form @submit.prevent="$emit('queryChange', queryString)">
            <div>
              <input
                id="query"
                name="query"
                type="text"
                placeholder="What are you looking for? "
                v-model="queryString"
              />
            </div>
            <div>
              <button>Search</button>
            </div>
          </form>
        </div>
      </div>
    </section>
  </header>
</template>

<script>
export default {
  name: "HeaderPage",
  data() {
    return {
      queryString: "",
    };
  },
};
</script>

<style lang="scss" scoped>
nav {
  display: grid;
  grid-template-columns: max-content 1fr;
  padding: 26px 20px;
  position: absolute;
  width: 100%;
  z-index: 5;
}
@media screen and (min-width: 550px) {
  nav {
    padding: 26px 56px;
  }
}

nav .logo {
  height: 27px;
}
@media screen and (min-width: 550px) {
  nav .logo {
    height: 37px;
  }
}
.jumbotron {
  position: relative;
}
.jumbotron .gradient {
  background-image: linear-gradient(
    to top,
    rgba(0, 0, 0, 0.8) 0,
    rgba(0, 0, 0, 0) 60%,
    rgba(0, 0, 0, 0.8) 100%
  );
  position: absolute;
  inset: 0;
}
.jumbotron .background {
  position: absolute;
  z-index: 1;
  inset: 0;
}
.jumbotron .background img {
  height: 100%;
  width: 100%;
  opacity: 0.6;
  object-fit: cover;
}

.jumbotron .content {
  padding: 95px 20px;
  max-width: 655px;
  margin: 0 auto;
  display: grid;
  align-items: center;
  text-align: center;
  position: relative;
  z-index: 3;
}
@media screen and (min-width: 550px) {
  .jumbotron .content {
    padding-top: 235px;
    padding-bottom: 185px;
  }
}

.jumbotron h1 {
  font-size: 1.75rem;
  font-weight: bold;
}
.jumbotron h2 {
  font-size: 1.125rem;
  margin-top: 13px;
  margin-bottom: 29px;
}
.jumbotron h3 {
  font-size: 1.125rem;
}
@media screen and (min-width: 550px) {
  .jumbotron h1 {
    font-size: 3.125rem;
    font-weight: bold;
  }
  .jumbotron h2 {
    font-size: 1.625rem;
    margin-top: 13px;
    margin-bottom: 29px;
  }
  .jumbotron h3 {
    font-size: 1.2rem;
  }
}

.jumbotron form {
  position: relative;
  display: grid;
  grid-template-columns: 1fr;
  margin: 20px 20px 0;
  row-gap: 15px;
}
@media screen and (min-width: 550px) {
  .jumbotron form {
    display: grid;
    grid-template-columns: 1fr max-content;
  }
}

.jumbotron input {
  padding: 15px 10px;
  font-size: 1.2rem;
  width: 100%;
}
.jumbotron input:focus {
  padding-top: 19px;
  padding-bottom: 11px;
}

.jumbotron button {
  font-size: 1rem;
  padding: 10px 16px;
  background-color: #e50914;
  border-radius: 2px;
  color: #fff;
  border: 0;
}
@media screen and (min-width: 550px) {
  .jumbotron button {
    font-size: 1.625rem;
    padding: 13px 26px;
    border-radius: 0;
  }
}
</style>
