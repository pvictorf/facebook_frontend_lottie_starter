<template>
  <div class="post-card">
    <div class="post-card-top">
      <div class="profile-avatar">
        <img src="@/assets/img/profile-pic.jpg" alt="" />

        <div>
          <p>Stephanny Motta</p>
          <span>18:37</span>
        </div>
      </div>

      <div>
        <p class="post-text">
          Lorem, ipsum dolor sit amet consectetur adipisicing elit. Laborum non
          labore sit nesciunt fuga fugit ut, voluptas iusto.
        </p>
      </div>
    </div>

    <div class="card-middle">
      <img src="@/assets/img/post1.png" alt="" />
    </div>

    <div class="reactions-counter">
      <div class="counter-box">
        <img src="@/assets/img/like-icon.svg" alt="" />
        <span>13</span>
      </div>

      <div class="counter-box">
        <img src="@/assets/img/heart-icon.svg" alt="" />
        <span>08</span>
      </div>
    </div>

    <PostReactions />
    
    <div class="post-comments" :class="{ 'open-comments': openedComments }">
      <div class="comment-form">
        <form>
          <img src="@/assets/img/profile-pic.jpg" alt="" />
          <ExpandableTextarea
            v-model="text"
            placeholder="Escreva seu comentário"
          />
        </form>
      </div>

      <div class="comments">
        <div class="comment">
          <img src="@/assets/img/profile-pic.jpg" alt="" />
          <div class="comment-content">
            <span>Deborah Gomes</span>
            <p>
              Lorem ipsum dolor sit, amet consectetur adipisicing elit. Non
              culpa temporibus unde doloremque eos dolore.
            </p>
          </div>
        </div>

        <div class="comment">
          <img src="@/assets/img/profile-pic.jpg" alt="" />
          <div class="comment-content">
            <span>Deborah Gomes</span>
            <p>
              Lorem ipsum dolor sit, amet consectetur adipisicing elit. Non
              culpa temporibus unde doloremque eos dolore.
            </p>
          </div>
        </div>
      </div>

      <div class="commments-actions">
        <button>Mostrar mais</button>
        <button @click="openedComments = !openedComments">
          Ocultar comentários
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data(): any {
    return {
      openedComments: false,
      text: '',
    }
  },
})
</script>

<style lang="scss" scoped>
.post-card {
  background: color(dark, shade1);
  border-radius: 1.25rem;
  box-shadow: 1px 3.2px 8.7px 0.3px rgba(1, 1, 1, 0.19);
  padding-bottom: 1.563rem;
  .post-card-top {
    padding: 1.2rem;
    display: grid;
    grid-gap: 1rem;
    .profile-avatar {
      display: grid;
      grid-template-columns: repeat(2, auto);
      grid-gap: 1.2rem;
      justify-content: start;
      align-items: center;

      > div {
        display: grid;
        grid-gap: 0.33rem;
        p {
          color: color(white);
          font-weight: bold;
        }
        span {
          color: color(gray, shade1);
          font-size: 0.875rem;
        }
      }
      img {
        width: 3.5rem;
        border-radius: 2.438rem;
      }
    }
    .post-text {
      color: color(white);
    }
  }
  .card-middle {
    img {
      width: 100%;
    }
  }
  .reactions-counter {
    display: grid;
    grid-auto-flow: column;
    grid-gap: 1.1rem;
    justify-content: start;
    padding-left: 1.7rem;
    position: relative;
    top: -21px;
    .counter-box {
      position: relative;
      color: #98a9bc;
      display: grid;
      align-items: center;
      justify-items: center;
      grid-gap: 0.6rem;
      img {
        width: 1.875rem;
      }
    }
  }
  
  .post-comments {
    padding: 1.2rem;
    padding-bottom: 0;
    display: grid;
    grid-gap: 1.4rem;
    height: 0;
    opacity: 0;
    transition: all 300ms ease;
    overflow: hidden;
    .comment-form {
      form {
        display: grid;
        grid-template-columns: auto 1fr;
        grid-gap: 1rem;
        img {
          width: 2.688rem;
          border-radius: 50%;
        }
        .grow-wrap {
          background: #112331;
          padding: 0.888rem 1.375rem;
          border-radius: 2rem;
        }
      }
    }
    .comments {
      display: grid;
      grid-gap: 0.7rem;
      .comment {
        display: grid;
        grid-template-columns: auto 1fr;
        align-items: center;
        grid-gap: 1rem;
        .comment-content {
          display: grid;
          grid-gap: 0.5rem;
          justify-content: start;
          border-radius: 1.25rem;
          padding: 0.888rem 1.375rem;
          background: color(dark, shade2);
          color: color(white);
          span {
            font-size: 0.875rem;
            font-weight: bold;
          }
        }
        img {
          width: 2.688rem;
          border-radius: 50%;
        }
      }
    }
    .commments-actions {
      display: grid;
      grid-auto-flow: column;
      justify-content: space-between;
      button {
        outline: none;
        background: none;
        color: color(gray, shade1);
        cursor: pointer;
      }
    }
  }
  .open-comments {
    height: auto;
    opacity: 1;
  }
}
</style>
