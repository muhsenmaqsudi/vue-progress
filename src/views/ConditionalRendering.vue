<template>
  <div class="p-8">
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
        <div class="pb-2">
          <button
            class="bg-blue-300 p-1 rounded-lg hover:bg-blue-500"
            @click="toggleLoginType"
          >
            Toggle login type
          </button>
        </div>
      </div>
      <div class="w-1/2 border-2">
        <h2 class="text-lg font-semibold text-red-300">v-show</h2>
        <h1 v-show="ok">Hello!</h1>
        <p>
          The difference is that an element with v-show will always be rendered
          and remain in the DOM; v-show only toggles the display CSS property of
          the element.
        </p>
        <p>
          Note that v-show doesn’t support the template element, nor does it
          work with v-else.
        </p>
      </div>
    </div>
    <div class="flex px-4">
      <div class="w-2/2 border-2">
        <h2 class="text-lg font-semibold text-red-300">v-if vs v-show</h2>
        <ul>
          <li>
            v-if is “real” conditional rendering because it ensures that event
            listeners and child components inside the conditional block are
            properly destroyed and re-created during toggles.
          </li>
          <li>
            v-if is also lazy: if the condition is false on initial render, it
            will not do anything - the conditional block won’t be rendered until
            the condition becomes true for the first time.
          </li>
          <li>
            In comparison, v-show is much simpler - the element is always
            rendered regardless of initial condition, with CSS-based toggling.
          </li>
          <li>
            Generally speaking, v-if has higher toggle costs while v-show has
            higher initial render costs. So prefer v-show if you need to toggle
            something very often, and prefer v-if if the condition is unlikely
            to change at runtime.
          </li>
        </ul>
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
