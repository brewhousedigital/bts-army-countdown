<script>
  import Member from "$lib/components/Member.svelte";

  const timeline = [
    {name: "Jin", start: "12/13/2022", end: "6/13/2024", color: "#e498d7", icon: "icon-jin"},
    {name: "Hobi", start: "04/18/2023", end: "10/18/2024", color: "#61c97f", icon: "icon-hobi"},
    {name: "Yoongi", start: "09/22/2023", end: "06/21/2025", color: "#b8eed4", icon: "icon-yoongi"},
    {name: "Namjoon", start: "", end: "", color: "#ac6fcd", icon: "icon-namjoon"},
    {name: "Jimin", start: "", end: "", color: "#5ad7fa", icon: "icon-jimin"},
    {name: "Taehyung", start: "", end: "", color: "#f4a945", icon: "icon-taehyung"},
    {name: "Jungkook", start: "", end: "", color: "#c74641", icon: "icon-jungkook"},
  ]
</script>

<svelte:head>
  <title>BTS Returns! Tracker</title>
  <meta name="description" content="Keep track of each member of BTS and how long their deployment will be!">

  <meta property="og:url" content="https://bts-countdown.netlify.app/">
  <meta property="og:type" content="website">
  <meta property="og:title" content="BTS Returns! Tracker">
  <meta property="og:description" content="Keep track of each member of BTS and how long their deployment will be!">
  <meta property="og:image" content="https://bts-countdown.netlify.app/opengraph.png">

  <meta name="twitter:card" content="summary_large_image">
  <meta property="twitter:domain" content="bts-countdown.netlify.app">
  <meta property="twitter:url" content="https://bts-countdown.netlify.app/">
  <meta name="twitter:title" content="BTS Returns! Tracker">
  <meta name="twitter:description" content="Keep track of each member of BTS and how long their deployment will be!">
  <meta name="twitter:image" content="https://bts-countdown.netlify.app/opengraph.png">
</svelte:head>


<div class="container">
  <h1>Patiently Waiting</h1>

  <div class="chart">
    {#each timeline as time}
      <Member name={time.name} start={time.start} end={time.end} color={time.color} icon={time.icon} />
    {/each}
  </div>

  <p style="text-align: center;">🏴‍☠️ Made for the Arrchive 🏴‍☠️</p>
</div>


<style>
  .container {
    max-width: 600px;
    margin: 0 auto;
    padding: 0 20px;
    overflow: hidden;
  }

  .chart {
    margin-bottom: 100px;
  }
</style>
