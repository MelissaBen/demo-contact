<template>
  <Layout>
    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <g-image alt="Example image" src="~/favicon.png" width="135" />

    <h1>Hello, world!</h1>

    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur excepturi labore tempore expedita, et iste tenetur suscipit explicabo! Dolores, aperiam non officia eos quod asperiores</p>

    <p class="home-links">
      <a href="https://gridsome.org/docs/" target="_blank" rel="noopener">Gridsome Docs</a>
      <a href="https://github.com/gridsome/gridsome" target="_blank" rel="noopener">GitHub</a>
    </p>

    <form name="contact" method="POST" data-netlify="true">
      <p>
        <label>
          Your Name:
          <input type="text" name="name" />
        </label>
      </p>
      <p>
        <label>
          Your Email:
          <input type="email" name="email" />
        </label>
      </p>

      <p>
        <label>
          Message:
          <textarea name="message"></textarea>
        </label>
      </p>
      <p>
        <button type="submit">Send</button>
      </p>
    </form>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: "Hello, world!"
  },
  name: "QAForm",
  methods: {
    updatePanelist(ev) {
      this.currentPanelist = ev.target.value;
    }
  },
  data() {
    return {
      panelists: ["Evan You", "Chris Fritz"],
      currentPanelist: "Evan You"
    };
  }
};
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
