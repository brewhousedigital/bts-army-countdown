<script>
  import Member from "$lib/components/Member.svelte";

  const timeline = [
    {name: "Jin", start: "12/13/2022", end: "6/13/2024", color: "#e498d7", icon: "icon-jin"},
    {name: "Hobi", start: "04/18/2023", end: "10/18/2024", color: "#61c97f", icon: "icon-hobi"},
    {name: "Namjoon", start: "", end: "", color: "#ac6fcd", icon: "icon-namjoon"},
    {name: "Yoongi", start: "", end: "", color: "#b8eed4", icon: "icon-yoongi"},
    {name: "Jimin", start: "", end: "", color: "#5ad7fa", icon: "icon-jimin"},
    {name: "Taehyung", start: "", end: "", color: "#f4a945", icon: "icon-taehyung"},
    {name: "Jungkook", start: "", end: "", color: "#c74641", icon: "icon-jungkook"},
  ]
</script>


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
