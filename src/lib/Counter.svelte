<script lang="ts">
  let count: number = $state(0)
  const increment = () => {
    count += 1
  }
  const decrement = () => {
    count -= 1;
  }
</script>

<div>
  <p class="uk-paragraph">count is {count}</p>
  <div>
    <button class="uk-btn uk-btn-primary" onclick={decrement}>
      -1
    </button>      
    <button class="uk-btn uk-btn-primary" onclick={increment}>
      +1
    </button>
  </div>
</div>
