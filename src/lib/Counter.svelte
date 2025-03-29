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
  count is {count}
  <div>
    <button onclick={decrement}>
      -1
    </button>      
    <button onclick={increment}>
      +1
    </button>
  </div>
</div>
