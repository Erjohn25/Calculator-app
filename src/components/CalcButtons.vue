<template>
  <div class="flex">
    <div class="w-3/4">
      <div class="flex">
        <div class="w-1/3">
          <button
            class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
          >C</button>
        </div>
        <div class="w-1/3">
          <button
            class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
          >IDK</button>
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
            class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
            @click="addition(7)"
          >7</button>
        </div>
        <div class="w-1/3">
          <button
            class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
            @click="count += 8"
          >8</button>
        </div>
        <div class="w-1/3">
          <button
            class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
            @click="count += 9"
          >9</button>
        </div>
      </div>

      <div class="flex">
        <div class="w-1/3">
          <button
            class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
          >4</button>
        </div>
        <div class="w-1/3">
          <button
            class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
          >5</button>
        </div>
        <div class="w-1/3">
          <button
            class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
          >6</button>
        </div>
      </div>

      <div class="flex">
        <div class="w-1/3">
          <button
            class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
          >1</button>
        </div>
        <div class="w-1/3">
          <button
            class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
          >2</button>
        </div>
        <div class="w-1/3">
          <button
            class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
          >3</button>
        </div>
      </div>
      <div class="flex">
        <div class="w-2/3">
          <button
            class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
          >0</button>
        </div>
        <div class="w-1/3">
          <button
            class="text-center w-full py-3 bg-gray-700 border-r border-b border-black text-white focus:outline-none focus:bg-gray-600"
          >.</button>
        </div>
      </div>
    </div>
    <div class="w-1/4 flex flex-col bg-orange-500">
      <div class>
        <button
          class="text-center w-full text-white py-3 border-b border-black focus:outline-none focus:bg-orange-400"
        >/</button>
      </div>
      <div class>
        <button
          class="text-center w-full text-white py-3 border-b border-black focus:outline-none focus:bg-orange-400"
        >X</button>
      </div>
      <div class>
        <button
          class="text-center w-full text-white py-3 border-b border-black focus:outline-none focus:bg-orange-400"
        >-</button>
      </div>
      <div class>
        <button
          class="text-center w-full text-white py-3 border-b border-black focus:outline-none focus:bg-orange-400"
        >+</button>
      </div>
      <div class>
        <button
          class="w-full text-center text-white py-3 border-b border-black focus:outline-none focus:bg-orange-400"
          @click="addition"
        >=</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    
}
</script>