<script>
    export let timestamp;
    let date = new Date(timestamp);
  </script>
  
{date.toLocaleString('en-GB')}