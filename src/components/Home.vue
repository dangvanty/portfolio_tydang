<template>
  <div
    :class="{ 'bg-white': !nightMode, 'bg-dark': nightMode }"
    class="pt-5 p-st"
  >
    <div
      class="container"
      data-aos="fade"
      data-aos-once="true"
      data-aos-duration="1000"
    >
      <div class="row align-items-center">
        <div class="col-xl-6 col-bg-6 col-md-6 col-sm-12 pt-5">
          <span
            class="home-title"
            :class="{ pgray: !nightMode, 'text-light': nightMode }"
          >
            {{
              this.langVN
                ? "Xin chào, dưới đây là portfolio của tôi!"
                : "Welcome to my portfolio!"
            }}
          </span>
          <div>
            <p
              class="home-description"
              v-html="this.langVN ? description.vi : description.en"
            ></p>
          </div>
          <div class="text-center pb-4">
            <button
              class="btn btn-outline-secondary mx-2"
              @click="open('linkedin')"
              v-tooltip.bottom="'LinkedIn'"
            >
              <i class="fab fa-linkedin"></i>
            </button>
            <button
              class="btn btn-outline-secondary mx-2"
              @click="open('github')"
              v-tooltip.bottom="'GitHub'"
            >
              <i class="fab fa-github"></i>
            </button>
            <button
              class="btn btn-outline-secondary mx-2"
              v-tooltip.bottom="'dangvantydh@gmail.com'"
              @click.prevent
            >
              <i class="fab fa-google"></i>
            </button>
            <button
              class="btn btn-outline-secondary mx-2"
              @click="open('resume')"
              v-tooltip.bottom="'Resume'"
            >
              <i class="fa fa-file"></i>
            </button>
          </div>
        </div>
        <div class="col-xl-6 col-bg-6 col-md-6 col-sm-12 text-center img-box">
          <img :src="picture" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import info from "../../info";

export default {
  name: "Home",
  components: {},
  props: {
    nightMode: {
      type: Boolean,
    },
    langVN: {
      type: Boolean,
    },
  },
  data() {
    return {
      picture: info.flat_picture,
      description: info.description,
      name: info.name,
      linkedin: info.links.linkedin,
      github: info.links.github,
      google: info.links.google,
      resume: info.links.resume,
    };
  },
  methods: {
    open(link) {
      switch (link) {
        case "linkedin":
          window.open(this.linkedin, "_blank");
          break;
        case "github":
          window.open(this.github, "_blank");
          break;
        case "google":
          window.open(this.google, "_blank");
          break;
        case "resume":
          window.open(this.langVN ? this.resume.vi : this.resume.en, "_blank");
          break;
      }
    },
  },
};
</script>

<style scoped>
.home-title {
  font-size: 32px;
  font-weight: 500;
}

.img-box {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  padding: 20px;
}

.img-box img {
  max-width: 100%; /* Ảnh luôn nằm gọn trong div */
  height: auto; /* Giữ tỷ lệ ảnh */
  border-radius: 20px;
  object-fit: contain;
}
@media (min-width: 768px) and (max-width: 1024px) {
  .home-description {
    font-size: 14px; /* Giảm cỡ chữ */
  }
}
@media (max-width: 768px) {
  .img-box img {
    max-width: 300px;
    height: auto;
    margin-top: 20px;
  }
}

@media (max-width: 480px) {
  .img-box img {
    max-width: 200px;
    height: auto;
    border-radius: 50%;
  }
}

.fa {
  font-size: 15px;
}

.btn {
  border-color: #759cc9;
  color: #759cc9;
}

.btn:hover {
  background-color: #759cc9;
  border-color: #759cc9;
  color: white;
}

.btn:focus {
  background-color: #759cc9;
  border-color: #759cc9;
  color: white;
}

.btn:focus {
  outline: none !important;
}

p {
  text-align: justify;
  font-weight: 400;
}

/* LEAVES */
</style>
