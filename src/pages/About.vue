<template>
  <div class="container mt-100 mt-60">
    <div class="row align-items-center">
      <div class="col-lg-5 col-md-6 mt-4 mt-sm-0 pt-2 pt-sm-0 order-2 order-md-1">
        <div class="card shadow rounded border-0">
          <div class="card-body py-5">
            <h4 class="card-title">Get In Touch !</h4>
            <h1>ok</h1>
            <div class="custom-form mt-4">
              <div id="message"></div>
              <form
                name="contact"
                method="post"
                id="contact-form"
                action="/success/"
                v-on:submit.prevent="handleSubmit"
                data-netlify="true"
                data-netlify-honeypot="bot-field"
              >
                <input type="hidden" name="form-name" value="contact" />
                <div class="row">
                  <div class="col-md-6">
                    <div class="form-group position-relative">
                      <label>
                        Nom
                        <span class="text-danger">*</span>
                      </label>
                      <i data-feather="user" class="fea icon-sm icons"></i>
                      <input
                        v-model="formData.name"
                        name="name"
                        id="name"
                        type="text"
                        class="form-control pl-5"
                        placeholder="Nom :"
                      />
                    </div>
                  </div>
                  <!--end col-->
                  <div class="col-md-6">
                    <div class="form-group position-relative">
                      <label>
                        Email
                        <span class="text-danger">*</span>
                      </label>
                      <i data-feather="mail" class="fea icon-sm icons"></i>
                      <input
                        v-model="formData.email"
                        name="email"
                        id="email"
                        type="email"
                        class="form-control pl-5"
                        placeholder="Email :"
                      />
                    </div>
                  </div>
                  <!--end col-->
                  <div class="col-md-12">
                    <div class="form-group position-relative">
                      <label>Message</label>
                      <i data-feather="message-circle" class="fea icon-sm icons"></i>
                      <textarea
                        name="message"
                        id="comments"
                        rows="4"
                        class="form-control pl-5"
                        placeholder="Votre message:"
                        v-model="formData.message"
                      ></textarea>
                    </div>
                  </div>
                </div>
                <!--end row-->

                <!--button submit -->
                <div class="row">
                  <div class="col-sm-12 text-center">
                    <button
                      @click="showDismissibleAlert=true"
                      class="submitBnt btn btn-primary btn-block"
                    >Envoyer</button>
                    <div id="simple-msg"></div>
                  </div>
                  <!--end col-->
                </div>
                <!--end row-->
              </form>
              <!--end form-->
            </div>
            <!--end custom-form-->
          </div>
        </div>
      </div>
      <!--end col-->

      <div class="col-lg-7 col-md-6 order-1 order-md-2">
        <div class="card border-0">
          <div class="card-body p-0"></div>
        </div>
      </div>
      <!--end col-->
    </div>
    <!--end row-->
  </div>
  <!--end container-->
</template>
<script>
export default {
  metaInfo: {
    title: "ContactForm"
  },
  data() {
    return {
      formData: {},
      dismissSecs: 10,
      dismissCountDown: 0,
      showDismissibleAlert: false
    };
  },
  methods: {
    countDownChanged(dismissCountDown) {
      this.dismissCountDown = dismissCountDown;
    },
    showAlert() {
      this.dismissCountDown = this.dismissSecs;
    },

    encode(data) {
      return Object.keys(data)
        .map(
          key => encodeURIComponent(key) + "=" + encodeURIComponent(data[key])
        )
        .join("&");
    },
    handleSubmit(e) {
      fetch("/", {
        method: "POST",
        headers: { "Content-Type": "application/x-www-form-urlencoded" },
        body: this.encode({
          "form-name": e.target.getAttribute("name"),
          ...this.formData
        })
      })
        .then(() => {
          showDismissibleAlert = true;
          // this.notifiy('Votre message est envoyé')
          this.$router.push("/");
        })
        .catch(error => alert(error));
    }
  }
};
</script>
