<template>
  <button class="btn">
    More
    <svg width="40" height="40" xmlns="http://www.w3.org/2000/svg">
      <g fill="none" fill-rule="evenodd">
        <circle fill="#303030" cx="20" cy="20" r="20"/>
        <path stroke="#FFF" stroke-width="2" d="M14 23l6-6 6 6"/>
      </g>
    </svg>
  </button>
</template>

<script>
export default {
  name: 'Button'
}
</script>

<style lang="scss" scoped>
  .btn {
    color: $darkGray;
    background: $white;
    width: 9.125rem;
    height: 3.5rem;
    border: none;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 28px;
    cursor: pointer;
    transition: color 300ms ease-in-out;
    font-size: 1rem;
    line-height: 1.75rem;
    letter-spacing: 5px;
    font-weight: 700;
    text-transform: uppercase;
    margin-top: 3.5rem;

    &:hover {
      color: #999;
    }

    &:hover circle {
      fill: #999;
    }

    svg {
      margin-left: 0.5rem;
      transition: all 300ms ease-in-out;
      transform: rotateX(180deg);

      circle {
        transition: fill 300ms ease-in-out;
      }
    }

    @media screen and (min-width: 80rem) {
      margin-top: 0;
      position: absolute;
      bottom: 0;
      right: 0;
    }
  }
</style>