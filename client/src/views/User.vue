<script>
export default {
  data() {
    return {
      disabled: 0,
      name: "tes",
      username: "tes1",
      email: "tes@eci.co.id",
      password: "tes123",
    };
  },
  methods: {
    tesTriger(e) {
      this.disabled == 0 ? (this.disabled += 1) : (this.disabled -= 1);
    },
    submitEdit() {
      this.disabled -= 1;
    },
  },
};
</script>

<template>
  <div class="container px-6 h-full">
    <div class="grid h-48 mt-10">
      <div class="flex justify-center">
        <span id="iconUser"><i class="fa-regular fa-user"></i></span>
      </div>
      <div>
        <form @submit.prevent="submitEdit">
          <div>
            <input
              type="text"
              placeholder="Name"
              class="input input-bordered w-full max-w-xs"
              :disabled="disabled == 0"
              v-model="name"
            />
          </div>
          <div class="mt-2">
            <input
              type="text"
              placeholder="Username"
              class="input input-bordered w-full max-w-xs"
              :disabled="disabled == 0"
              v-model="username"
            />
          </div>
          <div class="mt-2">
            <input
              type="text"
              placeholder="Email"
              class="input input-bordered w-full max-w-xs"
              :disabled="disabled == 0"
              v-model="email"
            />
          </div>
          <div class="mt-2">
            <input
              type="password"
              placeholder="Password"
              class="input input-bordered w-full max-w-xs"
              :disabled="disabled == 0"
              v-model="password"
            />
          </div>
          <div class="flex ml-20">
            <button
              @click.prevent="tesTriger"
              type="submit"
              class="btn mt-2 mr-10"
              id="editButton"
            >
              {{ disabled == 0 ? "EDIT" : "CANCEL" }}
            </button>
            <button type="submit" class="btn mt-2" id="submitButton">
              Submit
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
#iconUser {
  font-size: 10em;
  color: #000000;
  margin-left: 10px;
}
</style>
