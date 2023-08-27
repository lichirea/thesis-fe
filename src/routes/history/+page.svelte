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
    // await fetch(`http://localhost:3000/history`)
    //   .then(r => r.json())
    //   .then(data => {
    //     console.log(data);
    //     checks = data.Items;
    //   });
    checks = [
      {
  "time": 1693145873709,
  content: {
    "title": "Harvard University",
    "sites": [
      "https://www.harvard.edu",
      "https://hds.harvard.edu"
    ],
    "allitemcount": 855,
    "totalelements": 2575,
    "categories": {
      "error": {
        "description": "Errors",
        "count": 8,
        "items": {
          "label_missing": {
            "id": "label_missing",
            "description": "Missing form label",
            "count": 1
          },
          "button_empty": {
            "id": "button_empty",
            "description": "Empty button",
            "count": 4
          },
          "alt_link_missing": {
            "id": "alt_link_missing",
            "description": "Linked image missing alternative text",
            "count": 3
          }
        }
      },
      "contrast": {
        "description": "Contrast Errors",
        "count": 1,
        "items": {
          "contrast": {
            "id": "contrast",
            "description": "Very low contrast",
            "count": 1
          }
        }
      },
      "alert": {
        "description": "Alerts",
        "count": 43,
        "items": {
          "heading_possible": {
            "id": "heading_possible",
            "description": "Possible heading",
            "count": 13
          },
          "link_redundant": {
            "id": "link_redundant",
            "description": "Redundant link",
            "count": 6
          },
          "noscript": {
            "id": "noscript",
            "description": "Noscript element",
            "count": 2
          },
          "text_small": {
            "id": "text_small",
            "description": "Very small text",
            "count": 9
          },
          "table_layout": {
            "id": "table_layout",
            "description": "Layout table",
            "count": 3
          },
          "html5_video_audio": {
            "id": "html5_video_audio",
            "description": "HTML5 video or audio",
            "count": 7
          },
          "alt_duplicate": {
            "id": "alt_duplicate",
            "description": "A nearby image has the same alternative text",
            "count": 1
          },
          "tabindex": {
            "id": "tabindex",
            "description": "Tabindex",
            "count": 1
          },
          "title_redundant": {
            "id": "title_redundant",
            "description": "Redundant title text",
            "count": 1
          }
        }
      },
      "feature": {
        "description": "Features",
        "count": 79,
        "items": {
          "alt": {
            "id": "alt",
            "description": "Alternative text",
            "count": 28
          },
          "alt_link": {
            "id": "alt_link",
            "description": "Linked image with alternative text",
            "count": 9
          },
          "figure": {
            "id": "figure",
            "description": "Figure",
            "count": 34
          },
          "label": {
            "id": "label",
            "description": "Form label",
            "count": 1
          },
          "link_skip": {
            "id": "link_skip",
            "description": "Skip link",
            "count": 2
          },
          "link_skip_target": {
            "id": "link_skip_target",
            "description": "Skip link target",
            "count": 2
          },
          "lang": {
            "id": "lang",
            "description": "Language",
            "count": 2
          },
          "alt_null": {
            "id": "alt_null",
            "description": "Null or empty alternative text",
            "count": 1
          }
        }
      },
      "structure": {
        "description": "Structural Elements",
        "count": 122,
        "items": {
          "h1": {
            "id": "h1",
            "description": "Heading level 1",
            "count": 5
          },
          "h2": {
            "id": "h2",
            "description": "Heading level 2",
            "count": 27
          },
          "h3": {
            "id": "h3",
            "description": "Heading level 3",
            "count": 22
          },
          "ol": {
            "id": "ol",
            "description": "Ordered list",
            "count": 25
          },
          "ul": {
            "id": "ul",
            "description": "Unordered list",
            "count": 19
          },
          "iframe": {
            "id": "iframe",
            "description": "Inline frame",
            "count": 3
          },
          "header": {
            "id": "header",
            "description": "Header",
            "count": 3
          },
          "nav": {
            "id": "nav",
            "description": "Navigation",
            "count": 9
          },
          "search": {
            "id": "search",
            "description": "Search",
            "count": 1
          },
          "main": {
            "id": "main",
            "description": "Main content",
            "count": 2
          },
          "footer": {
            "id": "footer",
            "description": "Footer",
            "count": 2
          },
          "region": {
            "id": "region",
            "description": "Generic region",
            "count": 4
          }
        }
      },
      "aria": {
        "description": "ARIA",
        "count": 602,
        "items": {
          "aria": {
            "id": "aria",
            "description": "ARIA",
            "count": 144
          },
          "aria_label": {
            "id": "aria_label",
            "description": "ARIA label",
            "count": 188
          },
          "aria_describedby": {
            "id": "aria_describedby",
            "description": "ARIA description",
            "count": 12
          },
          "aria_tabindex": {
            "id": "aria_tabindex",
            "description": "ARIA tabindex",
            "count": 62
          },
          "aria_live_region": {
            "id": "aria_live_region",
            "description": "ARIA alert or live region",
            "count": 1
          },
          "aria_button": {
            "id": "aria_button",
            "description": "ARIA button",
            "count": 6
          },
          "aria_hidden": {
            "id": "aria_hidden",
            "description": "ARIA hidden",
            "count": 149
          },
          "aria_expanded": {
            "id": "aria_expanded",
            "description": "ARIA expanded",
            "count": 40
          }
        }
      }
    }
  }
},
{
  "time": 1693146147893,
  content: {
    "title": "Google",
    "sites": [
      "https://www.google.com",
      "https://www.google.com/search/howsearchworks/?fg=1"
    ],
    "allitemcount": 172,
    "totalelements": 657,
    "categories": {
      "error": {
        "description": "Errors",
        "count": 1,
        "items": {
          "label_missing": {
            "id": "label_missing",
            "description": "Missing form label",
            "count": 1
          }
        }
      },
      "contrast": {
        "description": "Contrast Errors",
        "count": 7,
        "items": {
          "contrast": {
            "id": "contrast",
            "description": "Very low contrast",
            "count": 7
          }
        }
      },
      "alert": {
        "description": "Alerts",
        "count": 18,
        "items": {
          "label_title": {
            "id": "label_title",
            "description": "Unlabeled form control with title",
            "count": 1
          },
          "heading_missing": {
            "id": "heading_missing",
            "description": "No heading structure",
            "count": 2
          },
          "region_missing": {
            "id": "region_missing",
            "description": "No page regions",
            "count": 1
          },
          "select_missing_label": {
            "id": "select_missing_label",
            "description": "Select missing label",
            "count": 1
          },
          "link_redundant": {
            "id": "link_redundant",
            "description": "Redundant link",
            "count": 4
          },
          "noscript": {
            "id": "noscript",
            "description": "Noscript element",
            "count": 1
          },
          "javascript_jumpmenu": {
            "id": "javascript_jumpmenu",
            "description": "JavaScript jump menu",
            "count": 1
          },
          "html5_video_audio": {
            "id": "html5_video_audio",
            "description": "HTML5 video or audio",
            "count": 6
          },
          "youtube_video": {
            "id": "youtube_video",
            "description": "YouTube video",
            "count": 1
          }
        }
      },
      "feature": {
        "description": "Features",
        "count": 17,
        "items": {
          "alt": {
            "id": "alt",
            "description": "Alternative text",
            "count": 3
          },
          "alt_null": {
            "id": "alt_null",
            "description": "Null or empty alternative text",
            "count": 5
          },
          "lang": {
            "id": "lang",
            "description": "Language",
            "count": 2
          },
          "alt_link": {
            "id": "alt_link",
            "description": "Linked image with alternative text",
            "count": 7
          }
        }
      },
      "structure": {
        "description": "Structural Elements",
        "count": 12,
        "items": {
          "ul": {
            "id": "ul",
            "description": "Unordered list",
            "count": 4
          },
          "iframe": {
            "id": "iframe",
            "description": "Inline frame",
            "count": 2
          },
          "search": {
            "id": "search",
            "description": "Search",
            "count": 1
          },
          "header": {
            "id": "header",
            "description": "Header",
            "count": 1
          },
          "nav": {
            "id": "nav",
            "description": "Navigation",
            "count": 3
          },
          "footer": {
            "id": "footer",
            "description": "Footer",
            "count": 1
          }
        }
      },
      "aria": {
        "description": "ARIA",
        "count": 117,
        "items": {
          "aria": {
            "id": "aria",
            "description": "ARIA",
            "count": 53
          },
          "aria_label": {
            "id": "aria_label",
            "description": "ARIA label",
            "count": 23
          },
          "aria_tabindex": {
            "id": "aria_tabindex",
            "description": "ARIA tabindex",
            "count": 19
          },
          "aria_menu": {
            "id": "aria_menu",
            "description": "ARIA menu",
            "count": 1
          },
          "aria_button": {
            "id": "aria_button",
            "description": "ARIA button",
            "count": 13
          },
          "aria_hidden": {
            "id": "aria_hidden",
            "description": "ARIA hidden",
            "count": 2
          },
          "aria_expanded": {
            "id": "aria_expanded",
            "description": "ARIA expanded",
            "count": 3
          },
          "aria_haspopup": {
            "id": "aria_haspopup",
            "description": "ARIA popup",
            "count": 3
          }
        }
      }
    }
  }
}
    ]
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

  /* width */
  ::-webkit-scrollbar {
    width: 10px;
  }

  /* Track */
  ::-webkit-scrollbar-track {
    background: #f1f1f1;
  }

  /* Handle */
  ::-webkit-scrollbar-thumb {
    background: #888;
  }

  /* Handle on hover */
  ::-webkit-scrollbar-thumb:hover {
    background: #555;
  }
</style>