<script>
  import Member from "$lib/components/Member.svelte";

  const timeline = [
    {name: "Jin", start: "12/13/2022", end: "6/13/2024", color: ""},
    {name: "Hobi", start: "04/17/2023", end: "10/17/2024", color: ""},
    {name: "Namjoon", start: "", end: "", color: ""},
    {name: "Yoongi", start: "", end: "", color: ""},
    {name: "Jimin", start: "", end: "", color: ""},
    {name: "Taehyung", start: "", end: "", color: ""},
    {name: "Jungkook", start: "", end: "", color: ""},
  ]
</script>


<div class="container">
  <h1>Patiently Waiting</h1>

  {#each timeline as time}
    <Member name={time.name} start={time.start} end={time.end} />
  {/each}
</div>


<style>
  .container {
    max-width: 600px;
    margin: 0 auto;
  }
</style>
