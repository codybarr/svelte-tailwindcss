<script>
  import { onMount } from 'svelte'
  import Tailwind from './Tailwind.svelte'

  let time = new Date()

  // these automatically update when `time`
  // changes, because of the `$:` prefix
  $: hours = time.getHours()
  $: minutes = time.getMinutes()
  $: seconds = time.getSeconds()

  onMount(() => {
    const interval = setInterval(() => {
      time = new Date()
    }, 1000)

    return () => {
      clearInterval(interval)
    }
  })
</script>

<div class="flex align-center justify-center">
  <div class="shadow-lg bg-gray-800 text-white p-5 mt-5">
    <p>{time}</p>
  </div>
</div>

<style>
</style>
