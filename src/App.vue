<template>
  <div
    id="app"
    @keydown.backspace="erase()"
    @keydown="onKeydown"
  >
    <section class="container max-w-md py-16 mx-auto">
      <h1 class="text-center text-2xl capitalize mb-10">Calculator App</h1>
      <div class="w-full">
        <result :total="currentCount || '0'"></result>
        <div class="flex">
          <div class="w-3/4">
            <div class="flex">
              <div class="w-1/3">
                <button
                  class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
                  @click="clear()"
                >C</button>
              </div>
              <div class="w-1/3">
                <button
                  class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
                  @click="erase()"
                >
                  <svg
                    width="18"
                    height="24"
                    aria-hidden="true"
                    focusable="false"
                    data-prefix="fas"
                    data-icon="arrow-left"
                    class="w-full text-center"
                    role="img"
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 448 512"
                  >
                    <path
                      fill="currentColor"
                      d="M257.5 445.1l-22.2 22.2c-9.4 9.4-24.6 9.4-33.9 0L7 273c-9.4-9.4-9.4-24.6 0-33.9L201.4 44.7c9.4-9.4 24.6-9.4 33.9 0l22.2 22.2c9.5 9.5 9.3 25-.4 34.3L136.6 216H424c13.3 0 24 10.7 24 24v32c0 13.3-10.7 24-24 24H136.6l120.5 114.8c9.8 9.3 10 24.8.4 34.3z"
                    />
                  </svg>
                </button>
              </div>
              <div class="w-1/3">
                <button
                  class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
                >%</button>
              </div>
            </div>

            <div class="flex">
              <div class="w-1/3">
                <button
                  class="text-center w-full py-3 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
                  :class="[currentCount.charAt(currentCount.length-1) == '7' ? 'bg-gray-600' : 'bg-gray-700']"
                  @click="append(7)"
                >7</button>
              </div>
              <div class="w-1/3">
                <button
                  class="text-center w-full py-3 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
                  :class="[currentCount.charAt(currentCount.length-1) == '8' ? 'bg-gray-600' : 'bg-gray-700']"
                  @click="append(8)"
                >8</button>
              </div>
              <div class="w-1/3">
                <button
                  class="text-center w-full py-3 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
                  :class="[currentCount.charAt(currentCount.length-1) == '9' ? 'bg-gray-600' : 'bg-gray-700']"
                  @click="append(9)"
                >9</button>
              </div>
            </div>

            <div class="flex">
              <div class="w-1/3">
                <button
                  class="text-center w-full py-3 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
                  :class="[currentCount.charAt(currentCount.length-1) == '4' ? 'bg-gray-600' : 'bg-gray-700']"
                  @click="append(4)"
                >4</button>
              </div>
              <div class="w-1/3">
                <button
                  class="text-center w-full py-3 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
                  :class="[currentCount.charAt(currentCount.length-1) == '5' ? 'bg-gray-600' : 'bg-gray-700']"
                  @click="append(5)"
                >5</button>
              </div>
              <div class="w-1/3">
                <button
                  class="text-center w-full py-3 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
                  :class="[currentCount.charAt(currentCount.length-1) == '6' ? 'bg-gray-600' : 'bg-gray-700']"
                  @click="append(6)"
                >6</button>
              </div>
            </div>

            <div class="flex">
              <div class="w-1/3">
                <button
                  class="text-center w-full py-3 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
                  :class="[currentCount.charAt(currentCount.length-1) == '1' ? 'bg-gray-600' : 'bg-gray-700']"
                  @click="append(1)"
                >1</button>
              </div>
              <div class="w-1/3">
                <button
                  class="text-center w-full py-3 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
                  :class="[currentCount.charAt(currentCount.length-1) == '2' ? 'bg-gray-600' : 'bg-gray-700']"
                  @click="append(2)"
                >2</button>
              </div>
              <div class="w-1/3">
                <button
                  class="text-center w-full py-3 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
                  @click="append(3)"
                  :class="[currentCount.charAt(currentCount.length-1) == '3' ? 'bg-gray-600' : 'bg-gray-700']"
                >3</button>
              </div>
            </div>
            <div class="flex">
              <div class="w-2/3">
                <button
                  class="text-center w-full py-3 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
                  @click="append(0)"
                  :class="[currentCount.charAt(currentCount.length-1) == '0' ? 'bg-gray-600' : 'bg-gray-700']"
                >0</button>
              </div>
              <div class="w-1/3">
                <button
                  @click="append('.')"
                  class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
                >.</button>
              </div>
            </div>
          </div>

          <div class="w-1/4 flex flex-col bg-orange-500">
            <div class>
              <button
                class="text-center w-full text-white py-3 border-b border-black focus:outline-none focus:bg-orange-400"
                :class="[ sign == '/' ? 'bg-orange-400' : 'bg-orange-500' ]"
                @click="divide"
              >
                <svg
                  width="24"
                  height="24"
                  aria-hidden="true"
                  focusable="false"
                  data-prefix="fas"
                  data-icon="divide"
                  class="w-full mx-auto"
                  role="img"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 448 512"
                >
                  <path
                    fill="currentColor"
                    d="M224 352c-35.35 0-64 28.65-64 64s28.65 64 64 64 64-28.65 64-64-28.65-64-64-64zm0-192c35.35 0 64-28.65 64-64s-28.65-64-64-64-64 28.65-64 64 28.65 64 64 64zm192 48H32c-17.67 0-32 14.33-32 32v32c0 17.67 14.33 32 32 32h384c17.67 0 32-14.33 32-32v-32c0-17.67-14.33-32-32-32z"
                  />
                </svg>
              </button>
            </div>
            <div class>
              <button
                class="text-center w-full text-white py-3 border-b border-black focus:outline-none focus:bg-orange-400"
                :class="[ sign == '*' ? 'bg-orange-400' : 'bg-orange-500' ]"
                @click="times"
              >
                <svg
                  height="24"
                  width="24"
                  aria-hidden="true"
                  focusable="false"
                  data-prefix="fas"
                  data-icon="times"
                  class="w-full mx-auto"
                  role="img"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 352 512"
                >
                  <path
                    fill="currentColor"
                    d="M242.72 256l100.07-100.07c12.28-12.28 12.28-32.19 0-44.48l-22.24-22.24c-12.28-12.28-32.19-12.28-44.48 0L176 189.28 75.93 89.21c-12.28-12.28-32.19-12.28-44.48 0L9.21 111.45c-12.28 12.28-12.28 32.19 0 44.48L109.28 256 9.21 356.07c-12.28 12.28-12.28 32.19 0 44.48l22.24 22.24c12.28 12.28 32.2 12.28 44.48 0L176 322.72l100.07 100.07c12.28 12.28 32.2 12.28 44.48 0l22.24-22.24c12.28-12.28 12.28-32.19 0-44.48L242.72 256z"
                  />
                </svg>
              </button>
            </div>
            <div class>
              <button
                class="text-center w-full text-white py-3 border-b border-black focus:outline-none focus:bg-orange-400"
                :class="[ sign == '-' ? 'bg-orange-400' : 'bg-orange-500' ]"
                @click="minus"
              >
                <svg
                  width="24"
                  height="24"
                  aria-hidden="true"
                  focusable="false"
                  data-prefix="fas"
                  data-icon="minus"
                  class="w-full mx-auto"
                  role="img"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 448 512"
                >
                  <path
                    fill="currentColor"
                    d="M416 208H32c-17.67 0-32 14.33-32 32v32c0 17.67 14.33 32 32 32h384c17.67 0 32-14.33 32-32v-32c0-17.67-14.33-32-32-32z"
                  />
                </svg>
              </button>
            </div>
            <div class>
              <button
                class="text-center w-full text-white py-3 border-b border-black focus:outline-none focus:bg-orange-400"
                :class="[ sign == '+' ? 'bg-orange-400' : 'bg-orange-500' ]"
                @click="add"
              >
                <svg
                  height="24"
                  width="24"
                  aria-hidden="true"
                  focusable="false"
                  data-prefix="fas"
                  data-icon="plus"
                  class="w-full mx-auto"
                  role="img"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 448 512"
                >
                  <path
                    fill="currentColor"
                    d="M416 208H272V64c0-17.67-14.33-32-32-32h-32c-17.67 0-32 14.33-32 32v144H32c-17.67 0-32 14.33-32 32v32c0 17.67 14.33 32 32 32h144v144c0 17.67 14.33 32 32 32h32c17.67 0 32-14.33 32-32V304h144c17.67 0 32-14.33 32-32v-32c0-17.67-14.33-32-32-32z"
                  />
                </svg>
              </button>
            </div>
            <div class>
              <button
                class="w-full text-center text-white py-3 border-b border-black focus:outline-none focus:bg-orange-400"
                :class="[ sign == '=' ? 'bg-orange-400' : 'bg-orange-500' ]"
                @click="equal"
              >
                <svg
                  height="24"
                  width="24"
                  aria-hidden="true"
                  focusable="false"
                  data-prefix="fas"
                  data-icon="equals"
                  class="w-full mx-auto"
                  role="img"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 448 512"
                >
                  <path
                    fill="currentColor"
                    d="M416 304H32c-17.67 0-32 14.33-32 32v32c0 17.67 14.33 32 32 32h384c17.67 0 32-14.33 32-32v-32c0-17.67-14.33-32-32-32zm0-192H32c-17.67 0-32 14.33-32 32v32c0 17.67 14.33 32 32 32h384c17.67 0 32-14.33 32-32v-32c0-17.67-14.33-32-32-32z"
                  />
                </svg>
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import result from "./components/Result.vue";

