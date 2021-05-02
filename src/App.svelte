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

<div class="flex align-center justify-center h-screen">
  <div class="shadow-lg bg-gray-500 text-white p-5">
    <p>{time}</p>
  </div>
</div>

<style>
</style>
