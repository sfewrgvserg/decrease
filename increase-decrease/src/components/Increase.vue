<template>
  <div class="mainContainer">
    <div class="container">
      <h2>The current count is....</h2>
      <h1 :class="Textcolor" ref="countElement">{{ count }}</h1>
      <div class="btn-container">
        <div class="btn">
          <button @click="handleClickIncrease">+</button>
          <button @click="handleClickDecrease">-</button>
        </div>
        <button @click="handleReset" class="btn-reset">Reset Now</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      Textcolor: "zero",
    };
  },
  methods: {
    handleClickIncrease() {
      this.handleColor();
      this.count++;
    },
    handleClickDecrease() {
      this.handleColor();
      this.count--;
    },
    handleColor() {
      const h1 = this.$refs.countElement;
      console.log(h1);
      if (this.count > 0) {
        h1.classList.remove("sub", "zero");
        h1.classList.add("plus");
      } else if (this.count < 0) {
        h1.classList.remove("plus", "zero");
        h1.classList.add("sub");
      } else if (this.count === 0) {
        h1.classList.remove("plus", "sub");
      }
      //   if (this.count > 0) {
      //     this.Textcolor = "plus";
      //   } else if (this.count < 0) {
      //     this.Textcolor = "sub";
      //   } else if (this.count === 0) {
      //     this.Textcolor = "zero";
      //   }
    },
    handleReset() {
      const h1 = this.$refs.countElement;
      h1.classList.remove("plus", "sub");
      h1.classList.add("zero");
      this.count = 0;
    },
  },
};
</script>

<style>
.mainContainer {
  width: 100%;
  height: 100vh;
  background-color: aquamarine;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.container {
  background-color: antiquewhite;
  padding: 5rem;
  border-radius: 15px;
}

.container h2 {
  font-size: xx-large;
  margin: 40px 0;
}
.btn button {
  font-size: xx-large;
  font-weight: bold;
  padding: 2px 50px;
  margin: 45px 15px;
  border: none;
  box-shadow: 5px 1px 5px black;
}
.btn-container {
  display: flex;
  flex-direction: column;
}
.btn-reset {
  width: 10rem;
  padding: 10px 0;
  border: none;
  box-shadow: 7px 3px 15px black;
  margin: auto;
  font-size: medium;
  font-weight: bold;
}

.container button:hover {
  background-color: burlywood;
  box-shadow: 7px 3px 15px black;
  transition: 0.3s ease-in;
}
.container button:active {
  color: white;
  background-color: cyan;
}
.sub {
  color: red;
}
.plus {
  color: green;
}
.zero {
  color: black;
}
</style>