export default {
  components: {
    result
  },
  data() {
    return {
      currentCount: "",
      previous: null,
      sign: null,
      operator: null,
      operatorClicked: false,
      color: null
    };
  },
  methods: {
    clear() {
      this.currentCount = "";
    },
    erase() {
      this.currentCount = this.currentCount.slice(0, -1);
    },
    append(number) {
      if (this.operatorClicked) {
        this.currentCount = "";
        this.operatorClicked = false;
      }

      this.currentCount += number;
    },
    setPrevious() {
      this.previous = "";
      this.previous = this.currentCount;
      this.operatorClicked = true;
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.sign = "/";
      this.setPrevious();
    },
    add() {
      this.operator = (a, b) => a + b;
      this.sign = "+";
      this.setPrevious();
    },
    times() {
      this.operator = (a, b) => a * b;
      this.sign = "*";
      this.setPrevious();
    },
    minus() {
      this.operator = (a, b) => a - b;
      this.sign = "-";
      this.setPrevious();
    },
    equal() {
      this.currentCount = `${this.operator(
        parseFloat(this.previous),
        parseFloat(this.currentCount)
      )}`;
      this.previous = null;
      this.sign = "=";
    },

    onKeydown(evt) {
      const numbersPattern = /[0-9]/;
      const symbolsPattern = /[+*-/=]/;

      if(numbersPattern.test(evt.key)) {
        this.append(evt.key);
      } 
      // If operators has been pressed do a calculation
      else if(symbolsPattern.test(evt.key)) {
        const operatorsAlias = {
          '-' : 'minus',
          '+' : 'add',
          '*' : 'times',
          '/' : 'divide',
          '=' : 'equal',
        }

        this[operatorsAlias[evt.key]]();
      }
    }
  }
};
</script>

<style>
@tailwind base;
@tailwind components;
@tailwind utilities;
.active {
  color: darkorange;
}
</style>