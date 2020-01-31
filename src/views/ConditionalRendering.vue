<template>
  <div>
    <h1 class="text-xl font-bold">Conditional Rendering</h1>
    <div class="flex px-4 pt-4">
      <div class="w-1/2 border-2">
        <h2 class="text-lg font-semibold text-red-300">v-if</h2>
        <h3 v-if="awesome">Vue is awesome!</h3>
        <h3 v-else>Oh no 😢</h3>
      </div>
      <div class="w-1/2 border-2">
        <h2 class="text-lg font-semibold text-red-300">
          Conditional Groups with v-if on template
        </h2>
        <!-- template will not render -->
        <template v-if="ok">
          <h1>Title</h1>
          <p>Paragraph 1</p>
          <p>Paragraph 2</p>
        </template>
      </div>
    </div>
    <div class="flex px-4">
      <div class="w-1/2 border-2">
        <h2 class="text-lg font-semibold text-red-300">v-else</h2>
        <div v-if="Math.random() > 0.5">
          Now you see me
        </div>
        <div v-else>
          Now you don't
        </div>
      </div>
      <div class="w-1/2 border-2">
        <h2 class="text-lg font-semibold text-red-300">v-else-if</h2>
        <div v-if="type === 'A'">A</div>
        <div v-else-if="type === 'B'">B</div>
        <div v-else-if="type === 'C'">C</div>
        <div v-else>Not A/B/C</div>
      </div>
    </div>
    <div class="flex px-4">
      <div class="w-1/2 border-2">
        <h2 class="text-lg font-semibold text-red-300">
          Controlling Reusable Elements with key
        </h2>
        <div class="py-2">
          <h4>Example with no key</h4>
          <template v-if="loginType === 'username'">
            <label>Username: </label>
            <input placeholder="Enter your username" />
          </template>
          <template v-else>
            <label>Email: </label>
            <input placeholder="Enter your email address" />
          </template>
          <p>
            witching the loginType in the code above will not erase what the
            user has already entered. Since both templates use the same
            elements, the input is not replaced - just its placeholder
          </p>
        </div>
        <div class="py-2">
          <h4>Example with key</h4>
          <template v-if="loginType === 'username'">
            <label>Username: </label>
            <input placeholder="Enter your username" key="username-input" />
          </template>
          <template v-else>
            <label>Email: </label>
            <input placeholder="Enter your email address" key="email-input" />
          </template>
          <p>
            This isn’t always desirable though, so Vue offers a way for you to
            say, “These two elements are completely separate - don’t re-use
            them.” Add a key attribute with unique values:
          </p>
        </div>
        <button
          class="bg-blue-300 p-1 rounded-lg hover:bg-blue-500"
          @click="toggleLoginType"
        >
          Toggle login type
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ConditionalRendering",
  data() {
    return {
      awesome: true,
      ok: true,
      type: "B",
      loginType: "username"
    };
  },
  methods: {
    toggleLoginType() {
      console.log("y");
      if (this.loginType === "username") {
        this.loginType = "email";
      } else {
        this.loginType = "username";
      }
    }
  }
};
</script>

<style lang="scss" scoped></style>
