<script>
    import { onMount } from "svelte";
    import List, {
    Item,
    Graphic,
    Meta,
    Text,
    PrimaryText,
    SecondaryText,
  } from '@smui/list';
  import TimestampToDate from "../../shared/components/TimestampToDate.svelte";
  import CheckDetails from "./CheckDetails.svelte";

    let checks;
    let selectionIndex = 0;
    let list;

    onMount(async () => {
    await fetch(`http://localhost:3000/history`)
      .then(r => r.json())
      .then(data => {
        console.log(data);
        checks = data.Items;
      });
    });
</script>

{#if checks}
<div class="list-and-details-container">
  <div class="list-class">
    <List
      class="check-list"
      bind:this={list}
      threeLine
      singleSelection
      selectedIndex={selectionIndex}
    >
      {#each checks as item, i}
        <Item
          on:SMUI:action={() => (selectionIndex = i)}
          selected={selectionIndex === i}
        >
          <Text>
            <PrimaryText>{item.content.title}</PrimaryText>
            <SecondaryText><TimestampToDate timestamp={item.time}></TimestampToDate></SecondaryText>
            <SecondaryText>{item.content.allitemcount} items analyzed</SecondaryText>
          </Text>
        </Item>
      {/each}
    </List>
  </div>
  
  <div class="details-container">
    <CheckDetails check={checks[selectionIndex]}>
    </CheckDetails>
  </div>

</div>

{:else}
  <p class="loading">loading...</p>
{/if}

<style>

  .list-and-details-container {
    display: flex;
  }
  
  .list-class {
    overflow-y: scroll; 
    height: 92vh;
    min-width: 250px;
  }

  .details-container {
    width: 100%;
    height: 100%;
    padding: 0.3rem;
    display: flex;
    gap: 1rem;
    flex-wrap: wrap; 
  }
</style>