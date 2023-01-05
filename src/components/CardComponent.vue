<template>
  <div class="card">
    <div class="container">
      <div class="header">
        <div class="avatar">
          <img :src="imageSrc()" :alt="graduate.name" />
        </div>
        <div class="graduate">
          <div class="name fw-semi-bold text-opacity-50">
            {{ graduate.name }}
          </div>
          <div class="verified text-opacity-50">
            {{ graduate.verified ? "Verified Graduate" : "Unverified Graduate" }}
          </div>
        </div>
      </div>
      <div class="body text-opacity-70">
        <div class="overview">
          {{ graduate.overview }}
        </div>
        <div class="content">
          {{ graduate.content }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardComponent",
  props: {
    graduate: Object,
  },
  methods: {
    imageSrc: function () {
      return new URL(`../assets/images/image-${this.graduate.avatar}.jpg`, import.meta.url).href;
    },
  },
};
</script>

<style lang="scss" scoped>
.card {
  padding: 2em;
  border-radius: 1em;
  box-shadow: 1px 1px 5pc 5px var(--clr-neutral-400);

  &.quotation {
    background-image: url("@/assets/images/bg-pattern-quotation.svg");
    background-repeat: no-repeat;
    background-position: top 2% right 10%;
  }

  .container {
    display: flex;
    flex-direction: column;

    .header {
      display: flex;
      align-items: center;
      margin-bottom: 0.5em;

      .avatar {
        margin-right: 2em;

        img {
          width: 4em;
          border-radius: 100%;
        }
      }

      .graduate {
        .name {
          font-size: 1.25em;
        }
      }
    }

    .body {
      .overview {
        font-size: 2em;
        line-height: 1.25em;
      }
      .content {
        margin-top: 1em;
        font-size: 1.25em;

        &::before,
        &::after {
          content: '"';
        }
      }
    }
  }
}
</style>
