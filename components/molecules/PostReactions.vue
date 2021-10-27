<template>
    <section class="post-reactions">
      <div class="post-actions">
        <div class="btn-reactions">
          <ul class="reactions">
            <li class="reaction-like">
                <LottieAnimation animation="emojis-like" />
            </li>
            <li class="reaction-heart">
                <LottieAnimation animation="emojis-love" />
            </li>
            <li class="reaction-laugh">
                <LottieAnimation animation="emojis-wow" />
            </li>
            <li class="reaction-sad">
              <LottieAnimation animation="emojis-sad" />
            </li>
            <li class="reaction-angry">
                <LottieAnimation animation="emojis-angry-face" />
            </li>
          </ul>

            <img src="@/assets/img/thumb-icon.svg" alt="" />
            <span>Reagir</span>
        </div>

        <div @click="openedComments = !openedComments" class="btn-open-comments">
            <img src="@/assets/img/comment-icon.svg" alt="" />
            <span>Comentar</span>
        </div>
      </div>
    </section>
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
.post-actions {
    display: grid;
    grid-auto-flow: column;
    grid-template-columns: repeat(2, 1fr);
    border-top: 1px solid #23354b;
    border-bottom: 1px solid #23354b;
    > div {
      cursor: pointer;
      display: grid;
      grid-auto-flow: column;
      align-items: center;
      grid-gap: 0.6rem;
      color: #f4f6f8;
      font-weight: bold;
      justify-content: center;
      padding: 1rem 0;
    }
    .btn-reactions {
      position: relative;

      .reaction-anim {
        background: transparent;
      }

      .reactions {
        visibility: hidden;
        opacity: 0;
        width: auto;
        position: absolute;
        display: grid;
        grid-auto-flow: column;
        grid-gap: 0.6rem;
        top: -3.813rem;
        left: 8px;
        background: #1f354d;
        padding: 0.3rem 0.4rem;
        border-radius: 3.438rem;
        box-shadow: 1px -6px 8px rgba(0, 0, 0, 0.25);
        transition: all 300ms ease;
        @include screen('medium', 'small') {
          top: -3.188rem;
        }

        li {
          display: grid;
          align-items: center;
          position: relative;
          transform: scale(0.2);
          opacity: 0;
          transition: all 300ms;
          .lottie-animation {
            width: 51px;
            transition: all 300ms ease;
            @include screen('medium', 'small') {
              width: 2.5rem;
            }
            &:hover {
              transform: scale(1.35);
            }
          }
        }
      }
      &:hover .reactions {
        visibility: visible;
        opacity: 1;
        li {
          transform: scale(1);
          opacity: 1;
        }

        .reaction-heart {
          transition-delay: 0.06s;
        }

        .reaction-laugh {
          transition-delay: 0.09s;
        }

        .reaction-sad {
          transition-delay: 0.12s;
        }

        .reaction-angry {
          transition-delay: 0.15s;
        }
      }
    }
}
</style>